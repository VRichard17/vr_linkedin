# Self-Learning Framework with Mem0

## Overview
This framework enables agents and commands to learn from experience, identify patterns, and apply solutions to future problems. All learning is persisted in Mem0 for continuous improvement.

## Core Learning Cycle

### 1. Problem Detection & Solution Search
Before attempting any risky operation:
```javascript
// Search for known solutions
const problemContext = "error description or operation type";
const solutions = await mcp__mem0__mem0_search(`solution: ${problemContext}`);
const patterns = await mcp__mem0__mem0_search(`pattern: ${problemContext}`);

// Apply known solutions if found
if (solutions.length > 0) {
  // Apply the solution pattern
  console.log("Applying known solution:", solutions[0]);
}
```

### 2. Execution Monitoring
Track all operations for learning opportunities:
```javascript
const operation = {
  type: "form_filling|navigation|authentication|etc",
  context: "detailed context",
  startTime: Date.now(),
  attempts: [],
  errors: [],
  successful: false
};

// Record each attempt
operation.attempts.push({
  method: "approach description",
  result: "success|failure",
  errorDetails: errorMessage
});
```

### 3. Post-Mortem Analysis
After completing any significant task:

#### A. Problem Identification
```javascript
const problems = [];
if (operation.errors.length > 0) {
  problems.push({
    category: "error_type",
    description: "what went wrong",
    context: "when/where it happened",
    impact: "high|medium|low"
  });
}
```

#### B. Solution Extraction
```javascript
const solutions = [];
if (operation.successful) {
  solutions.push({
    problem: "problem it solved",
    approach: "how it was solved",
    steps: ["step1", "step2"],
    confidence: 0.95
  });
}
```

#### C. Pattern Recognition
```javascript
const patterns = {
  trigger: "what situations trigger this problem",
  symptoms: ["symptom1", "symptom2"],
  solution_pattern: "generalized solution approach",
  variations: ["variation1", "variation2"],
  success_rate: "percentage"
};
```

#### D. Memory Storage
```javascript
// Store problems for future reference
await mcp__mem0__mem0_add(
  content: `PROBLEM: ${problem.description}. CONTEXT: ${problem.context}. CATEGORY: ${problem.category}`,
  tags: ["problem", problem.category, "learned"]
);

// Store solutions
await mcp__mem0__mem0_add(
  content: `SOLUTION for "${problem.description}": ${solution.approach}. Steps: ${solution.steps.join(", ")}`,
  tags: ["solution", problem.category, "proven", `confidence:${solution.confidence}`]
);

// Store patterns
await mcp__mem0__mem0_add(
  content: `PATTERN: When ${patterns.trigger}, symptoms include ${patterns.symptoms.join(", ")}. Solution: ${patterns.solution_pattern}`,
  tags: ["pattern", "behavioral", problem.category]
);
```

## Problem Categories & Solutions

### Authentication Problems
```javascript
{
  category: "authentication",
  patterns: [
    {
      problem: "Session expired",
      symptoms: ["redirect to login", "401 errors"],
      solution: "Re-authenticate using stored credentials"
    },
    {
      problem: "CAPTCHA challenge",
      symptoms: ["captcha element present"],
      solution: "Slow down actions, add human-like delays"
    }
  ]
}
```

### Form Filling Problems
```javascript
{
  category: "form_filling",
  patterns: [
    {
      problem: "Field not found",
      symptoms: ["selector returns null"],
      solution: "Use semantic search, look for labels"
    },
    {
      problem: "Validation error",
      symptoms: ["error message appears"],
      solution: "Read error text, adjust input format"
    }
  ]
}
```

### Navigation Problems
```javascript
{
  category: "navigation",
  patterns: [
    {
      problem: "Page not loading",
      symptoms: ["timeout", "network error"],
      solution: "Retry with longer timeout, check connection"
    },
    {
      problem: "Dynamic content",
      symptoms: ["element not immediately visible"],
      solution: "Wait for specific elements, use lazy loading patterns"
    }
  ]
}
```

## Implementation Template

### For Agents
```markdown
## Learning & Problem Solving
This agent implements self-learning through post-mortem analysis:

1. **Before Operations**: Search Mem0 for known problems and solutions
2. **During Operations**: Track attempts, errors, and successes
3. **After Operations**: Analyze outcomes, extract patterns, store learnings

### Problem Resolution Process
When encountering an error:
1. Search: `mcp__mem0__mem0_search("solution: [error description]")`
2. Apply known solutions if found
3. If no solution exists, try alternative approaches
4. Document what worked for future reference

### Post-Mortem Analysis
After completing tasks:
1. Identify all problems encountered
2. Document successful solutions
3. Extract reusable patterns
4. Store in Mem0 with appropriate tags
```

### For Commands
```markdown
## Self-Learning Capabilities
This command learns from each execution:

1. **Pre-execution**: Query Mem0 for relevant patterns and known issues
2. **Execution**: Monitor and log all operations
3. **Post-execution**: Analyze results and update knowledge base

### Continuous Improvement
- Tracks success rates for different approaches
- Identifies recurring problems
- Builds solution library over time
- Shares learnings across all agents
```

## Memory Query Patterns

### Finding Solutions
```javascript
// Specific error solutions
mcp__mem0__mem0_search("solution: timeout error LinkedIn")

// General patterns
mcp__mem0__mem0_search("pattern: form validation")

// Category-based
mcp__mem0__mem0_search("authentication problems")
```

### Storing Learnings
```javascript
// Problem documentation
mcp__mem0__mem0_add(
  content: "PROBLEM: LinkedIn rate limiting detected after 50 rapid requests",
  tags: ["problem", "rate-limit", "linkedin"]
);

// Solution documentation
mcp__mem0__mem0_add(
  content: "SOLUTION: Add 2-3 second delays between LinkedIn requests to avoid rate limiting",
  tags: ["solution", "rate-limit", "linkedin", "proven"]
);

// Pattern documentation
mcp__mem0__mem0_add(
  content: "PATTERN: LinkedIn implements rate limiting. Symptoms: 429 errors, slow responses. Solution: Implement exponential backoff with base delay of 2 seconds",
  tags: ["pattern", "linkedin", "rate-limit", "behavioral"]
);
```

## Success Metrics

Track improvement over time:
```javascript
const metrics = {
  total_problems_encountered: 0,
  problems_solved_with_memory: 0,
  new_patterns_discovered: 0,
  success_rate_improvement: 0,
  average_time_to_resolution: 0
};

// Store metrics periodically
mcp__mem0__mem0_add(
  content: `METRICS: Success rate: ${metrics.success_rate_improvement}%, Problems solved from memory: ${metrics.problems_solved_with_memory}`,
  tags: ["metrics", "learning", "improvement"]
);
```

## Best Practices

1. **Be Specific**: Store detailed problem descriptions and contexts
2. **Tag Consistently**: Use standardized tags for easy retrieval
3. **Update Confidence**: Adjust solution confidence based on success rates
4. **Share Learnings**: Patterns discovered by one agent benefit all
5. **Prune Outdated**: Mark obsolete solutions when UI changes
6. **Version Awareness**: Include timestamps and versions in patterns