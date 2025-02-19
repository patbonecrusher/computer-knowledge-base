---
creation date: 2025-14-02 12:12:12
tags:
  - dev/platform/esp
  - hw/esp32s3
---
---
## R16 and R32 gotchas

The ESP32 S3 R16 and R32 can only do spi at 1.8v.  In other words, only GPIO47 and 48 are 1.8V, the rest is 3.3V. Those two GPIO pins may not be connected to the flash, but they're powered by the same voltage.

---
## strapping pin

**0** Boot Mode (pull-up at boot = boot from flash)  
**3** JTAG (pull-down at boot)  
**45** SPI voltage. (pull-down at boot = 3.3v SPI)  
**46** Debug console print during boot (pull-down at boot = print debug messages)

---
## timers

### high precision timer, useful to read sensor
```cardlink
url: https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/system/esp_timer.html#one-shot-and-periodic-timers
title: "ESP Timer (High Resolution Timer) - ESP32 -  — ESP-IDF Programming Guide v5.4 documentation"
host: docs.espressif.com
```

The ESP Timer feature allows for creating software timers and invoking their callback functions (dispatching callbacks) on timeout. ESP Timer is useful when user software needs to perform delayed or periodic actions, such as delayed device start/stop or periodic sampling of sensor data.

ESP Timer hides the complexity associated with managing multiple timers, dispatching callbacks, accounting for clock frequency changes (if dynamic frequency scaling is enabled), and maintaining correct time after light sleep.

For application scenarios that require better real-time performance (such as generating waveforms) or configurable timer resolution, it is recommended that [GPTimer](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/gptimer.html) be used instead. Also, GPTimer has features not available in ESP Timer, such as event capture.

Finally, FreeRTOS has its own software timers. As explained in [FreeRTOS Timers](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/system/esp_timer.html#freertos-timers), they have much lower resolution compared to ESP Timer, but FreeRTOS timers are portable (non-dependent on ESP-IDF) which might be an advantage in some cases.

### general purpose timer
```cardlink
url: https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/gptimer.html
title: "General Purpose Timer (GPTimer) - ESP32 -  — ESP-IDF Programming Guide v5.4 documentation"
host: docs.espressif.com
```


GPTimer (General Purpose Timer) is the driver of ESP32 Timer Group peripheral. The hardware timer features high resolution and flexible alarm action. A timer alarm occurs when the internal counter of a timer reaches a specific target value. At that moment, a user-registered per-timer callback function is triggered.

General-purpose timers are typically used in the following scenarios:

- To run freely like a clock, providing high-resolution timestamps anytime and anywhere;
    
- To generate periodic alarms that trigger events at regular intervals;
    
- To generate one-shot alarms that respond at a specific target time.

```c
typedef struct {
    uint64_t event_count;
} example_queue_element_t;

static bool example_timer_on_alarm_cb(gptimer_handle_t timer, const gptimer_alarm_event_data_t *edata, void *user_ctx)
{
    BaseType_t high_task_awoken = pdFALSE;
    QueueHandle_t queue = (QueueHandle_t)user_ctx;
    // Retrieve the count value from event data
    example_queue_element_t ele = {.event_count = edata->count_value};
    // Optional: send the event data to other task by OS queue
    // Do not introduce complex logics in callbacks
    // Suggest dealing with event data in the main loop, instead of in this callback
    xQueueSendFromISR(queue, &ele, &high_task_awoken);
    // return whether we need to yield at the end of ISR
    return high_task_awoken == pdTRUE;
}

gptimer_alarm_config_t alarm_config = {
    .reload_count = 0,                  // counter will reload with 0 on alarm event
    .alarm_count = 60 * 1000000,        // period = 1s @resolution 1MHz
    .flags.auto_reload_on_alarm = true, // enable auto-reload
};
ESP_ERROR_CHECK(gptimer_set_alarm_action(gptimer, &alarm_config));

gptimer_event_callbacks_t cbs = {
    .on_alarm = example_timer_on_alarm_cb, // register user callback
};
ESP_ERROR_CHECK(gptimer_register_event_callbacks(gptimer, &cbs, queue));
ESP_ERROR_CHECK(gptimer_enable(gptimer));
ESP_ERROR_CHECK(gptimer_start(gptimer));
```

---

---
## clock tree


```cardlink
url: https://docs.espressif.com/projects/esp-idf/en/stable/esp32s2/api-reference/peripherals/clk_tree.html#_CPPv416soc_module_clk_t
title: "Clock Tree - ESP32-S2 -  — ESP-IDF Programming Guide v5.4 documentation"
host: docs.espressif.com
```



