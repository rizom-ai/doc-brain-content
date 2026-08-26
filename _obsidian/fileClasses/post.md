---
fields:
  - id: title
    name: title
    type: Input
  - id: slug
    name: slug
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
  - id: excerpt
    name: excerpt
    type: Input
  - id: author
    name: author
    type: Input
  - id: coverImageId
    name: coverImageId
    type: Input
  - id: ogImageId
    name: ogImageId
    type: Input
  - id: seriesName
    name: seriesName
    type: Input
  - id: seriesIndex
    name: seriesIndex
    type: Number
  - id: ogImage
    name: ogImage
    type: Input
  - id: ogDescription
    name: ogDescription
    type: Input
  - id: twitterCard
    name: twitterCard
    options:
      '0': summary
      '1': summary_large_image
    type: Select
  - id: canonicalUrl
    name: canonicalUrl
    type: Input
  - id: atprotoUri
    name: atprotoUri
    type: Input
filesPaths: post
---
