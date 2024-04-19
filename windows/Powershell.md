# Powershell

_I have one and only precious life, why am doing this?_ 🥲 

## Intro

Powershell is a **command-line shell** and a **scripting language**.
+ built with .NET framework
+ command line shell -> run individuals commands
+ scripting language -> create and execute more complex scripts

When you want to create folders for 30 or 100 users, command line is better than GUI.

Command prompt =/= Powershell

Powershell commands are called **CmdLets** (command-lets)
The format of commands is: **Verb-Noun**.

## `Get-Help` !!!

The first thing we need to do is know how to `Get-Help` on commands or how to RTFM.

*The most important command to know*
```powershell
Get-Help <command name>
# or
# to open browser window with cmdlet info
Get-Help <command name> -Online

```

Some documentation is missing for some commands, so we need to run `Update-Help` **as administrator**.
This wasn't possible for me and I had some errors, that I troubleshooted (see section Troubleshooting). 

## Syntax

**cmdlets** follow the syntax verb + noun such as `Get-Help`, `Get-Date`, `Write-Host`

[See Verbs for powershell cmdlet](https://learn.microsoft.com/fr-fr/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands?view=powershell-5.1)

It's possible to do pattern-matching
`Get-Command Verb-*` or `Get-Command *-Noun`

## Some basic commands

Some basic linux commands (such as ls, cp, mv, pwd...) work in a Powershell terminal.
Some basic commands for files manipulation, check [cheatsheet](#cheatsheet) for more.

**`Get-Command`**
`Get-Command` will get all the _cmdlets_ installed on the current computer.

**`Get-ChildItem`**
`ls` is the equivalent of `Get-ChildItem`
ex: `Get-ChildItem -Path "C:\"`

**`New-Item`**
Equivalent to `touch`

**`Get-Content`**
Equivalent to `cat`

**`Copy-Item`**
Equivalent to `cp`

**`Move-Item`**
Equivalent to `mv`

**`Remove-Item`**
Equivalent to `rm`

## Aliases

There are some aliases for cmdlets.
```powershell
Get-Alias <cmdlet>
```

See: [Using aliases](https://learn.microsoft.com/en-us/powershell/scripting/learn/shell/using-aliases?view=powershell-7.4)


## File Permisions


`Get-Acl`, `Set-Acl`, `RunAs`
`Get-Localuser` to get a list of users and if they are enabled or not

🚧 ...

## Environment Variables

```powershell
# Display a variable
echo $env:computername

# Assign a value to a env variable
$env:test = "some text"

# Add to 
$env:test += " more text" 
```

[Recognized environment variables](https://learn.microsoft.com/en-us/windows/deployment/usmt/usmt-recognized-environment-variables)

### `$env:path`

This variable stores the location where Windows looks for files that are not in your current folder. 
For example, if you call VSCode from the powershell terminal, it opens it even if the executable isn't present in the current folder. That's because the path to the vscode's executable is stored in `$env:path`.

**Add `machin` to your path**

## Scripts

+ Extension for file: .ps1 
+ Run script with: `.\host-commands.ps1`
	+ In most shells, the forward slash notation `./` may also be used.

## Variables

**Create a variable**
```
$my_string_variable = "Hello, World!"
```

**User Input**
```powershell
$my_input = Read-Host -Prompt "Enter a number"
```

**Use variables in a string**
```powershell
Write-Host "Hello, $name! You are $age years old."
```

**Variables types**







## Cheatsheet

| cmdlet                                       | action                               | Aliases                     | linux equivalent    |
| -------------------------------------------- | ------------------------------------ | --------------------------- | ------------------- |
| `Get-Help <command> -examples`               | Get help about commands              |                             | `<command> -- help` |
| `Get-Command`                                | Get all available commands           | gcm                         |                     |
| `Get-Command -Verb <verb>`                   | Look for specific verbs              |                             |                     |
| `Get-Command -Noun <noun>`                   | Look for specific nouns              |                             |                     |
| `Get-Location`                               | Print current location on the screen |                             | `pwd`               |
| `Get-ChildItem`                              | Print content of current directory   |                             | `ls`                |
| `Get-ChildItem -Path "C:\"`                  | Print content of C:\                 |                             | `ls <directory>`    |
| `Set-Location -Path <path name>`             | Go to directory                      | `sl`, `chdir`, `cd`         | `cd`                |
| `Get-ChildItem -Path "C:\Users\me"`          | Print content of home folder         |                             |                     |
| `Get-History`                                | Get history                          | `h`, `ghy`                  | `history`           |
| `Get-Alias <cmdlet>`                         | Gets the alias for the cmdlets       | `gal`                       |                     |
| `Get-Content`                                | Display file content                 |                             | `cat`               |
| `New-Item [-Path] -Name [-ItemType "file"]`  | Create new file                      |                             | `touch`             |
| `New-Item -Path -Name -ItemType "directory"` | Create new directory                 |                             | `mkdir`             |
| `Move-Item`                                  | Move or rename file or directory     | `mi`, `mv`                  | `mv`                |
| `Rename-Item`                                | Rename file                          | `rni`, `ren`                | `mv`                |
| `Remove-item`                                | Delete item                          | `del`, `erase`, `rd`, `ri`, | `rm`, `rmdir`       |
| **Permissions**                              |                                      |                             |                     |
| `Get-Localuser`                              | Get list of users                    |                             |                     |
| `New-LocalUser`                              | Create new user                      |                             |                     |
| `Set-LocalUser`                              |                                      |                             |                     |
| `Get-Acl`                                    |                                      |                             |                     |
| `Set-Acl`                                    |                                      |                             |                     |
| `RunAs`                                      |                                      |                             |                     |
|                                              |                                      |                             |                     |
|                                              |                                      |                             |                     |
|                                              |                                      |                             |                     |
|                                              |                                      |                             |                     |
| `Read-Host -Prompt "Enter a number"`         | Get user input                       |                             |                     |
|                                              |                                      |                             |                     |


## Resources

https://www.youtube.com/@PowershellOrg/videos

 
## Troubleshooting

+ Updating help for the PSReadLine module in windows powershell 5.1
🚧 Add screen cap and link

🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧 

## Misc / Unsorted 

```powershell-session
Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber
```

`Get-Help`
`Get-ChildItem`


---

```powershell-session
Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber
```
Some other classes to use:
+ `Win32_Process` to get a process listing
+ `Win32_Service` to get a listing of services
+ `Win32_Bios` to get [Basic Input/Output System](https://en.wikipedia.org/wiki/BIOS) (`BIOS`) information.
![[Pasted image 20240415115906.png]]
![[Pasted image 20240415121613.png]]

**Prompt**
`prompt $D - $T : $P$G`
Censé afficher la date et l'heure mais ne fonctionne pas 

