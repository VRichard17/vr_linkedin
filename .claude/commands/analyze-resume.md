---
description: Extract LinkedIn job matching data from resume
argument-hint: <resume_file_path>
allowed-tools: ["*"]
---

Extract structured data from resume for LinkedIn job matching automation.

## Memory Bank Integration
Before starting:
1. Use `mcp__mem0__mem0_search("resume location")` to check for saved resume paths
2. Save analysis results to Mem0 using `mcp__mem0__mem0_add` with tags ["resume", "analysis", "skills"]
3. Store extracted job preferences for future searches

## Self-Learning Capabilities
The resume-analyzer agent will:
- Search for known parsing solutions before processing
- Document any new file format challenges
- Store successful extraction patterns for reuse
- Build a knowledge base of resume format variations

Use the Task tool to invoke the `resume-analyzer` agent to extract structured data from the resume for LinkedIn job matching.

**Goal**: Extract comprehensive job matching data from the resume including skills, experience, preferences, and generate LinkedIn-optimized search criteria.

**Input**: Resume file path (PDF, DOC, DOCX supported)
**Output**: Structured JSON data for LinkedIn job search automation

This command demonstrates the permission chain:
**Slash Command → Task Tool → Resume Analyzer Agent → File Reading → LinkedIn Data Extraction**