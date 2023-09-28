---
title: Format Date String
description: Format Date String notes
date: 2020-01-10
tags:
  - date
  - format
---
To format the date string for Mountain Standard Time (MST), you can append the MST offset to the end of the date string. 

MST is `UTC-7`, so you can append `-07:00` to the end of the date string.

Here's an example:

```sh
2023-08-28T10:56:02-07:00
```

This will give you the following output:

```sh
Mon Aug 28 10:56:02 MDT 2023
```

Note that the output includes the abbreviation for Mountain Daylight Time (MDT), which is used during the summer months in the Mountain Time Zone. During the winter months, the zone uses Mountain Standard Time (MST), which is equivalent to UTC-7.

