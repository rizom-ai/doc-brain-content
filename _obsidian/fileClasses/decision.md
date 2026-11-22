---
fields:
  - id: channelName
    name: channelName
    type: Input
  - id: interfaceType
    name: interfaceType
    type: Input
  - id: status
    name: status
    options:
      '0': active
      '1': superseded
    type: Select
  - id: startedAt
    name: startedAt
    type: Input
  - id: endedAt
    name: endedAt
    type: Input
  - id: decidedBy
    name: decidedBy
    type: Multi
  - id: mentionedBy
    name: mentionedBy
    type: Multi
filesPaths: decision
---
