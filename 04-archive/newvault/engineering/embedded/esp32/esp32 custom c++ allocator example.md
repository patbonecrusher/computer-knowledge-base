---
creation date: 2025-08-02 12:12:12
tags:
  - dev/snippets
  - dev/platform/esp
---
---
```cardlink
url: https://github.com/openvehicles/Open-Vehicle-Monitoring-System-3
title: "GitHub - openvehicles/Open-Vehicle-Monitoring-System-3: Open Vehicle Monitoring System - Version 3"
description: "Open Vehicle Monitoring System - Version 3. Contribute to openvehicles/Open-Vehicle-Monitoring-System-3 development by creating an account on GitHub."
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://opengraph.githubassets.com/72e70c9ddcf665ecbfc760e7690b01de4b6874f2560c579ca7431dcdc4abe031/openvehicles/Open-Vehicle-Monitoring-System-3
```



```c++
void *ExternalRamMalloc(size_t sz);
void *ExternalRamCalloc(size_t count, size_t size);
void *ExternalRamRealloc(void *ptr, size_t size);

void *InternalRamMalloc(size_t sz);
void *InternalRamCalloc(size_t count, size_t size);
void *InternalRamRealloc(void *ptr, size_t size);

class ExternalRamAllocated
{
  public:
    static void *operator new(std::size_t sz);
    static void *operator new[](std::size_t sz);
    static char *strdup(const char *src);
    static int asprintf(char **strp, const char *fmt, ...) __attribute__((format(printf, 2, 3)));
    static int vasprintf(char **strp, const char *fmt, va_list ap) __attribute__((format(printf, 2, 0)));
};

class InternalRamAllocated
{
  public:
    static void *operator new(std::size_t sz);
    static void *operator new[](std::size_t sz);
    static char *strdup(const char *src);
    static int asprintf(char **strp, const char *fmt, ...) __attribute__((format(printf, 2, 3)));
    static int vasprintf(char **strp, const char *fmt, va_list ap) __attribute__((format(printf, 2, 0)));
};

// C++11 Allocator:
template <class T> struct ExtRamAllocator {
    typedef T value_type;
    ExtRamAllocator() = default;
    template <class U> constexpr ExtRamAllocator(const ExtRamAllocator<U> &) noexcept {}
    T *allocate(std::size_t n)
    {
        auto p = static_cast<T *>(ExternalRamMalloc(n * sizeof(T)));
        return p;
    }
    void deallocate(T *p, std::size_t) noexcept { std::free(p); }
};
template <class T, class U> bool operator==(const ExtRamAllocator<T> &, const ExtRamAllocator<U> &) { return true; }
template <class T, class U> bool operator!=(const ExtRamAllocator<T> &, const ExtRamAllocator<U> &) { return false; }

namespace extram
{
typedef std::basic_string<char, std::char_traits<char>, ExtRamAllocator<char>> string;
typedef std::basic_ostringstream<char, std::char_traits<char>, ExtRamAllocator<char>> ostringstream;
} // namespace extram
```

