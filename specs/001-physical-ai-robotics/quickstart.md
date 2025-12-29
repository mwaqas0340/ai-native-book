# Quickstart: Physical AI & Humanoid Robotics Book

## Overview
This quickstart guide provides the essential information to understand and work with the Physical AI & Humanoid Robotics textbook project.

## Project Setup

### Prerequisites
- Node.js (version 18 or higher)
- npm or yarn package manager
- Git for version control

### Initial Setup
1. Clone the repository
2. Navigate to the `my-website` directory
3. Install dependencies: `npm install`
4. Start the development server: `npm start`

## Book Structure

### Directory Structure
```
my-website/
├── docs/
│   ├── chapter-1.md
│   ├── chapter-2.md
│   ├── chapter-3.md
│   ├── chapter-4.md
│   └── chapter-5.md
├── static/
│   └── img/
├── src/
│   └── components/
├── docusaurus.config.js
├── sidebars.js
└── package.json
```

### Content Organization
- **docs/**: Contains all book chapters in Markdown format
- **static/img/**: Stores images, diagrams, and illustrations
- **src/components/**: Custom Docusaurus components
- **docusaurus.config.js**: Main Docusaurus configuration
- **sidebars.js**: Navigation sidebar configuration

## Creating Content

### Chapter Format
Each chapter follows this basic structure:

```markdown
---
title: Chapter Title
sidebar_position: X
description: Brief description of the chapter
---

# Chapter Title

## Section 1

Content for section 1...

### Subsection 1.1

Content for subsection...

## Section 2

Content for section 2...

### Code Examples

import CodeBlock from '@theme/CodeBlock';
import { useState } from 'react';

```python
# Example Python code
def example_function():
    print("Hello, Physical AI!")
```

### Labs and Exercises

:::info Lab Exercise
**Objective**: Understand basic ROS 2 concepts
**Requirements**: ROS 2 installation, basic Python knowledge
**Steps**: ...
:::

### Image Placeholders

![Image Description](/img/image-placeholder.png)
```

## Key Technologies

### ROS 2 (Robot Operating System 2)
- **Purpose**: Middleware for robotics applications
- **Key Concepts**: Nodes, Topics, Services, Actions
- **Languages**: C++ and Python APIs

### Simulation Environments
- **Gazebo**: Physics-based simulation
- **Unity**: Game engine for robotics
- **NVIDIA Isaac Sim**: GPU-accelerated simulation

### Vision-Language-Action (VLA) Systems
- **Definition**: Systems integrating vision, language, and action
- **Examples**: RT-1, RT-2, ALOHA systems
- **Applications**: Robotic manipulation tasks

## Development Workflow

### 1. Content Creation
- Create new Markdown files in the `docs/` directory
- Follow the established chapter format
- Include code examples and labs where appropriate
- Add image placeholders in the `static/img/` directory

### 2. Navigation Setup
- Update `sidebars.js` to include new content in navigation
- Set proper sidebar positions for ordering
- Create cross-links between related content

### 3. Testing
- Run `npm start` to launch development server
- Review content in browser
- Check cross-links and navigation
- Verify code examples render correctly

### 4. Building
- Run `npm run build` to create production build
- Test locally with `npm run serve`
- Deploy to static hosting platform

## Best Practices

### Content Standards
- Maintain university-level educational quality
- Ensure technical accuracy in all examples
- Provide clear explanations with depth
- Follow modular structure for reusability

### Code Examples
- Include both Python and C++ examples where relevant
- Provide clear explanations for each code snippet
- Test examples in appropriate environments
- Use consistent formatting and styling

### Images and Diagrams
- Use descriptive alt text for accessibility
- Include captions explaining image content
- Store in `static/img/` directory
- Use appropriate file formats (PNG, SVG, JPG)

## Common Commands

```bash
# Install dependencies
npm install

# Start development server
npm start

# Build for production
npm run build

# Serve production build locally
npm run serve

# Deploy to hosting platform
npm run deploy
```

## Next Steps

1. Review the complete implementation plan in `plan.md`
2. Check the detailed data model in `data-model.md`
3. Explore API contracts in the `contracts/` directory
4. Review the task breakdown in `tasks.md`
5. Begin with Chapter 1 content creation