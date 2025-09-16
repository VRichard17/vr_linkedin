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

Use the Task tool to invoke the `resume-analyzer` agent which will:

1. **Skills Extraction**: Extract all technical skills, tools, certifications
2. **Role Analysis**: Extract job titles, experience levels, career progression
3. **Industry Mapping**: Identify industries, domains, company types
4. **Experience Quantification**: Calculate years, leadership scope, project scale
5. **Geographic Data**: Extract location preferences and remote work experience
6. **LinkedIn Optimization**: Generate keywords and search filters

The agent provides:
- Structured JSON data for job matching algorithms
- LinkedIn keyword lists for search optimization
- Job search criteria and filters
- Target role recommendations
- Skill gap analysis for career development

**Input**: Resume file path (PDF, DOC, DOCX supported)
**Output**: Structured JSON data for LinkedIn job search automation

This command demonstrates the permission chain:
**Slash Command → Task Tool → Resume Analyzer Agent → File Reading → LinkedIn Data Extraction**