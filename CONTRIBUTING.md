# Contributing to BabelBlk Checker

Thank you for your interest in contributing to **BabelBlk Checker**! Your contributions help make this checklist a valuable resource for auditors and developers in the smart contract community. Whether you're suggesting new checklist items, improving existing content, or enhancing the documentation, your input is greatly appreciated.

## Table of Contents

1. [How Can You Contribute?](#how-can-you-contribute)
   - [Suggesting New Checklist Items](#suggesting-new-checklist-items)
   - [Improving Existing Items](#improving-existing-items)
   - [Enhancing Documentation](#enhancing-documentation)
   - [Reporting Issues](#reporting-issues)
2. [Contribution Guidelines](#contribution-guidelines)
   - [General Guidelines](#general-guidelines)
   - [Style Guide](#style-guide)
   - [Formatting Checklist Items](#formatting-checklist-items)
3. [Submitting Contributions](#submitting-contributions)
   - [Forking the Repository](#forking-the-repository)
   - [Creating a Branch](#creating-a-branch)
   - [Making Changes](#making-changes)
   - [Commit Messages](#commit-messages)
   - [Submitting a Pull Request](#submitting-a-pull-request)

---

## How Can You Contribute?

### Suggesting New Checklist Items

We welcome the addition of new items to the checklist. If you have identified a critical aspect of smart contract auditing that is not currently covered, please consider adding it.

1. **Open an Issue**: Start by opening an issue to discuss your proposed checklist item with the community.
2. **Gather Feedback**: Engage with maintainers and contributors to refine your idea.
3. **Submit a Pull Request**: Once agreed upon, follow the [Submitting Contributions](#submitting-contributions) guidelines to add your item.

### Improving Existing Items

Enhancements to current checklist items, including clarifications, additional potential issues, or updated references, are highly encouraged.

- **Direct Edits**: For minor changes, you can submit a pull request without opening an issue.
- **Discussion First**: For significant changes, please open an issue to discuss your proposed edits.

### Enhancing Documentation

If you find areas where the documentation can be improved for better clarity or completeness, please contribute your suggestions.

- **Structural Changes**: Open an issue to discuss major documentation overhauls.

### Reporting Issues

If you encounter any problems or have concerns about the checklist, please report them by opening an issue.

- **Reports**: Describe the issue in detail, including steps to reproduce if applicable.
- **Feedback**: Share your thoughts on how we can improve the checklist.

---

## Contribution Guidelines

### General Guidelines

- **Be Respectful**: Maintain a professional and respectful tone in all interactions.
- **Stay On Topic**: Ensure your contributions are relevant to smart contract language auditing.
- **Collaborate**: Engage with the community for feedback and be open to suggestions.

### Style Guide

- **Language**: Use clear, concise, and formal language suitable for a professional audience.
- **Tone**: Maintain an informative and neutral tone throughout.
- **Terminology**: Use consistent terminology, especially for technical terms.
- **Spelling and Grammar**: Ensure your contributions are free of spelling and grammatical errors.

### Formatting Checklist Items

When adding or editing checklist items, please adhere to the following format to maintain consistency:

- **Ref Number**: Use the category code (e.g., `LS` for Language Syntax and Semantics) followed by a hyphen and a three-digit unique number (e.g., `LS-007`).
- **Name**: Provide a concise, descriptive title for the checklist item.
- **Objective**: Clearly state the goal of the checklist item and its importance in auditing.
- **Potential Issues**: List potential problems that could arise if the item is not addressed, formatted as a bulleted list.

**Note:** Include any relevant links or citations that support the item.

#### Example Template

```markdown
| Ref Number | Name                         | Objective | Potential Issues |
|------------|------------------------------|-----------|------------------|
| XX-XXX     | [Checklist Item Name]        | [Objective] | <ul><li>[Issue 1]</li><li>[Issue 2]</li></ul> |
```

---

## Submitting Contributions

### Forking the Repository

1. **Fork**: Click the 'Fork' button on the top right corner of the repository page to create a copy in your GitHub account.

### Creating a Branch

1. **Clone**: Clone your forked repository to your local machine.
   ```bash
   git clone https://github.com/your-username/babelblk-checker.git
   ```
2. **Branch**: Create a new branch for your contribution.
   ```bash
   git checkout -b feature/your-feature-name
   ```

### Making Changes

- **Edit Files**: Make your changes in the appropriate markdown files.
- **Follow Guidelines**: Ensure your edits comply with the [Style Guide](#style-guide) and [Formatting Checklist Items](#formatting-checklist-items).

### Commit Messages

- **Descriptive**: Write clear and descriptive commit messages.
- **Format**: Use the imperative mood (e.g., "Add new checklist item for XYZ").

### Submitting a Pull Request

1. **Push Changes**: Push your branch to your forked repository.
   ```bash
   git push origin feature/your-feature-name
   ```
2. **Create Pull Request**: Go to the original repository and click 'New Pull Request'.
3. **Provide Details**: Fill out the pull request template with all necessary information.
4. **Submit**: Click 'Create Pull Request' to submit.

---

If you have any questions or need assistance, feel free to reach out by opening an issue or contacting the maintainers.