```c++
void *ExternalRamMalloc(size_t sz)
{
    void *ret = heap_caps_malloc(sz, MALLOC_CAP_SPIRAM);
    if (ret)
        return ret;
    else
        return malloc(sz);
}

void *ExternalRamCalloc(size_t count, size_t size)
{
    void *ret = heap_caps_malloc(count * size, MALLOC_CAP_SPIRAM);
    if (ret) {
        bzero(ret, count * size);
        return ret;
    } else
        return calloc(count, size);
}

void *ExternalRamRealloc(void *ptr, size_t size)
{
    if (!ptr) return ExternalRamMalloc(size);
    if (size == 0) {
        heap_caps_free(ptr);
        return NULL;
    }
    void *ret = heap_caps_realloc(ptr, size, MALLOC_CAP_SPIRAM);
    if (ret)
        return ret;
    else
        return realloc(ptr, size);
}

void *InternalRamMalloc(size_t sz)
{
    void *ret = heap_caps_malloc(sz, MALLOC_CAP_INTERNAL | MALLOC_CAP_8BIT);
    if (ret)
        return ret;
    else
        return malloc(sz);
}

void *InternalRamCalloc(size_t count, size_t size)
{
    void *ret = heap_caps_malloc(count * size, MALLOC_CAP_INTERNAL | MALLOC_CAP_8BIT);
    if (ret) {
        bzero(ret, count * size);
        return ret;
    } else
        return calloc(count, size);
}

void *InternalRamRealloc(void *ptr, size_t size)
{
    if (!ptr) return InternalRamMalloc(size);
    if (size == 0) {
        heap_caps_free(ptr);
        return NULL;
    }
    void *ret = heap_caps_realloc(ptr, size, MALLOC_CAP_INTERNAL | MALLOC_CAP_8BIT);
    if (ret)
        return ret;
    else
        return realloc(ptr, size);
}

// void *operator new(std::size_t size)
// {
//     // printf("#####################ALLOCATING %d bytes\n", size);
//     void *ptr = heap_caps_malloc(size, MALLOC_CAP_SPIRAM);
//     if (!ptr) {
//         abort();
//     }
//     return ptr;
// }

// void *operator new[](std::size_t size)
// {
//     void *ptr = heap_caps_malloc(size, MALLOC_CAP_SPIRAM);
//     if (!ptr) {
//         abort();
//     }
//     return ptr;
// }

// void operator delete(void *ptr) noexcept
// {
//     // printf("#####################DEALLOCATING\n");
//     free(ptr);
// }

// void operator delete(void *ptr, std::size_t) noexcept
// {
//     // printf("#####################DEALLOCATING\n");
//     free(ptr);
// }

// void operator delete[](void *ptr) noexcept { free(ptr); }

// void operator delete[](void *ptr, std::size_t) noexcept { free(ptr); }

void *operator new(size_t size) { return ExternalRamMalloc(size); }

void *operator new[](size_t size) { return ExternalRamMalloc(size); }

static void *ExternalRamAllocated::operator new(std::size_t sz) { return ExternalRamMalloc(sz); }

static void *ExternalRamAllocated::operator new[](std::size_t sz) { return ExternalRamMalloc(sz); }

char *ExternalRamAllocated::strdup(const char *src)
{
    if (!src) return NULL;
    size_t size = strlen(src) + 1;
    char *dupe = (char *)ExternalRamMalloc(size);
    if (dupe) memcpy(dupe, src, size);
    return dupe;
}

int ExternalRamAllocated::asprintf(char **strp, const char *fmt, ...)
{
    int size = 0;
    va_list args;
    va_start(args, fmt);
    size = vasprintf(strp, fmt, args);
    va_end(args);
    return size;
}

int ExternalRamAllocated::vasprintf(char **strp, const char *fmt, va_list ap)
{
    int size = 0;
    char *p = NULL;

    // determine required size:
    va_list apsz;
    va_copy(apsz, ap);
    size = vsnprintf(NULL, 0, fmt, apsz);
    va_end(apsz);

    if (size < 0) return -1;

    size++; // for '\0'
    p = (char *)ExternalRamMalloc(size);
    if (p == NULL) return -1;

    size = vsnprintf(p, size, fmt, ap);
    if (size < 0) {
        free(p);
        return -1;
    }

    *strp = p;
    return size;
}

static void *InternalRamAllocated::operator new(std::size_t sz) { return InternalRamMalloc(sz); }

static void *InternalRamAllocated::operator new[](std::size_t sz) { return InternalRamMalloc(sz); }

char *InternalRamAllocated::strdup(const char *src)
{
    if (!src) return NULL;
    size_t size = strlen(src) + 1;
    char *dupe = (char *)InternalRamMalloc(size);
    if (dupe) memcpy(dupe, src, size);
    return dupe;
}

int InternalRamAllocated::asprintf(char **strp, const char *fmt, ...)
{
    int size = 0;
    va_list args;
    va_start(args, fmt);
    size = vasprintf(strp, fmt, args);
    va_end(args);
    return size;
}

int InternalRamAllocated::vasprintf(char **strp, const char *fmt, va_list ap)
{
    int size = 0;
    char *p = NULL;

    // determine required size:
    va_list apsz;
    va_copy(apsz, ap);
    size = vsnprintf(NULL, 0, fmt, apsz);
    va_end(apsz);

    if (size < 0) return -1;

    size++; // for '\0'
    p = (char *)InternalRamMalloc(size);
    if (p == NULL) return -1;

    size = vsnprintf(p, size, fmt, ap);
    if (size < 0) {
        free(p);
        return -1;
    }

    *strp = p;
    return size;
}

```