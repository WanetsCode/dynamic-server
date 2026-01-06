[![wanetscode/dynamic-server - GitHub](https://gh-card.dev/repos/wanetscode/dynamic-server.svg)](https://github.com/wanetscode/dynamic-server)

[![Version](https://img.shields.io/badge/Version%20number:-v1-red.svg)](https://wnts.pages.dev)


[![AGPL License](https://img.shields.io/badge/Licensed-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)

# Dynamic Server v1.0

The easiest way to host a temporary or permanent server on any device and network with file editing, API request handling and read requests with no need of advanced server knowledge



## Deployment

1. Download the server CLI

```bash
  curl wnts.pages.dev/install.ps1
```

2. Pick any directory to host

```bash
  cd C:/Path/To/My/Dir
```

3. Host it privately or publicly with a custom port


Local:
```bash
  dynser start
```
Public:
```bash
  dynser start --public [nameserver]
```
Custom Port:
```bash
  dynser start --port [portid]
```

## API Reference

#### Read file data

```http
  http://localhost:8000/api/read?[directory]
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `directory` | `URL` | Example: for http://localhost:8000/edit/test/ab.txt is http://localhost:8000/api/read?test/ab.txt|

Result: Plain text


#### Read file data

```http
  http://localhost:8000/api/metadata?[directory]
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `directory` | `URL` | Example: for http://localhost:8000/edit/test/ab.txt is http://localhost:8000/api/metadata?test/ab.txt|

Result: Json

Example Result: `{"name": "ab.txt", "size": 2, "size_formatted": "2.0 B", "modified": "2025-12-12 20:13:36", "created": "2025-12-10 18:57:14", "type": ".txt"}`




:Note to self- finish API docs


## Authors

- [@wanetscode](https://www.github.com/wanetscode)
- [@repostudio](https://www.github.com/repostudio)


## FAQ

#### Is it free?

Yes completely free, because it runs on your machine only.

#### How to get 24/7 servers?

To keep your server open permanently make sure that the device it is being run on is onstantly ON and the script reruns incase of sudden power loss


## Feedback

If you have any feedback, found any bugs or have a suggestion please make an issue

##
[![MIT License](https://img.shields.io/badge/Powered%20by-Dynamic%20Server-red.svg)](https://wnts.pages.dev)

[![GPLv3 License](https://img.shields.io/badge/Public%20host%20status-Working-green.svg)](https://wnts.pages.dev/host)

[![AGPL License](https://img.shields.io/badge/Licensed-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)


## Sponsors

[Support dynamic server and it's development](https://thanks.dev/u/gh/wanetscode) and get your name/company written down here
