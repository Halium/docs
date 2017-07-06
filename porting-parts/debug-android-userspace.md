---
layout: page
date:   2017-04-24 10:07:34 +0530
permalink: /docs/Porting/DebugAndroidUserspace
---

## Debugging the Android userspace

Debugging the Android userspace

#### Logcat

Logcat is a tool that reads

```
/system/bin/logcat
```

For radio logs
```
/system/bin/logcat -b radio
```

#### dmesg

Even though Android logs does not normally end up in dmesg, early initialization of Android and kernel output ends up here.

```
dmesg
```

### Debug Libhybris crash

One of the main problems with the current Hybris based architecture, is the lack of symbols resolution and mapping once a crash happens at the Android layer. To workaround this we need to manuly import non stripped libaries
