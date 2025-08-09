# PostgreSQL MCP Server

A Model Context Protocol (MCP) server for querying PostgreSQL databases. This server provides tools to execute SQL queries, explore database schemas, and retrieve table data safely.

## Features

- **Database Querying**: Execute SELECT queries with parameterized statements
- **Schema Exploration**: List tables, describe table structures, and view constraints
- **Data Sampling**: Retrieve sample data from tables with configurable limits
- **Security**: Built-in protection against dangerous SQL operations
- **Connection Pooling**: Efficient PostgreSQL connection management
- **Type Safety**: Full TypeScript implementation with Zod validation

## Tools Available

### 1. query_database
Execute SQL queries against the PostgreSQL database.
- **Input**: SQL query string and optional parameters
- **Security**: Only SELECT queries are allowed by default
- **Output**: Query results with row count and field metadata

### 2. list_tables
List all tables in a specific schema.
- **Input**: Schema name (defaults to 'public')
- **Output**: List of tables with their types

### 3. describe_table
Get detailed information about a table's structure.
- **Input**: Table name and schema (defaults to 'public')
- **Output**: Column definitions, data types, constraints, and relationships

### 4. get_table_data
Retrieve sample data from a table.
- **Input**: Table name, schema, and limit (defaults to 10 rows)
- **Output**: Sample data with row count

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd postgres-mcp-server
```

2. Install dependencies:
```bash
npm install
```

3. Create environment configuration:
```bash
cp .env.example .env
```

4. Configure your PostgreSQL connection in `.env`:
```env
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
POSTGRES_DATABASE=your_database
POSTGRES_USER=your_username
POSTGRES_PASSWORD=your_password
```

## Usage

### Development Mode
```bash
npm run dev
```

### Production Mode
```bash
npm run build
npm start
```

### Watch Mode (for development)
```bash
npm run watch
```

## Configuration

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `POSTGRES_HOST` | PostgreSQL server host | `localhost` |
| `POSTGRES_PORT` | PostgreSQL server port | `5432` |
| `POSTGRES_DATABASE` | Database name | `postgres` |
| `POSTGRES_USER` | Database username | `postgres` |
| `POSTGRES_PASSWORD` | Database password | `` |
| `POSTGRES_MAX_CONNECTIONS` | Maximum connections in pool | `10` |
| `POSTGRES_IDLE_TIMEOUT` | Idle connection timeout (ms) | `30000` |
| `POSTGRES_CONNECTION_TIMEOUT` | Connection timeout (ms) | `10000` |

### MCP Client Configuration

To use this server with an MCP client, add the following configuration:

```json
{
  "servers": {
    "postgres-mcp-server": {
      "type": "stdio",
      "command": "node",
      "args": ["dist/index.js"]
    }
  }
}
```

## Security Features

- **SQL Injection Protection**: Uses parameterized queries
- **Query Restrictions**: Only SELECT statements allowed by default
- **Input Validation**: All inputs validated using Zod schemas
- **Connection Security**: Secure connection pooling with timeouts

## Project Structure

```
├── src/
│   └── index.ts          # Main MCP server implementation
├── .vscode/
│   ├── mcp.json          # MCP configuration
│   └── tasks.json        # VS Code tasks
├── .github/
│   └── copilot-instructions.md
├── .env.example          # Environment template
├── package.json
├── tsconfig.json
└── README.md
```

## Development

### Prerequisites
- Node.js 18+
- PostgreSQL database
- TypeScript knowledge

### Building
```bash
npm run build
```

### Type Checking
```bash
npm run typecheck
```

### Cleaning Build Artifacts
```bash
npm run clean
```

## Example Usage

Once the server is running, you can use it with any MCP-compatible client to:

1. **Query your database**:
   ```sql
   SELECT * FROM users WHERE created_at > '2024-01-01'
   ```

2. **Explore your schema**:
   - List all tables in the public schema
   - Get detailed information about table structures
   - View sample data from any table

3. **Analyze your data**:
   - Execute complex analytical queries
   - Join multiple tables
   - Aggregate data with GROUP BY and window functions

## Troubleshooting

### Connection Issues
- Verify PostgreSQL is running and accessible
- Check connection parameters in `.env`
- Ensure database user has necessary permissions

### Permission Errors
- Grant SELECT permissions to the database user
- For schema exploration, ensure access to `information_schema`

### Performance Issues
- Adjust connection pool settings
- Consider adding query timeouts for long-running queries
- Monitor database performance

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

MIT License - see LICENSE file for details

## References

- [Model Context Protocol](https://modelcontextprotocol.io/)
- [MCP SDK Documentation](https://github.com/modelcontextprotocol/create-python-server)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
