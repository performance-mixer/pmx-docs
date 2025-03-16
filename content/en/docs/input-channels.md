---
title: Input Channels
categories: [End-User Documentation]
tags: [intro]
description: Describes the Input Channels
weight: 3
---

```mermaid
---
title: One Input Channel
---
flowchart LR
  L[Left]
  R[Right]
  LC[Copy]
  RC[Copy]
  SATA[Saturator A]
  CMPA[Compressor A]
  EQUA[Equalizer A]
  SATB[Saturator B]
  CMPB[Compressor B]
  EQUB[Equalizer B]

  L --> LC --> SATA
  R --> RC --> SATA
  LC --> SATB
  RC --> SATB
  SATA ==> CMPA ==> EQUA
  SATB ==> CMPB ==> EQUB
```

## Plugins

|Purpose|Plugin|Link|
|--|--|--|
|Saturator|Calf Saturator|[Calf Studio Gear](https://calf-studio-gear.org/)|
|Compressor|Calf Compressor|[Calf Studio Gear](https://calf-studio-gear.org/)|
|Equalizer|3-Band EQ from the Mini Series|[DISTRHO Mini Series](https://github.com/DISTRHO/Mini-Series)|
