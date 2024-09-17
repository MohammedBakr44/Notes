![[home.jpg]]


```contributionGraph
title: Contributions
graphType: default
dateRangeValue: 180
dateRangeType: LATEST_DAYS
startOfWeek: 0
showCellRuleIndicators: true
titleStyle:
  textAlign: center
  fontSize: 15px
  fontWeight: normal
dataSource:
  type: PAGE
  value: ""
  dateField:
    type: FILE_MTIME
  filters: []
  countField:
    type: DEFAULT
fillTheScreen: false
enableMainContainerShadow: false
cellStyleRules:
  - id: Wine_a
    color: "#d8b0b3"
    min: 1
    max: 2
  - id: Wine_b
    color: "#c78089"
    min: 2
    max: 3
  - id: Wine_c
    color: "#ac4c61"
    min: 3
    max: 5
  - id: Wine_d
    color: "#830738"
    min: 5
    max: 9999
cellStyle:
  minHeight: 8px
  minWidth: 8px

```

## 最近
```dataview
LIST file.mtime
SORT file.mtime DESC
LIMIT 3
```

## カレンダー
```dataview
CALENDAR file.mtime AS "Date Modified"
SORT file.mtime DESC
```






























