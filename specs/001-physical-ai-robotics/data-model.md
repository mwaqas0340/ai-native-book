# Data Model: Physical AI & Humanoid Robotics Book

## Overview
This document defines the data structures and entities for the Physical AI & Humanoid Robotics textbook project.

## Book Structure Model

### Book Entity
- **name**: String - Title of the book
- **description**: String - Brief description of the book's content
- **chapters**: Array<Chapter> - List of chapters in the book
- **authors**: Array<String> - List of authors
- **version**: String - Version of the book

### Chapter Entity
- **id**: String - Unique identifier for the chapter
- **title**: String - Title of the chapter
- **number**: Integer - Chapter number
- **description**: String - Brief description of chapter content
- **sections**: Array<Section> - List of sections within the chapter
- **learningObjectives**: Array<String> - Learning objectives for the chapter
- **prerequisites**: Array<String> - Prerequisites for understanding the chapter
- **estimatedReadingTime**: Integer - Estimated reading time in minutes

### Section Entity
- **id**: String - Unique identifier for the section
- **title**: String - Title of the section
- **content**: String - Main content of the section (Markdown format)
- **subsections**: Array<Section> - Nested subsections
- **examples**: Array<Example> - Code examples and practical demonstrations
- **labs**: Array<Laboratory> - Hands-on laboratory exercises
- **images**: Array<Image> - Image placeholders and references

### Example Entity
- **id**: String - Unique identifier for the example
- **title**: String - Title of the example
- **description**: String - Brief description of the example
- **code**: String - Code snippet (with language specification)
- **language**: String - Programming language (e.g., "python", "cpp")
- **explanation**: String - Explanation of the example

### Laboratory Entity
- **id**: String - Unique identifier for the lab
- **title**: String - Title of the laboratory exercise
- **objectives**: Array<String> - Learning objectives of the lab
- **requirements**: Array<String> - Software/hardware requirements
- **steps**: Array<String> - Step-by-step instructions
- **expectedOutcome**: String - Expected result of the lab
- **troubleshooting**: Array<String> - Common issues and solutions

### Image Entity
- **id**: String - Unique identifier for the image
- **title**: String - Title/description of the image
- **path**: String - Path to the image file
- **altText**: String - Alternative text for accessibility
- **caption**: String - Caption for the image
- **type**: String - Type of image (diagram, chart, photo, etc.)

## Content Relationships

### Book contains Chapters
- **Cardinality**: One-to-Many (1:M)
- **Description**: A book contains multiple chapters in a specific order

### Chapter contains Sections
- **Cardinality**: One-to-Many (1:M)
- **Description**: A chapter contains multiple sections, some of which may have nested subsections

### Section contains Examples
- **Cardinality**: One-to-Many (1:M)
- **Description**: A section may contain multiple code examples

### Section contains Labs
- **Cardinality**: One-to-Many (1:M)
- **Description**: A section may contain multiple laboratory exercises

### Section contains Images
- **Cardinality**: One-to-Many (1:M)
- **Description**: A section may reference multiple images

## Validation Rules

### Book Validation
- Must have at least 1 chapter
- Title cannot be empty
- All chapters must have unique numbers

### Chapter Validation
- Must have at least 1 section
- Chapter number must be unique within the book
- Title cannot be empty

### Section Validation
- Content cannot be empty
- Title cannot be empty
- Subsections must be properly nested (max 3 levels deep)

### Example Validation
- Code cannot be empty
- Language must be specified
- Must have an explanation

### Laboratory Validation
- Must have at least 1 step
- Objectives cannot be empty
- Requirements should be specified

## State Transitions

### Chapter State
- **Draft**: Initial state, content is being written
- **Review**: Content is under review
- **Approved**: Content has been approved
- **Published**: Content is published in the book

### Example State
- **Concept**: Idea for example is proposed
- **Implementation**: Example code is being written
- **Tested**: Example has been tested and verified
- **Integrated**: Example is integrated into the content

## Cross-Reference Model

### Internal References
- **targetId**: String - ID of the referenced entity
- **type**: String - Type of entity being referenced (chapter, section, example, etc.)
- **text**: String - Text to display for the reference
- **context**: String - Context of where the reference is used

### External References
- **url**: String - URL to external resource
- **title**: String - Title of the external resource
- **description**: String - Brief description of the resource
- **accessDate**: Date - Date when the resource was accessed