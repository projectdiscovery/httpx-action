<h1 align="center">
  <img src="https://github.com/projectdiscovery/httpx/blob/master/static/httpx-logo.png" alt="httpx" width="200px"></a>
  <br>
</h1>

<h4 align="center"><a href="https://github.com/projectdiscovery/httpx-action">httpx Action</a> makes it easy to orchestrate <a href="https://github.com/projectdiscovery/httpx">httpx</a> with GitHub Action.</h4>



Example Usage
-----

**GitHub Action running httpx on list of hosts**

```yaml
      - name: 💥 httpx - HTTP Web Server probing
        uses: projectdiscovery/httpx-action@main
        with:
          list: hosts.txt
```

**Example workflow** - `.github/workflows/httpx.yml`


```yaml
name: 💥 httpx - HTTP Web Server probing

on:
    schedule:
      - cron: '0 0 * * *'
    workflow_dispatch:

jobs:
  httpx-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-go@v2
        with:
          go-version: 1.15

      - name: 💥 httpx - HTTP Web Server probing
        uses: projectdiscovery/httpx-action@main
        with:
          list: hosts.txt

      - name: GitHub Workflow artifacts
        uses: actions/upload-artifact@v2
        with:
          name: httpx.log
          path: httpx.log
```


Available Inputs
------

| Key      | Description                                          | Required |
| -------- | ---------------------------------------------------- | -------- |
| `list`   | List of hosts to run HTTP/S Web server probbing      | false    |
| `output` | File to save output result (default - httpx.log)     | false    |
| `json`   | Write results in JSON format                         | false    |
| `flags`  | Additional httpx CLI flags to use                    | false    |
