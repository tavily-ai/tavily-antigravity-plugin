# Tavily for Antigravity and Gemini CLI

Give Google Antigravity and Gemini CLI live web access through Tavily. Your agent can search the web, read any
page, map a site and crawl its pages while it works, so answers come from current documentation, changelogs,
issues and news instead of training data.

## Install

**Antigravity CLI**

```bash
agy plugin install https://github.com/tavily-ai/tavily-antigravity-plugin
```

**Antigravity app**

Open **Customizations** in the left sidebar, then **Marketplace**, find **Tavily** and select **+**. Installed
plugins sync to the Antigravity CLI.

**Gemini CLI**

```bash
gemini extensions install https://github.com/tavily-ai/tavily-antigravity-plugin
```

The plugin identifier is `tavily`; its MCP server is named `tavily`.

## Sign in

The plugin connects to Tavily's hosted MCP server at `https://mcp.tavily.com/mcp`, which uses OAuth. There is no
API key to paste.

- **Antigravity CLI:** run `/mcp`, select the `tavily` server and choose **Authenticate**. Complete the browser
  sign-in and paste the authorization code back into the terminal.
- **Antigravity app:** open **Customizations → Installed → Tavily** and sign in.
- **Gemini CLI:** start a session and Gemini CLI opens a browser window for the Tavily sign-in. Run
  `/mcp auth tavily` to sign in again.

Don't have an account? Sign up at [app.tavily.com](https://app.tavily.com); new accounts include free monthly
credits.

## Try it

From inside your project:

```text
Find the current migration guide for this project's main framework and list what we'd need to change.
```

- "Search the docs and GitHub issues for this error and suggest a fix with sources."
- "Map docs.example.com and find the page on API authentication."
- "Crawl the changelog section of this library's docs and summarize breaking changes since v3."

## What the plugin includes

| Component | What it does |
| --- | --- |
| `tavily_search` | Searches the web and returns the most relevant passages from each result. |
| `tavily_extract` | Reads clean markdown from up to 20 URLs, including pages built with JavaScript. |
| `tavily_map` | Lists the URLs on a site so the agent can find the right page. |
| `tavily_crawl` | Follows links from a URL and returns the content of the pages it reaches. |
| `tavily-search` skill | Guides the agent on writing queries, reading pages, mapping and crawling. Invoke it with `/tavily-search`. |
| `tavily-research` skill | Researches a topic in depth and writes a cited report. |
| `tavily-entity` skill | Fills in a company, person or organization for a CRM, including a CSV of existing rows. |
| `tavily-list` skill | Builds a deduplicated table of matches for a set. |
| `tavily-monitor` skill | Sets up a recurring search or page check with a saved baseline. |
| `tavily-sdk` skill | Reference for building Tavily into your own code with the Python and JavaScript SDKs. |
| Rule | Reminds the agent to use Tavily when a task depends on information outside the repository. |

## Data and security

The bundled MCP configuration connects to `https://mcp.tavily.com` over HTTPS. Search queries and requested URLs
are sent to Tavily, along with your OAuth token and an `X-Client-Name` header that identifies the plugin's
traffic. The plugin includes no local executables; its skills and rule are instructions read by the client.
If the MCP tools aren't available, the skills fall back to the [Tavily CLI](https://github.com/tavily-ai/tavily-cli)
(`tvly`) when it is installed. See the [privacy policy](https://www.tavily.com/privacy).

## Uninstall

```bash
agy plugin uninstall tavily
gemini extensions uninstall tavily
```

## Resources

- [Tavily MCP documentation](https://docs.tavily.com/documentation/mcp)
- [Tavily API reference](https://docs.tavily.com/documentation/api-reference/endpoint/search)
- [Tavily MCP server source](https://github.com/tavily-ai/tavily-mcp)
- [Tavily agent skills](https://github.com/tavily-ai/skills)
- Support: [support@tavily.com](mailto:support@tavily.com)

## License

MIT
