---
description: Thoroughly analyze a task and orchestrate optimal agent execution strategy
argument-hint: <task_description>
allowed-tools: ["*"]
---

Comprehensively analyze any task and orchestrate the optimal execution strategy using specialized agents and commands.

## MANDATORY: TodoWrite Tool Usage
**CRITICAL REQUIREMENT**: This slash command MUST use the TodoWrite tool to track all analysis phases and orchestration steps. Create todos for each major phase (Task Analysis, Memory Context, Strategy Planning, Orchestration Execution, Results Integration) and update them as progress is made. This ensures complete transparency of the analysis and orchestration process.

## Memory Bank Integration
Before task analysis:
1. Use `mcp__mem0__mem0_search("task patterns")` to find similar past tasks
2. Search for "successful strategies" and "problem solutions" related to the task domain
3. Retrieve user preferences, credentials, and contextual information
4. Store the task analysis and execution results for future learning

## Self-Learning Capabilities
The task analyzer will:
- Search for known task patterns and apply proven strategies
- Document new task types and successful orchestration patterns
- Extract reusable workflows from complex task decomposition
- Build a knowledge base of task → agent mappings

## Comprehensive Task Analysis Process

**Step 1: Task Understanding & Decomposition**
Use the Task tool to invoke the `task-orchestrator` agent with detailed instructions to:

1. **Parse Task Requirements**:
   - Extract explicit goals and implicit objectives
   - Identify required outputs and success criteria
   - Detect constraints, deadlines, and dependencies
   - Recognize domain context (coding, research, automation, etc.)

2. **Memory Context Gathering**:
   - Search Mem0 for relevant past experiences
   - Retrieve user preferences and credentials
   - Identify applicable learned patterns
   - Gather domain-specific knowledge

3. **Resource & Capability Mapping**:
   - Scan all available agents in `.claude/agents/`
   - Review available slash commands in `.claude/commands/`
   - Identify required tools and permissions
   - Map task components to agent capabilities

4. **Strategy Formulation**:
   - Determine optimal agent sequencing
   - Identify parallelizable vs sequential steps
   - Plan data flow between agents
   - Design fallback strategies for potential failures

5. **Orchestration Execution**:
   - Execute agents in optimal sequence/parallel structure
   - Pass structured data between agent invocations
   - Monitor progress and adapt to results
   - Handle errors with intelligent retry/fallback

6. **Results Integration & Learning**:
   - Consolidate outputs from all agents
   - Verify task completion against success criteria
   - Extract patterns for future similar tasks
   - Store successful strategies in Mem0

## Task Orchestrator Instructions Template

When invoking the task-orchestrator, provide these structured instructions:

```
TASK ANALYSIS REQUEST:
1. Task Description: [User's task description]
2. Success Criteria: [What defines successful completion]
3. Available Context: [Any relevant context from memory]
4. Priority: [Time-sensitive, quality-focused, or balanced]

ANALYSIS REQUIREMENTS:
- Identify all subtasks and dependencies
- Map each subtask to optimal agent/command
- Determine execution order and parallelization opportunities
- Plan data handoffs between agents
- Design error handling and fallback strategies

ORCHESTRATION PLAN:
- Break down the task into atomic operations
- For each operation, identify:
  * Required agent/command
  * Input data needed
  * Expected output
  * Dependencies on other operations
  * Fallback options

EXECUTION STRATEGY:
- Execute with progress tracking via TodoWrite
- Monitor each agent's output
- Adapt plan based on intermediate results
- Ensure data consistency between steps
- Validate final output against requirements
```

## Intelligent Agent Selection

The task-orchestrator will intelligently select from available agents based on task requirements:

**For Development Tasks:**
- Code generation, refactoring, debugging agents
- Testing and documentation agents
- Build and deployment automation

**For Research Tasks:**
- Web search and information gathering agents
- Data analysis and summarization agents
- Fact-checking and validation agents

**For Automation Tasks:**
- Browser automation agents (Playwright-based)
- API integration agents
- Data processing and transformation agents

**For Creative Tasks:**
- Content generation agents
- Design and formatting agents
- Translation and adaptation agents

## Expected Output

**Task Analysis Report:**
- Decomposed task structure with dependencies
- Required agents and their roles
- Execution timeline and sequencing
- Risk assessment and mitigation strategies

**Orchestration Plan:**
- Step-by-step execution roadmap
- Agent invocation sequence with parameters
- Data flow diagram between agents
- Fallback procedures for each step

**Execution Results:**
- Real-time progress tracking via todos
- Output from each agent invocation
- Integrated final deliverable
- Performance metrics and success validation

**Learning Documentation:**
- New patterns discovered during execution
- Optimizations for future similar tasks
- Problems encountered and solutions applied
- Stored in Mem0 for future reference

## Advanced Orchestration Capabilities

**Parallel Execution:**
- Identify independent subtasks for concurrent processing
- Manage parallel agent invocations efficiently
- Synchronize results at convergence points

**Conditional Branching:**
- Adapt execution based on intermediate results
- Choose alternative paths based on conditions
- Implement if-then-else logic in orchestration

**Iterative Refinement:**
- Loop through agents for progressive improvement
- Validate and refine outputs iteratively
- Converge on optimal solution through multiple passes

**Error Recovery:**
- Detect failures and trigger recovery procedures
- Retry with modified parameters
- Escalate to alternative agents when needed
- Maintain task progress despite partial failures

## Usage Examples

```bash
/analyze-task "Build a full-stack web application with user authentication"
/analyze-task "Research and summarize latest AI developments in healthcare"
/analyze-task "Automate daily report generation from multiple data sources"
/analyze-task "Create comprehensive test suite for existing codebase"
```

## Permission Chain Demonstration

This command demonstrates comprehensive multi-agent orchestration:
**Slash Command → TodoWrite (Progress Tracking) → Mem0 MCP (Context Gathering)**
                **→ Task Tool → Task Orchestrator Agent → Agent Analysis**
                **→ Dynamic Agent Selection → Parallel/Sequential Execution**
                **→ Results Integration → Mem0 MCP (Learning Storage)**

This slash command provides intelligent task analysis and optimal orchestration strategy, ensuring any complex task is broken down, assigned to the right specialists, and executed efficiently with full progress visibility and continuous learning.