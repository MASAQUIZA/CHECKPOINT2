# Débogage de script PowerShell 
les resultat de la disponibilité des fichier dans la machine Client

<img width="414" alt="image" src="https://github.com/user-attachments/assets/1fb29f92-9f67-4e63-bc68-dcc2ee8dd9b0" />


<img width="275" alt="image" src="https://github.com/user-attachments/assets/dc06ceba-65d0-4223-968f-04060dd871e5" />


b)
execution de script main.ps1

<img width="475" alt="image" src="https://github.com/user-attachments/assets/0466b6b0-039b-48d0-9c07-2cbc5ac79d42" />

Execution de script AddLocalUsers

le script est change de "Utilisateur" Par "Users" et c'execute bien


<img width="317" alt="image" src="https://github.com/user-attachments/assets/0969ac63-5ba5-4721-9cbc-33021c29a97f" />

## ESCRIPT MODIFIE
function Log
{
    param([string]$FilePath,[string]$Content)

    # Vérifie si le fichier existe, sinon le crée
    If (-not (Test-Path -Path $FilePath))
    {
        New-Item -ItemType File -Path $FilePath | Out-Null
    }

    # Construit la ligne de journal
    $Date = Get-Date -Format "dd/MM/yyyy-HH:mm:ss"
    $User = [System.Security.Principal.WindowsIdentity]::GetCurrent().Name
    $logLine = "$Date;$User;$Content"

    # Ajoute la ligne de journal au fichier
    Add-Content -Path $FilePath -Value $logLine
}

Function Random-Password ($length = 10)
{
    $punc = 33..47 + 58..64 + 91..96 + 123..126
    $digits = 48..57
    $letters = 65..90 + 97..122

    $password = Get-random -Count $length -InputObject ($punc + $digits + $letters) |`
        ForEach-Object { [char]$_ } -join ""
    Return $password
}

Function ManageAccentsAndCapitalLetters
{
    param ([String]$String)
    
    $StringWithoutAccent = $String -replace '[éèêë]', 'e' -replace '[àâä]', 'a' -replace '[îï]', 'i' -replace '[ôö]', 'o' -replace '[ùûü]', 'u' -replace '[ç]', 'c'
    $StringWithoutAccentAndCapitalLetters = $StringWithoutAccent.ToLower()
    $StringWithoutAccentAndCapitalLetters
}

$Path = "C:\Scripts"
$CsvFile = "$Path\Users.csv"
$LogFile = "$Path\Log.log"

$Users = Import-Csv -Path $CsvFile -Delimiter ";" -Encoding UTF8 | Select-Object prenom, nom, description

foreach ($User in $Users)
{
    $Prenom = ManageAccentsAndCapitalLetters -String $User.prenom
    $Nom = ManageAccentsAndCapitalLetters -String $User.Nom
    $Name = "$Prenom.$Nom"
    If (-not(Get-LocalUser -Name $Nom" -ErrorAction SilentlyContinue))
    {
        $Pass = Random-Password
        $Password = (ConvertTo-secureString $Pass -AsPlainText -Force)
        $Description = "$($user.description) - $($User.fonction)"
        $UserInfo = @{
            Name                 = "$Prenom.$Nom"
            FullName             = "$Prenom.$Nom"
            Description          = $Description
            Password             = $Password
            AccountNeverExpires  = $true
            PasswordNeverExpires = $true
        }

        New-LocalUser $User.description
        Add-LocalGroupMember -Group "Users" -Member "$Name"
        Write-Host "L'utilisateur $Name a été crée avec succès."
    }
}

