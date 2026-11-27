# Windows PowerShell Snippet Safety

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/windows_powershell_snippet_safety


## Assume Windows PowerShell 5.1

- Assume the user runs Windows PowerShell 5.1 unless the user states a newer shell.

- Treat any API that exists only in PowerShell 7 or .NET Core as unavailable until you check it against Windows PowerShell 5.1.

- State the shell you checked the snippet against when you send it, and state that it is untested when you could not check it in that shell.

## Check APIs and syntax before sending

- Check every .NET method name in a snippet against Windows PowerShell 5.1 before sending the snippet.

- Replace a .NET Core only method with a form that Windows PowerShell 5.1 supports, and verify the replacement before relying on it.

- Wrap a pipeline that feeds Get-Random in parentheses before you index or join its result, since an unwrapped pipeline produces a parser error.

- Read the finished snippet once for a missing parenthesis, a missing method, and a silent fallback that would produce a repeated or weak value.

## Quote dollar signs safely

- Use single quotes for any literal string that contains a dollar sign, since double quotes expand the dollar segment in PowerShell.

- Prefer changing a password in the web interface over passing a password containing a dollar sign through a shell command.

- Test a password snippet with a harmless literal first when the real password contains a dollar sign, and confirm the stored value matches before treating the change as done.

## Present snippets honestly

- Send a snippet the user must copy as its own message, separate from explanation, so the user copies only the snippet.

- Tell the user at once when a snippet you sent fails, concede the failure plainly, and send only a corrected snippet that you checked against Windows PowerShell 5.1.

- Ask the user to paste the error text back when a snippet fails, and use that error text to fix the exact line rather than guessing at a new snippet.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Offer a web interface route when a shell route adds quoting risk and the web interface achieves the same change.

- Offer a shorter snippet with fewer symbols when the user only needs one random value, since fewer symbols mean fewer quoting failures.
