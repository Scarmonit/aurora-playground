# aurora-playground
Sandbox repo for experiments and demos

## MCP Server Suite

This repository is configured with a comprehensive suite of MCP (Model Context Protocol) servers that enable Claude Code to interact with various systems.

### Configured Servers

| Server | Description | Key Capabilities |
|--------|-------------|------------------|
| **GitHub** | GitHub API integration | Repos, issues, PRs, branches, search |
| **Git** | Local git operations | Commits, diffs, logs, blame, branches |
| **Filesystem** | File system access | Read, write, search, directory ops |
| **Fetch** | Web content retrieval | HTTP requests, HTML-to-markdown |
| **Memory** | Persistent memory | Knowledge graph, entity storage |

### Quick Setup

1. **Authenticate with GitHub** (one-time):
   ```bash
   gh auth login
   ```

2. **Start Claude Code** in this directory - MCP servers auto-configure.

### GitHub Server Capabilities

- **Repository Management**: Create, fork, clone, delete repos
- **Issues**: Create, update, close, comment, label
- **Pull Requests**: Create, review, merge, request changes
- **Branches**: Create, delete, protect, compare
- **Files**: Read, create, update, delete via API
- **Search**: Code, issues, repos, users, commits
- **Releases**: Create, edit, publish releases
- **Actions**: View workflow runs and statuses

### Git Server Capabilities

- **History**: View commits, logs, blame
- **Diffs**: Compare branches, commits, files
- **Branches**: List, create, checkout
- **Status**: Working tree status, staged changes

### Filesystem Server Capabilities

- **Read**: File contents, directory listings
- **Write**: Create and modify files
- **Search**: Find files by pattern
- **Info**: File metadata, permissions

### Fetch Server Capabilities

- **HTTP**: GET/POST requests to URLs
- **Parse**: Convert HTML to markdown
- **Extract**: Pull content from web pages

### Memory Server Capabilities

- **Entities**: Store and retrieve named entities
- **Relations**: Create connections between entities
- **Search**: Query the knowledge graph
- **Persist**: Long-term memory across sessions

## Configuration

MCP servers are configured in `.mcp.json`:

```json
{
  "mcpServers": {
    "github": { "command": "sh", "args": ["-c", "GITHUB_PERSONAL_ACCESS_TOKEN=$(gh auth token) npx -y @modelcontextprotocol/server-github"] },
    "git": { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-git"] },
    "filesystem": { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-filesystem", "/home/user/aurora-playground"] },
    "fetch": { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-fetch"] },
    "memory": { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-memory"] }
  }
}
```

## Usage Examples

Once configured, ask Claude Code to:

### GitHub Operations
- "Create an issue titled 'Bug: login fails'"
- "List all open pull requests"
- "Create a new branch called 'feature/auth'"
- "Search for files containing 'authentication'"

### Git Operations
- "Show the last 10 commits"
- "What changed in the last commit?"
- "Show git blame for README.md"

### File Operations
- "List all TypeScript files"
- "Read the package.json file"
- "Search for TODO comments"

### Web Operations
- "Fetch the content from https://example.com"
- "Get the latest docs from the API"

### Memory Operations
- "Remember that the API key is stored in .env"
- "What do you know about this project?"

## License

MIT License - see [LICENSE](LICENSE) for details.
