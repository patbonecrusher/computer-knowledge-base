---
source: https://www.motioncontroltips.com/what-are-pulses-per-revolution-for-encoders
creation date: 2022-10-17 22:41
modification date: Saturday 22nd October 2022 00:06:17
state: complete
tags: engineering, engineering/motor/stepper, engineering/motor/encoders
---

# ppr vs cpr

Message from my script:
---

Pulses per revolution (or PPR) is a parameter associated with encoders. It measures the number of pulses per full revolution or turn of the encoder, with a full revolution being 360 degrees. In essence, it is a measure of an encoder’s resolution.

But what counts as a pulse may have different definitions depending on the manufacturer. For instance, some encoder manufacturers denote a pulse as only the high portion of the square wave pulse an encoder produces. Think of a single cycle of a square wave composed of high (logic “1”) and low (logic “0”) portions of the signal. So the pulse is the high portion and represents one whole cycle of high and low.

[![encoder](https://939506.smushcdn.com/2600047/wp-content/uploads/2018/04/Encoder_Measure_CUI.png?lossy=1&strip=1&webp=1)](https://www.motioncontroltips.com/wp-content/uploads/2018/04/Encoder_Measure_CUI.png)

Complicating things further is that some manufacturers use different terminology that may denote the same or a different definition. For example, one alternative measure is cycles per revolution (CPR). This refers to one complete cycle of high and low and is equivalent to the PPR measure. However, another measure, counts per revolution (CPR), refers to the actual number of states in a quadrature encoder, which for one complete square-wave cycle is 4, and is not equivalent to cycles per revolution nor PPR.

The bottom line is to do one’s due diligence; check to ensure what PPR or CPR refers to in the specifications for an individual encoder.

