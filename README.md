# GitHub Brain Raycast Extension

A Raycast extension for searching GitHub issues, pull requests, and discussions using the [GitHub Brain MCP server](https://github.com/wham/github-brain).

![GitHub Brain Raycast Extension](https://raw.githubusercontent.com/wham/github-brain/main/docs/raycast.png)

## Overview

This extension allows you to search your organization's GitHub data directly from Raycast. It connects to the GitHub Brain MCP server to provide fast, efficient searches across:

- Issues
- Pull requests
- Discussions

## Prerequisites

Before using this extension, you need to have the GitHub Brain server installed and configured:

1. **Install GitHub Brain:**
   ```bash
   npm i -g github-brain
   ```

2. **Authenticate with GitHub:**
   ```bash
   github-brain login
   ```

3. **Pull your organization's data:**
   ```bash
   github-brain pull -o your-organization-name
   ```

For detailed GitHub Brain setup instructions, see the [GitHub Brain documentation](https://github.com/wham/github-brain#installation).

## Installation

### Install from Raycast Store (Recommended)

Once published, you can install this extension directly from the Raycast Store.

### Install from Source

1. **Clone this repository:**
   ```bash
   git clone https://github.com/wham/github-brain-raycast.git
   cd github-brain-raycast
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Import the extension into Raycast:**
   ```bash
   npm run dev
   ```

## Configuration

After installing the extension, you need to configure it in Raycast preferences:

1. Open Raycast preferences (⌘+,)
2. Go to Extensions → GitHub Brain
3. Configure the following settings:

   - **GitHub Brain executable** (required): 
     - Default: `github-brain`
     - If installed globally with npm, use: `github-brain`
     - For a custom location, provide the absolute path to the binary

   - **Home directory** (optional):
     - Leave empty to use the default: `~/.github-brain`
     - Provide a custom path if you're using a different home directory

## Usage

1. Open Raycast (⌘+Space)
2. Type "GitHub Brain" or "Search"
3. Start typing your search query
4. The extension will display up to 10 matching results
5. Press Enter to open the item in your browser
6. Press ⌘+C to copy the URL to clipboard

### Search Results

Each result displays:
- An icon indicating the type and state (issue, pull request, or discussion)
- The title of the item (bold)
- The repository name (subtle text)

### Icon Legend

| Type         | State  | Icon         | Color  |
| ------------ | ------ | ------------ | ------ |
| Issue        | Open   | Circle       | Green  |
| Issue        | Closed | Circle       | Purple |
| Pull Request | Open   | Code         | Green  |
| Pull Request | Closed | Code         | Red    |
| Pull Request | Merged | CheckCircle  | Purple |
| Discussion   | Open   | SpeechBubble | Green  |

## Development

### Run in Development Mode

```bash
npm run dev
```

Or use the convenience script:

```bash
scripts/raycast
```

### Build

```bash
npm run build
```

### Lint

```bash
npm run lint
```

### Fix Linting Issues

```bash
npm run fix-lint
```

## Troubleshooting

### "GitHub Brain executable not found"

Make sure:
1. GitHub Brain is installed: `npm i -g github-brain`
2. The executable is in your PATH
3. The path in extension preferences is correct

### "MCP server exited with code"

This usually means:
1. GitHub Brain is not configured (run `github-brain login` and `github-brain pull`)
2. The home directory doesn't exist or doesn't contain data
3. The organization is not specified in the `.env` file

Check your GitHub Brain configuration:
```bash
cat ~/.github-brain/.env
```

It should contain:
```
GITHUB_TOKEN=your_token
ORGANIZATION=your-org
```

### No Search Results

1. Ensure you've run `github-brain pull` to populate the database
2. Check if your search query matches any items in your organization
3. Verify the GitHub Brain server is working: `github-brain mcp`

## Project Structure

```
.
├── src/
│   └── search.tsx          # Main extension code
├── scripts/
│   └── raycast             # Development launcher script
├── package.json            # Extension manifest and dependencies
├── tsconfig.json           # TypeScript configuration
├── raycast-env.d.ts        # Type definitions
└── README.md               # This file
```

## License

MIT

## Links

- [GitHub Brain](https://github.com/wham/github-brain) - The MCP server this extension connects to
- [Raycast](https://www.raycast.com/) - The productivity launcher
- [MCP Protocol](https://modelcontextprotocol.io/) - Model Context Protocol

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.