---
fields:
  - id: conversationId
    name: conversationId
    type: Input
  - id: channelId
    name: channelId
    type: Input
  - id: channelName
    name: channelName
    type: Input
  - id: interfaceType
    name: interfaceType
    type: Input
  - id: spaceId
    name: spaceId
    type: Input
  - id: timeRange
    name: timeRange
    type: Input
  - id: sourceSummaryId
    name: sourceSummaryId
    type: Input
  - id: sourceMessageCount
    name: sourceMessageCount
    type: Number
  - id: projectionVersion
    name: projectionVersion
    type: Number
  - id: status
    name: status
    options:
      '0': open
      '1': done
      '2': dropped
    type: Select
  - id: assignedTo
    name: assignedTo
    type: Multi
  - id: requestedBy
    name: requestedBy
    type: Multi
filesPaths: action-item
---
