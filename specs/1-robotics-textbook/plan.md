# Implementation Plan: Robotics Textbook Generation System

**Branch**: `1-robotics-textbook` | **Date**: 2025-12-07 | **Spec**: [specs/1-robotics-textbook/spec.md](specs/1-robotics-textbook/spec.md)
**Input**: Feature specification from `/specs/1-robotics-textbook/spec.md`

**Note**: This template is filled in by the `/sp.plan` command. See `.specify/templates/commands/plan.md` for the execution workflow.

## Summary

This plan outlines the detailed approach for creating the "Physical AI & Humanoid Robotics – Embodied Intelligence in the Real World" textbook. It covers project structure, content generation pipeline, Docusaurus integration for documentation, and automation strategies for content updates and regeneration, incorporating the use of context 7 MCP server for Docusaurus documentation.

## Technical Context

**Language/Version**: Python 3.10+ (for content generation scripts, ROS 2 `rclpy`), C# (for Unity examples), Markdown/MDX (for book content)
**Primary Dependencies**: ROS 2, Gazebo, Unity, NVIDIA Isaac Sim, Docusaurus, OpenAI Whisper (for voice-to-action concepts)
**Storage**: Filesystem (for all book content, Docusaurus assets, code examples)
**Testing**: Automated content quality checks (linting, broken links), manual technical review by subject matter experts, Docusaurus build validation
**Target Platform**: Web (Docusaurus-generated static site)
**Project Type**: Documentation/Book Generation System
**Performance Goals**: Efficient generation of chapter content (e.g., single chapter regeneration under 5 minutes), fast Docusaurus build times (e.g., full build under 15 minutes)
**Constraints**: Adherence to "Book Creation System Constitution" principles (Clarity, Accuracy, Depth, Structure, Modularity), consistent course-style formatting, technical accuracy across all focus areas.
**Scale/Scope**: 19 chapters across 4 parts, extensive subtopics, numerous code examples, diagrams, and potential voice/video placeholders.
**Docusaurus Integration**: Use context 7 MCP server for dynamic content fetching or enhanced functionalities within the Docusaurus documentation.

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

*   **Clarity**: The plan ensures clear and concise content generation through structured outlines and review processes. (PASS)
*   **Accuracy**: The plan mandates technical reviews and verification against authoritative sources for accuracy. (PASS)
*   **Depth**: The plan supports deeply explained content via comprehensive subtopics and detailed examples. (PASS)
*   **Structure**: The plan strictly adheres to the PARTS → CHAPTERS → SUBTOPICS structure and Docusaurus hierarchy. (PASS)
*   **Modularity**: The plan promotes modular content generation and organization, allowing for flexible updates and regeneration. (PASS)

## Project Structure

### Documentation (this feature)

```text
specs/1-robotics-textbook/
├── plan.md              # This file (/sp.plan command output)
├── research.md          # Phase 0 output (/sp.plan command)
├── data-model.md        # Phase 1 output (/sp.plan command)
├── quickstart.md        # Phase 1 output (/sp.plan command)
├── contracts/           # Phase 1 output (/sp.plan command)
└── tasks.md             # Phase 2 output (/sp.tasks command - NOT created by /sp.plan)
```

### Source Code (repository root)

```text
book-generation-system/
├── scripts/             # Python scripts for content generation, automation
├── templates/           # Templates for chapter generation, code snippets
└── config/              # Configuration files for content generation, Docusaurus

docs/                    # Docusaurus project root
├── src/                 # Docusaurus source files (custom components, themes)
├── blog/                # Docusaurus blog (if used)
├── community/           # Docusaurus community docs (if used)
├── static/              # Static assets for Docusaurus (favicon, global images)
├── assets/              # Specifically for book images and diagrams
│   ├── images/
│   └── diagrams/
├── parts/               # Contains subdirectories for each PART
│   ├── part1-foundations-ai/
│   │   ├── chapter1-introduction-ros2.mdx
│   │   ├── chapter2-ros2-communication-model.mdx
│   │   └── ...
│   ├── part2-digital-twin/
│   │   └── ...
│   ├── part3-ai-robot-brain/
│   │   └── ...
│   └── part4-vision-language-action/
│       └── ...
├── sidebar.js           # Docusaurus sidebar configuration
└── docusaurus.config.js # Main Docusaurus configuration

examples/                # Standalone code examples, projects for book chapters
├── ros2-basics/
├── gazebo-models/
├── unity-hri-projects/
└── isaac-sim-rl/
```

**Structure Decision**: The project will adopt a dual-root structure: `book-generation-system/` for the content generation logic and `docs/` for the Docusaurus-based book content. A separate `examples/` directory will host standalone code projects. This ensures a clean separation between the generation system and the generated book content, aligning with modularity principles.

