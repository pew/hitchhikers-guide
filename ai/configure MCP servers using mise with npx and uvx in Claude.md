# configure MCP servers using mise with npx and uvx (in Claude)

I'm using [mise](https://mise.jdx.dev) to manage my Node, Python, and Ruby (or whatever) installations and packages. When I wanted to configure an MCP server in Claude Desktop using npx or uvx, I always got errors like spawn uvx ENOENT. Thankfully, I [found this comment](https://github.com/modelcontextprotocol/servers/issues/64#issuecomment-2996989591) on how to fix that issue. You can use them like so (examples for the karakeep and markitdown MCP servers):

```json
{
  "mcpServers": {
    "karakeep": {
      "command": "mise",
      "args": [
        "exec",
        "node",
        "--",
        "npx",
        "-y",
        "@karakeep/mcp"
      ],
      "env": {
        "KARAKEEP_API_ADDR": "https://karakeep.example.com",
        "KARAKEEP_API_KEY": "foobar"
      }
    },
    "markitdown": {
      "command": "mise",
      "args": [
        "exec",
        "uv",
        "--",
        "uvx",
        "markitdown-mcp"
      ]
    }
  }
}
```

see also [mise exec](https://mise.jdx.dev/cli/exec.html)
