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
				"path": "pwsh.exe",
				"arguments": [
					"-NoLogo",
					"-NoProfile",
					"-Command",
					"path\\to\\PowerShellEditorServices\\Start-EditorServices.ps1",
					"-Stdio",
					"-SessionDetailsPath",
					"path\\to\\PowerShellEditorServices\\powershell-es.session.json",
				],
			},
		},
    }
}
```

## Running PowerShell code

This extension provides task templates for running PowerShell code:

- **PowerShell: Run Selection** — runs the currently selected text
- **PowerShell: Run File** — runs the current file

These tasks are available via the `task: spawn` action.

To bind `F8` for running selected text (like PowerShell ISE and VS Code), add the following to your `keymap.json`:

```json
{
  "context": "Editor && extension == powershell",
  "bindings": {
    "f8": ["task::Spawn", { "task_name": "PowerShell: Run Selection" }]
  }
}
```

## Configuring your language server settings

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
