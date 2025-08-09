# Copilot Instructions

<!-- Use this file to provide workspace-specific custom instructions to Copilot. For more details, visit https://code.visualstudio.com/docs/copilot/copilot-customization#_use-a-githubcopilotinstructionsmd-file -->

This is an MCP (Model Context Protocol) server project for querying PostgreSQL databases.

## Project Context
- This is a TypeScript-based MCP server that provides tools for database operations
- Uses the @modelcontextprotocol/sdk for MCP functionality
- Uses pg library for PostgreSQL connections
- Implements secure database querying with proper error handling
- Follows MCP protocol specifications

## Key Components
- Database connection management with connection pooling
- SQL query execution tools with parameterized queries
- Schema introspection capabilities
- Proper error handling and logging
- Environment-based configuration

## References
- MCP SDK: https://github.com/modelcontextprotocol/create-python-server
- You can find more info and examples at https://modelcontextprotocol.io/llms-full.txt
- PostgreSQL documentation: https://www.postgresql.org/docs/

## Best Practices
- Always use parameterized queries to prevent SQL injection
- Implement proper connection pooling
- Handle database errors gracefully
- Validate input parameters using Zod schemas
- Follow TypeScript best practices for type safety
