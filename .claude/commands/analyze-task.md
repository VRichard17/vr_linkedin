---
description: Analyze a task and determine optimal execution strategy
argument-hint: <task_description>
allowed-tools: ["*"]
---

Analyze any task and orchestrate the optimal execution strategy using available agents and commands.

## Goal

Given a task description, analyze it and orchestrate the best execution approach by:
1. Understanding what needs to be accomplished
2. Identifying which agents and commands are best suited
3. Orchestrating their execution in the optimal sequence
4. Ensuring the task is completed successfully

## Memory Integration

- Search Mem0 for similar past tasks and successful patterns
- Retrieve relevant context, credentials, and preferences
- Store the analysis and results for future learning

## What to Provide to Task Orchestrator

Use the Task tool to invoke the `task-orchestrator` agent with:

**Input:**
- The complete task description from the user
- Any relevant context from memory
- Success criteria if specified

**Expected Outcomes:**
- Comprehensive task analysis and decomposition
- Optimal agent/command selection and sequencing
- Successful task execution with progress tracking
- Learning capture for future similar tasks

## Usage Examples

```bash
/analyze-task "Build a full-stack web application with user authentication"
/analyze-task "Research and summarize latest AI developments in healthcare"
/analyze-task "Automate daily report generation from multiple data sources"
/analyze-task "Create comprehensive test suite for existing codebase"
```

The task-orchestrator agent will determine the best approach, select appropriate agents, and manage the execution to achieve the desired outcome.