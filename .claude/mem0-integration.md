# Mem0 Memory Bank Integration

## Memory System
This agent/command uses Mem0 as its persistent memory system. Use the following MCP functions to interact with the memory bank:

### Available Memory Functions
- `mcp__mem0__mem0_add`: Add new memories with optional tags
- `mcp__mem0__mem0_search`: Search memories by query
- `mcp__mem0__mem0_list`: List all memories
- `mcp__mem0__mem0_delete`: Delete a specific memory by ID

### Memory Usage Guidelines

1. **Before Starting Any Task**:
   - Search Mem0 for relevant context using `mcp__mem0__mem0_search`
   - Common searches: user credentials, file locations, preferences, past interactions

2. **During Task Execution**:
   - Store important discoveries and learnings using `mcp__mem0__mem0_add`
   - Tag memories appropriately for easy retrieval

3. **Memory Categories to Track**:
   - User information (name, preferences, etc.)
   - File locations (resumes, credentials, etc.)
   - Job search criteria and preferences
   - Application history and results
   - System configurations and settings
   - Task outcomes and learnings

4. **Example Memory Operations**:
```
# Search for user's resume location
mcp__mem0__mem0_search("resume location")

# Add a new memory about job preferences
mcp__mem0__mem0_add(
  content="User prefers remote AI/ML engineering positions",
  tags=["preferences", "job-search", "remote"]
)

# List all memories to understand context
mcp__mem0__mem0_list()
```

5. **Memory Best Practices**:
   - Keep memories atomic and specific
   - Use descriptive tags for categorization
   - Update memories when information changes
   - Check for existing memories before adding duplicates