## Chapter-wise Content Generation Pipeline

1.  **Content Outline Generation**: The existing `spec.md` serves as the primary outline. For each chapter and subtopic, a dedicated generation task will be initiated.
2.  **Initial Content Drafting**: For each subtopic, an AI agent will draft the core technical explanation, ensuring depth and accuracy based on the subtopic description.
3.  **Code Example Integration**: AI agents will generate relevant code examples (Python for ROS 2/VLA, C# for Unity) based on the subtopic context. These examples will be placed in the `examples/` directory and referenced in the MDX files.
4.  **Diagram Generation/Placeholder**: For concepts requiring visual explanation, AI agents will generate text-based diagrams (e.g., Mermaid, PlantUML) directly within the MDX, or create explicit placeholders for complex visual assets to be designed later. These assets will reside in `docs/assets/diagrams/`.
5.  **Review & Refinement**: Each drafted chapter and its assets will undergo automated checks (linting, broken links) and human review by a robotics educator/engineer for technical accuracy, clarity, and adherence to formatting standards.
6.  **MDX Conversion & Formatting**: Content will be formatted into MDX files (`.mdx`), incorporating Docusaurus-specific syntax for features like collapsible sections, admonitions, and image embedding. The `context 7 MCP server` will be utilized here to potentially pull dynamic content or real-time data if needed for the documentation.

## Naming Conventions for All Chapters

*   **Part Directories**: `docs/parts/partX-part-title-slug/` (e.g., `part1-foundations-ai/`)
*   **Chapter Files**: `chapterX-chapter-title-slug.mdx` (e.g., `chapter1-introduction-ros2.mdx`)
*   **Image/Diagram Assets**: `docs/assets/images/chapterX-image-description.png` or `docs/assets/diagrams/chapterX-diagram-description.svg`
*   **Code Example Folders**: `examples/chapterX-example-project-slug/`

## Integration with Docusaurus for Documentation

*   **/docs folder structure**: The root of the Docusaurus project will be `docs/`. Content will be organized under `docs/parts/` with subdirectories for each part, containing individual `.mdx` files for chapters.
*   **Sidebar configuration**: A `docs/sidebar.js` file will be created to define the navigation structure, dynamically generating entries for each part and chapter based on the `docs/parts/` directory structure. This will ensure consistency with the book's hierarchy.
*   **MDX files for each chapter**: Each chapter will be an independent `.mdx` file, allowing for rich content, embedded code, and interactive components. The `context 7 MCP server` will be integrated into the Docusaurus setup to enable specific documentation features, potentially for real-time code execution environments, interactive simulations, or dynamic content delivery.
*   **Assets folder for images and diagrams**: A dedicated `docs/assets/` directory will store all static visual assets, categorized into `images/` and `diagrams/` for clear organization.

## Plan for Generating Code Examples, Diagrams, Voice/Video Placeholders

*   **Code Examples**: Automated generation scripts within `book-generation-system/scripts/` will take subtopic context and generate code snippets, ensuring they are runnable and illustrative. A manual review step will verify correctness and educational value. These will be outputted to `examples/` and referenced from MDX.
*   **Diagrams**: For conceptual diagrams (e.g., architectural flows, data pipelines), text-to-diagram tools like Mermaid or PlantUML will be integrated into the generation process. For more complex 3D visualizations or mechanical drawings, placeholders will be generated, explicitly marking locations for future design by a human artist. These will be stored in `docs/assets/diagrams/`.
*   **Voice/Video Placeholders (Optional)**: If desired, a markdown syntax will be defined for embedding voice/video placeholders within the MDX content (e.g., `{{VOICE_EXPLANATION: [topic]}}` or `{{VIDEO_DEMO: [link]}}`). This will allow for future integration of multimedia content without altering the core generation logic.

## Automation Plan

*   **How future content updates will be added using CLI**: A `book-cli` tool (under `book-generation-system/cli/`) will be developed. It will include commands such as `book-cli update chapter <chapter-id> --content <new-content>` or `book-cli update subtopic <chapter-id> <subtopic-title> --content <new-content>`. This CLI will parse the existing MDX, apply updates, and re-trigger necessary generation steps.
*   **How to regenerate specific chapters without touching others**: The `book-cli` will support a `book-cli generate chapter <chapter-id>` command. This command will identify the specific chapter's MDX file, its associated code examples, and diagrams. It will then execute the content generation pipeline (drafting, code, diagrams, review, MDX conversion) only for that specific chapter, leaving other chapters untouched. This modular regeneration will be crucial for efficient iterative development and updates. The Docusaurus build process will then re-index the updated content.
