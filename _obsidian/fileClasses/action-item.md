---
fields:
  - id: origin
    name: origin
    options:
      '0': conversation
      '1': inbox
      '2': board
    type: Select
  - id: conversationId
    name: conversationId
    type: Input
  - id: interfaceType
    name: interfaceType
    type: Input
  - id: channelId
    name: channelId
    type: Input
  - id: channelName
    name: channelName
    type: Input
  - id: sourceRef
    name: sourceRef
    type: Input
  - id: capturedAt
    name: capturedAt
    type: Input
  - id: status
    name: status
    options:
      '0': open
      '1': doing
      '2': blocked
      '3': done
      '4': dropped
    type: Select
  - id: assignedTo
    name: assignedTo
    type: Multi
  - id: requestedBy
    name: requestedBy
    type: Multi
  - id: projectedBodyHash
    name: projectedBodyHash
    type: Input
filesPaths: action-item
---
