---
fields:
  - id: title
    name: title
    type: Input
  - id: status
    name: status
    options:
      '0': draft
      '1': active
      '2': archived
    type: Select
  - id: audience
    name: audience
    options:
      '0': admin
      '1': trusted
      '2': public
    type: Select
  - id: trigger
    name: trigger
    type: Input
  - id: lifecycle
    name: lifecycle
    type: Input
  - id: once
    name: once
    type: Boolean
  - id: starterText
    name: starterText
    type: Input
  - id: description
    name: description
    type: Input
  - id: starterPrompt
    name: starterPrompt
    type: Input
  - id: completionMode
    name: completionMode
    options:
      '0': agent-confirmed
      '1': manual
    type: Select
filesPaths: playbook
---
