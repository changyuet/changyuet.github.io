---
layout: post
title: 编译nubia nx507 kernel error note
date: 2015-10-13
categories: blog
tags: [Android]

---
* 1
```
arch/arm/mach-msm/smd_init_dt.c:24:25: fatal error: smd_private.h: No such file or directory
```
打开arch/arm/mach-msm/smd_init_dt.c找到

#include <smd_private.h> 修改为 #include "smd_private.h"

 * 2
```
sound/soc/msm/pdsp6v2/rtac.c:28:21: error q6voice.sh No such file or directory
```
把sound/soc/msm/pdsp6v2/rtac.c 文件28行 #include <q6voice.h>改为 #include "q6voice.h"

 
* 3

修改hci_conn.c:407

cp.handle = cpu_to_le16(conn->handle);
```
- memcpy(cp.ltk, ltk, sizeof(*ltk));改为
+ memcpy(cp.ltk, ltk, sizeof(cp.ltk));
```
