## POSH-GIT AND OH-MY-POSH FOR POWERSHELL

See https://www.hanselman.com/blog/HowToMakeAPrettyPromptInWindowsTerminalWithPowerlineNerdFontsCascadiaCodeWSLAndOhmyposh.aspx

Themes:

- https://atomcorp.github.io/themes/
- https://terminalsplash.com/

1. Install PS : https://github.com/PowerShell/PowerShell/releases

```powershell
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
```

Then run "notepad \$PROFILE" and add these lines to the end:

```powershell
Import-Module posh-git
Import-Module oh-my-posh
Set-Theme Paradox
```

## WSL Ubuntu

```bash
sudo apt install golang-go
go get -u github.com/justjanne/powerline-go
```

Add the following to your .bashrc

```bash
function _update_ps1() {
    PS1="$($GOPATH/bin/powerline-go -error $?)"
}

if [ "$TERM" != "linux" ] && [ -f "$GOPATH/bin/powerline-go" ]; then
    PROMPT_COMMAND="_update_ps1; $PROMPT_COMMAND"
fi
```
