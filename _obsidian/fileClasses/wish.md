---
fields:
  - id: title
    name: title
    type: Input
  - id: status
    name: status
    options:
      '0': new
      '1': planned
      '2': in-progress
      '3': done
      '4': declined
    type: Select
  - id: priority
    name: priority
    options:
      '0': low
      '1': medium
      '2': high
      '3': critical
    type: Select
  - id: requested
    name: requested
    type: Number
  - id: declinedReason
    name: declinedReason
    type: Input
filesPaths: wish
---
