---
fields:
  - id: name
    name: name
    type: Input
  - id: kind
    name: kind
    options:
      '0': person
      '1': team
      '2': organization
    type: Select
  - id: organization
    name: organization
    type: Input
  - id: brainName
    name: brainName
    type: Input
  - id: url
    name: url
    type: Input
  - id: did
    name: did
    type: Input
  - id: repoDid
    name: repoDid
    type: Input
  - id: brainDid
    name: brainDid
    type: Input
  - id: anchorDid
    name: anchorDid
    type: Input
  - id: cardUri
    name: cardUri
    type: Input
  - id: cardCid
    name: cardCid
    type: Input
  - id: cardObservedAt
    name: cardObservedAt
    type: Input
  - id: cardLastCheckedAt
    name: cardLastCheckedAt
    type: Input
  - id: cardLastError
    name: cardLastError
    type: Input
  - id: cardFailureCount
    name: cardFailureCount
    type: Number
  - id: cardUnavailableAt
    name: cardUnavailableAt
    type: Input
  - id: cardStaleAfter
    name: cardStaleAfter
    type: Input
  - id: a2aEndpoint
    name: a2aEndpoint
    type: Input
  - id: status
    name: status
    options:
      '0': discovered
      '1': approved
      '2': archived
    type: Select
  - id: discoveredAt
    name: discoveredAt
    type: Input
  - id: introducedBy
    name: introducedBy
    type: Multi
  - id: hops
    name: hops
    type: Number
filesPaths: agent
---
