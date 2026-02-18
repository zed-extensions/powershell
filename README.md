# PowerShell support for Zed

This extension provides syntax highlighting as well as language server support for PowerShell files

## Configuring your language server

The extension requires PowerShell to be available in your environment. If that is the case,
the extension will auto-download the language server and start it.

If you wish to specify a custom path to your language server, you can do so via your settings:

```json
{
    "lsp": {
        "powershell-es": {
            "binary": {
                "path": "<path to PowerShellEditorServices>"
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
