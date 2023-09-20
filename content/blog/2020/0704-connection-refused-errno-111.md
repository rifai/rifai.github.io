---
title: 'SocketException: OS Error: Connection refused, errno = 111'
description: I got this weird error when developing flutter app in windows.
date: 2020-07-04
tags:
    - android
---

I encountered a peculiar error while developing a Flutter app on Windows. I had configured my local Apache server as the API server. When I tested the API using Postman, everything worked fine. However, the error surfaced when I tested the API within the app using an emulator.

As it turns out, the problem was with the emulator itself. Android emulators cannot communicate with **127.0.0.1** or **localhost**. The solution was straightforward: I replaced localhost with **10.0.2.2**. This IP address serves as a special alias to your host loopback interface.

For more details, you can refer to [this docs](https://developer.android.com/studio/run/emulator-networking)