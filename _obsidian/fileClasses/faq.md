---
fields:
  - id: question
    name: question
    type: Input
  - id: status
    name: status
    options:
      '0': draft
      '1': published
    type: Select
  - id: asked
    name: asked
    type: Number
  - id: sources
    name: sources
    type: Multi
  - id: review
    name: review
    options:
      '0': source-withdrawn
    type: Select
  - id: rank
    name: rank
    type: Number
filesPaths: faq
---
