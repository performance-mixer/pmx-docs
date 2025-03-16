---
title: Layer Channels
categories: [End-User Documentation]
tags: [intro]
description: Describes the Layer Channels
weight: 5
---

```mermaid
---
title: The Layer Mixer
---
flowchart LR
  CMPA[Compressor A]
  EQUA[Equalizer A]
  CMPB[Compressor B]
  EQUB[Equalizer B]
  MIXL[Mixer L]
  MIXR[Mixer R]

  CMPA ==> EQUA --> MIXL
  CMPB ==> EQUB --> MIXL
  EQUA --> MIXR
  EQUB --> MIXR
```

## Plugins

|Purpose|Plugin|Link|
|--|--|--|
|Compressor|Calf Compressor|[Calf Studio Gear](https://calf-studio-gear.org/)|
|Equalizer|3-Band EQ from the Mini Series|[DISTRHO Mini Series](https://github.com/DISTRHO/Mini-Series)|
