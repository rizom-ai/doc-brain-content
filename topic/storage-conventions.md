---
title: Storage Conventions
---
A substantial portion of the document details how entity storage works in the file system. Root markdown files become base note entities, while subdirectories like `brain-data/<entity-type>/` determine the entity type. Nested paths are converted into colon-separated IDs, which lets the runtime represent hierarchical content cleanly. The document also notes support for image files under `brain-data/image/` and explains the role of YAML frontmatter plus markdown bodies. These conventions are important because they define how content is persisted, synced, and interpreted by the runtime.
