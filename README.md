# PowerShell support for Zed

This extension provides syntax highlighting as well as language server support for PowerShell files

## Configuring your language server

The extension requires PowerShell to be available in your environment. If that is the case,
the extension will auto-download the language server and start it.

The extension looks for `pwsh` (PowerShell Core / PowerShell 7+) in your `PATH` first.
If it is not found, it falls back to `powershell` (Windows PowerShell), which ships
with Windows. On systems where neither is available, or if you need to point to a
specific installation, you can specify a custom path in your settings:

```json
{
    "lsp": {
        "powershell-es": {
            "binary": {
                "path": "powershell.exe"
            }
        }
    }
}
```

The `binary.path` only needs to point to the PowerShell executable (e.g. `pwsh.exe` or
`powershell.exe`). The extension handles downloading and configuring PowerShell Editor
Services automatically. Full custom arguments are only needed if you want to manage the
Editor Services bundle yourself:

```json
{
    "lsp": {
        "powershell-es": {
            "binary": {
                "path": "pwsh.exe",
                "arguments": [
                    "-NoLogo",
                    "-NoProfile",
                    "-Command",
                    "path\\to\\PowerShellEditorServices\\Start-EditorServices.ps1",
                    "-Stdio",
                    "-SessionDetailsPath",
                    "path\\to\\PowerShellEditorServices\\powershell-es.session.json"
                ]
            }
        }
    }
}
```

Additionally, you can configure settings for your language server as well as initialization options
to pass to the language server on start.

An example for this:

```json
"lsp":{
   "powershell-es":{
      "settings":{
         "powershell":{
            "codeFormatting":{
               "openBraceOnSameLine":true,
               "addWhitespaceAroundPipe":true,
               "trimWhitespaceAroundPipe":true,
               "ignoreOneLineBlock":true
            }
         }
      }
   }
```
