---
description: Complete LinkedIn job search automation with authentication, analysis, and search
argument-hint: [resume_path] [browser_mode]
allowed-tools: ["*"]
---

Complete LinkedIn job search automation workflow combining authentication, resume analysis, and intelligent job searching.

## MANDATORY: TodoWrite Tool Usage
**CRITICAL REQUIREMENT**: This slash command MUST use the TodoWrite tool throughout execution to track all major workflow steps and provide visibility to the user. Create todos for each of the 5 major steps at the beginning and update them as each step progresses. All invoked agents are also required to use TodoWrite for their internal step tracking. This comprehensive todo tracking is not optional - it ensures complete transparency and progress monitoring throughout the entire automation pipeline.

## Memory Bank Integration
Before starting:
1. Use `mcp__mem0__mem0_list()` to retrieve all user context and preferences
2. Search for "applied jobs" to avoid duplicate applications
3. Get "resume location" and "personal information" from memory
4. Store application results and track success rates

## Self-Learning & Continuous Improvement
Throughout the workflow:
- Each agent searches for known problems and applies learned solutions
- New challenges are documented with their resolutions
- Successful patterns are extracted and stored for future use
- The system becomes more effective with each execution

## Five-Step Automated Workflow

**STEP 0: Initialize Workflow Todo Tracking**
- Use TodoWrite to create todos for all 5 major workflow steps:
  - LinkedIn Authentication (with session detection)
  - Resume Analysis (with intelligent caching)
  - LinkedIn Job Search (with multi-strategy approach)
  - Job URL Collection (with pagination handling)
  - Semantic Job Application (with batch processing)
- Mark each step as in_progress when starting and completed when finished
- Each invoked agent will also create their own detailed todo tracking

**Step 1: LinkedIn Authentication**
Use the Task tool to invoke the `linkedin-login` agent.
**Goal**: Establish authenticated LinkedIn session.

**Step 2: Resume Analysis**
Use the Task tool to invoke the `resume-analyzer` agent.
**Goal**: Extract and cache job matching data from resume.

**Step 3: Job Search**
Use the Task tool to invoke the `linkedin-job-search` agent.
**Goal**: Search LinkedIn for relevant jobs based on resume analysis, focusing on recent postings.

**Step 4: Job URL Collection**
Use the Task tool to invoke the `linkedin-job-collector` agent.
**Goal**: Collect all job URLs from search results and save to daily session file.

**Step 5: Batch Job Applications**
For each collected job URL, use the Task tool to invoke the `linkedin-job-applicator` agent.
**Goal**: Apply to each job using appropriate method (Easy Apply or external), tracking progress with TodoWrite.

## Arguments
- `$1` - Resume file path (required)
- `$2` - Browser mode: "visible" (default) or "headless"

## Complete Automated Workflow
1. **LinkedIn Authentication**: Smart login with session detection
2. **Resume Processing**: Cached analysis with job matching data extraction
3. **Job Search Execution**: Multi-strategy search with fresh job filtering
4. **URL Collection**: Systematic harvesting of job URLs from all result pages
5. **Semantic Job Application**: Batch processing of collected job URLs with individual application tracking
6. **Results Integration**: Comprehensive reporting with application success rates and recommendations

## Expected Output

**LinkedIn Session:**
- Authenticated user profile verification
- Active session with full job search access
- Snapshot documentation using browser_snapshot (snapshotFrameForAI)

**Resume Analysis:**
- Cached JSON with target roles, skills, industries
- LinkedIn-optimized keywords and search criteria
- Experience level and salary expectations
- Location preferences and remote work indicators

**Job Search Results:**
- Multiple search iterations (primary, secondary, skills-based)
- Fresh job opportunities (Last 24 hours default)
- Results count and top matches per search strategy
- Company insights and salary data
- Recommended next steps and application priorities

**URL Collection:**
- Complete job URL list saved to `sessions/<today-date>/jobs.txt`
- Deduplicated URLs from all search result pages
- Ready for batch processing and application tracking
- Daily collection file supports multiple search sessions

**Job Application Results:**
- **Individual todo tracking** for each job application with real-time progress
- Application attempts logged in `sessions/<today-date>/applications.log`
- Success/failure status for each job URL processed
- Snapshots documenting application completion for each job using browser_snapshot (snapshotFrameForAI)
- Form filling intelligence using semantic field detection
- Contextual responses to company-specific screening questions
- Application tracking numbers and confirmation details
- **Batch summary report** with total applications attempted, success rate, and failure analysis

This demonstrates the complete multi-agent permission chain:
**Slash Command → Task Tool → LinkedIn Login Agent → Playwright MCP Server**
                **→ Task Tool → Resume Analyzer Agent → File System + Caching**
                **→ Task Tool → Job Search Agent → LinkedIn Jobs Automation**
                **→ Task Tool → LinkedIn Job Collector → URL Harvesting + File Storage**
                **→ Task Tool → LinkedIn Job Applicator → Semantic Application + Success Tracking**