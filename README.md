# aurora-playground
Sandbox repo for experiments and demos

## GitHub MCP Server Setup

This repository is configured with a GitHub MCP (Model Context Protocol) server that enables Claude Code to interact with GitHub directly.

### Features

The GitHub MCP server provides the following capabilities:

- **Repository Management**: Create, fork, and manage repositories
- **Issues**: Create, read, update, and comment on issues
- **Pull Requests**: Create, review, merge, and manage pull requests
- **Branches**: Create and manage branches
- **Files**: Read, create, update, and delete files in repositories
- **Search**: Search for code, issues, repositories, and users
- **Commits**: View commit history and details
- **Releases**: Create and manage releases
- **Actions**: View workflow runs and statuses

### Quick Setup

1. **Create a GitHub Personal Access Token**:
   - Go to [GitHub Settings > Tokens](https://github.com/settings/tokens)
   - Click "Generate new token (classic)"
   - Select these scopes:
     - `repo` - Full control of private repositories
     - `read:org` - Read org and team membership
     - `gist` - Create gists
     - `read:user` - Read user profile data
     - `read:project` - Read project boards
   - Click "Generate token" and copy it

2. **Configure the token**:
   ```bash
   # Copy the example env file
   cp .env.example .env

   # Edit .env and add your token
   # GITHUB_PERSONAL_ACCESS_TOKEN=ghp_your_token_here
   ```

3. **Start Claude Code** with the environment variable:
   ```bash
   # Option 1: Load from .env file
   source .env && claude

   # Option 2: Set directly
   GITHUB_PERSONAL_ACCESS_TOKEN=ghp_your_token claude
   ```

### MCP Configuration

The MCP server is configured in `.mcp.json`:

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_PERSONAL_ACCESS_TOKEN}"
      }
    }
  }
}
```

### Usage Examples

Once configured, you can ask Claude Code to:

- "Create a new issue in this repository"
- "List all open pull requests"
- "Search for files containing 'authentication'"
- "Create a new branch called 'feature/new-feature'"
- "Review the latest pull request"
- "Fork this repository"
- "Create a release v1.0.0"

## License

MIT License - see [LICENSE](LICENSE) for details.
