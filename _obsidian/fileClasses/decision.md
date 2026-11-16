---
fields:
  - id: channelName
    name: channelName
    type: Input
  - id: interfaceType
    name: interfaceType
    type: Input
  - id: timeRange
    name: timeRange
    type: Input
  - id: status
    name: status
    options:
      '0': active
      '1': superseded
    type: Select
  - id: decidedBy
    name: decidedBy
    type: Multi
  - id: mentionedBy
    name: mentionedBy
    type: Multi
filesPaths: decision
---
