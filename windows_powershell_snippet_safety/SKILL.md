# Windows PowerShell Snippet Safety

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/windows_powershell_snippet_safety

## When this applies
- Apply before sending the user any PowerShell command, snippet, or `.ps1` script to run on Windows.

## Assume Windows PowerShell 5.1
- Assume the user runs Windows PowerShell 5.1 (on .NET Framework 4.x) unless they say they use a newer shell.
- Treat any API or syntax that exists only in PowerShell 7 or .NET Core as unavailable until you have checked it against Windows PowerShell 5.1.
- When you send a snippet, name the shell you checked it against. If you could not check it in that shell, say it is untested.

## Avoid PowerShell 7-only features
- Never use `&&` or `||` between commands, the `? :` ternary, `??` or `??=`, `ForEach-Object -Parallel`, `ConvertFrom-Json -AsHashtable`, or `-Encoding utf8NoBOM`. None of these exist in 5.1.
- Never use .NET Core-only members such as `[System.Security.Cryptography.RandomNumberGenerator]::GetInt32`, `GetItems`, or `Fill`, or the `String.Split(char, options)` overloads. For random values in 5.1, use `New-Object System.Security.Cryptography.RNGCryptoServiceProvider` and `GetBytes`.
- Never use `Get-Random` for passwords or secrets, because it is not cryptographically secure.

## Check APIs and syntax before sending
- Check every .NET method name in a snippet against Windows PowerShell 5.1 before sending it.
- Replace any .NET Core-only method with a form that 5.1 supports, and verify the replacement before relying on it.
- Wrap a command or pipeline in parentheses before indexing it, accessing a member, or passing it to `-join`. For example, write `(Get-Random -InputObject $a -Count 3)[0]`. Without the parentheses, the index is parsed as an argument or causes a parser error.
- Read the finished snippet once for a missing parenthesis, a missing method, and a silent fallback that would produce a repeated or weak value.

## Handle encoding and the network
- In 5.1, `Out-File` and `>` write UTF-16LE, `Set-Content` writes ANSI, and `-Encoding UTF8` writes a BOM. Choose the encoding deliberately when another tool will read the file.
- Keep any `.ps1` you deliver ASCII-only, because 5.1 reads a UTF-8 file without a BOM as ANSI, which corrupts non-ASCII characters and can break parsing.
- Before calling `Invoke-WebRequest` or `Invoke-RestMethod` against a modern HTTPS endpoint, set `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`, and pass `-UseBasicParsing` to `Invoke-WebRequest`.

## Quote dollar signs safely
- Use single quotes for any literal string that contains a dollar sign, because double quotes expand the dollar segment.
- Prefer changing a password in the web interface to passing a password that contains a dollar sign through a shell command.
- When the real password contains a dollar sign, test the snippet with a harmless literal first, and confirm the stored value matches before treating the change as done.

## Present snippets honestly
- Send a snippet the user must copy as its own message, separate from the explanation, so the user copies only the snippet.
- When a snippet you sent fails, tell the user at once and concede the failure plainly. Send only a corrected snippet that you checked against Windows PowerShell 5.1.
- When a snippet fails, ask the user to paste back the error text, and use it to fix the exact line rather than guessing at a new snippet.

## Available connectors
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results
- When a shell route adds quoting risk and the web interface makes the same change, offer the web interface.
- When the user needs only one random value, offer a shorter snippet with fewer symbols, because fewer symbols mean fewer quoting failures.
