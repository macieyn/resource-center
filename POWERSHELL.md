## Oh My Posh Settings
```powershell
Import-Module posh-git
Import-Module oh-my-posh
Set-Theme Agnoster
```

## Powershell Functions to give it more Bash feeling

```powershell
function touch {
 $Path = $args[0]
 ni $Path | Out-Null
}

function pwd {
    Get-Location
}

function ls {
    $path = $args[0]

    if (-Not $path) {
        $path = '.' 
    }
    
    Write-Host ((Get-ChildItem $path -Name -Directory) -split "`n" -join "   ") "  " -ForegroundColor Green -nonewline
    Write-Host ((Get-ChildItem $path -Name -File) -split "`n" -join "   ") -ForegroundColor Cyan
}
```

## Command to create gitignore file
Options are displayed here https://github.com/github/gitignore
```powershell
function gitignore{
    $Lang = $args[0]
    $url = "https://raw.githubusercontent.com/github/gitignore/master/" + $Lang + ".gitignore"
    curl -UseBasicParsing $url -o .gitignore
}
```

Usage: `gitignore Python`
