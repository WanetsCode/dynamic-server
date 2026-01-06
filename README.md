# Dynamic Server v1.0

[![View dynamic-server on GitHub](https://img.shields.io/github/stars/wanetscode/dynamic-server?color=232323&label=dynamic-server&logo=github&labelColor=232323)](https://github.com/wanetscode/dynamic-server) [![Author wanetscode](https://img.shields.io/badge/wanetscode-b820f9?labelColor=b820f9&logo=githubsponsors&logoColor=fff)](https://github.com/wanetscode) 
[![License](https://img.shields.io/badge/License-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)

The easiest way to host a temporary or permanent server on any device and network. Edit files, handle API requests, and serve content—no advanced server knowledge required.

## Deployment

1. **Download the server CLI**

```bash
curl wnts.pages.dev/install.ps1
```

2. **Choose a directory to host**

```bash
cd C:/Path/To/My/Dir
```

3. **Host it locally, publicly, or on a custom port**

**Local (default port 8000):**
```bash
dynser start
```

**Public (requires nameserver):**
```bash
dynser start --public [nameserver]
```

**Custom Port:**
```bash
dynser start --port [portid]
```

## API Reference

### Read file data

```http
GET http://localhost:8000/api/read?path=[filepath]
```

| Parameter | Type | Description |
| :-------- | :------- | :------------------------- |
| `filepath` | `string` | File path relative to server root. Example: `test/ab.txt` |

**Result**: File contents (HTML files, images, and JSON may be previewed instead of downloaded depending on browser. Append `view-source:` prefix to view raw content: `view-source:http://localhost:8000/api/read?test/ab.txt`)

### Read file metadata

```http
GET http://localhost:8000/api/metadata?path=[filepath]
```

| Parameter | Type | Description |
| :-------- | :------- | :------------------------- |
| `filepath` | `string` | File path relative to server root. Example: `test/ab.txt` |

**Result**: JSON object

**Example Response:**
```json
{
  "name": "ab.txt",
  "size": 2,
  "size_formatted": "2.0 B",
  "modified": "2025-12-12 20:13:36",
  "created": "2025-12-10 18:57:14",
  "type": ".txt"
}
```

### Create new file

```http
POST http://localhost:8000/api/create?path=[directory]&filename=[filename]
```

| Parameter | Type | Description |
| :-------- | :------- | :------------------------- |
| `directory` | `string` | Folder path relative to root. Example: `test` |
| `filename` | `string` | Name of file to create. Example: `ab.txt` |

**Result**: File created (no response body)

**Example Request:**
```bash
curl -X POST "http://localhost:8000/api/create?path=test&filename=ab.txt"
```

### Edit file

```http
POST http://localhost:8000/api/save?path=[filepath]
```

| Parameter | Type | Description |
| :-------- | :------- | :------------------------- |
| `filepath` | `string` | File path relative to server root. Example: `test/ab.txt` |

**Request Body**: New file content as plain text.

**Result**: `"OK"` (File saved successfully)

**Example Request:**
```bash
curl -X POST \
  "http://localhost:8000/api/save?path=test/ab.txt" \
  -H "Content-Type: text/plain" \
  -d "This is the new content of the file"
```

**Alternative Method**: Use the web interface at `http://localhost:8000/edit/[filepath]` (e.g., `http://localhost:8000/edit/test/ab.txt`).

### Clear logs

```http
POST http://localhost:8000/api/logs/clear
```

**Result**: Logs cleared (no response body)

### Get logs

```http
GET http://localhost:8000/api/logs
```

**Result**: JSON object containing recent log entries

### Get history

```http
GET http://localhost:8000/api/history
```

**Result**: JSON array of recent file changes (last 5 actions)

### List files in directory

```http
GET http://localhost:8000/api/list?path=[directory]
```

| Parameter | Type | Description |
| :-------- | :------- | :------------------------- |
| `directory` | `string` | Folder path relative to root. Example: `test` |

**Result**: JSON array of file/directory objects

**Example Response:**
```json
[
  {
    "name": "directory",
    "path": "test\\directory",
    "is_dir": true,
    "modified": 1765388921
  },
  {
    "name": "yipee.txt",
    "path": "test\\ab.txt",
    "is_dir": false,
    "modified": 1765563216
  }
]
```

## Authors

- **Written by**: [@WanetsCode](https://www.github.com/wanetscode)
- **Contributions & commit management**: [@RepoStudio](https://www.github.com/repostudio)
- **Written in**: [@Python](https://github.com/python)

## FAQ

#### Is Dynamic Server free?
Yes, completely free. The server runs on your machine, so there are no hosting fees.

#### How do I get 24/7 server uptime?
To keep your server running permanently:
- Ensure the device stays powered on
- Set up automatic script restart in case of power loss or crashes
- Consider using process managers like `pm2` (Node.js) or supervisor daemons

#### Can I host this on a VPS or cloud server?
Yes! Dynamic Server works on any device with Python, including cloud VPS instances, Raspberry Pi, or old computers.

#### Is it secure for public hosting?
While suitable for development and personal use, consider adding authentication and HTTPS for sensitive data in production environments.

## Feedback

Found a bug? Have a suggestion? Please [create an issue](https://github.com/wanetscode/dynamic-server/issues) on GitHub.

## Sponsors

Support Dynamic Server development and get your name featured here!

[![Sponsor](https://img.shields.io/badge/Sponsor-Thanks.dev-orange.svg)](https://thanks.dev/u/gh/wanetscode)

