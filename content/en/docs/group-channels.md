---
title: Group Channels
categories: [End-User Documentation]
tags: [intro]
description: Describes the Group Channels
weight: 4
---

```mermaid
---
title: The Group Mixer
---
flowchart LR
  CMPA[Compressor A]
  EQUA[Equalizer A]
  CMPB[Compressor B]
  EQUB[Equalizer B]
  CMPC[Compressor C]
  EQUC[Equalizer C]
  CMPD[Compressor D]
  EQUD[Equalizer D]
  MIXL[Mixer L]
  MIXR[Mixer R]

  CMPA ==> EQUA --> MIXL
  CMPB ==> EQUB --> MIXL
  CMPC ==> EQUC --> MIXL
  CMPD ==> EQUD --> MIXL
  EQUA --> MIXR
  EQUB --> MIXR
  EQUC --> MIXR
  EQUD --> MIXR
```

## Plugins

|Purpose|Plugin|Link|
|--|--|--|
|Compressor|Calf Compressor|[Calf Studio Gear](https://calf-studio-gear.org/)|
|Equalizer|3-Band EQ from the Mini Series|[DISTRHO Mini Series](https://github.com/DISTRHO/Mini-Series)|
