---
fields:
  - id: title
    name: title
    type: Input
  - id: slug
    name: slug
    type: Input
  - id: description
    name: description
    type: Input
  - id: author
    name: author
    type: Input
  - id: status
    name: status
    options:
      '0': generating
      '1': draft
      '2': queued
      '3': published
      '4': failed
    type: Select
  - id: publishedAt
    name: publishedAt
    type: Input
  - id: event
    name: event
    type: Input
  - id: coverImageId
    name: coverImageId
    type: Input
  - id: ogImageId
    name: ogImageId
    type: Input
filesPaths: deck
---
