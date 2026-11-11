# Azure Learning Environment

## Environment

### Hardware
- OS: Windows 11
- Architecture: x64

### Software
- Visual Studio Code
- Azure CLI
- Azure PowerShell

## Tools

| Tool | Purpose |
|---|---|
| Visual Studio Code | コード・設定ファイルの編集 |
| Azure CLI | Azureリソースの操作・管理 |
| Azure PowerShell | PowerShellによるAzureリソースの操作 |

## Setup

### Visual Studio Code

- **Installation**
  - [Visual Studio Code - Windows 64bit](https://code.visualstudio.com/thank-you?dv=win64user&build=stable)

### Azure CLI

- **Installation**
  - [Microsoft Learn - Install Azure CLI on Windows](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?pivots=winget)
  - Command:
    ```powershell
    winget install --exact --id Microsoft.AzureCLI --source winget
    ```

- **Version verification**
  - Command:
    ```powershell
    az version
    ```
  - Output:
    ```json
    {
      "azure-cli": "2.92.0",
      "azure-cli-core": "2.92.0",
      "azure-cli-telemetry": "1.1.0",
      "extensions": {}
    }
    ```

- **Login**
  - Command:
    ```powershell
    az login
    ```
  - Output:
    ```text
    Select the account you want to log in with. For more information on login with Azure CLI, see https://go.microsoft.com/fwlink/?linkid=2271136

    Retrieving tenants and subscriptions for the selection...
    No subscriptions found for hogehoge.
    ```
  - Microsoftアカウントによる認証
  - Azureサブスクリプション未登録のため、Subscription無し
  - ※認証情報はセキュリティ上、記載しない

### Azure PowerShell

- **Installation**
  - PowerShell 7
  - Command:
    ```powershell
    $PSVersionTable
    ```
  - Output:
    ```text
    Name                           Value
    ----                           -----
    PSVersion                      7.6.9
    PSEdition                      Core
    GitCommitId                    7.6.9
    OS                             Microsoft Windows 10.0.26300
    Platform                       Win32NT
    PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
    PSRemotingProtocolVersion      2.4
    SerializationVersion           1.1.0.1
    WSManStackVersion              3.0
    ```
  - Command:
    ```powershell
    Get-Command pwsh
    ```
  - Output:
    ```text
    CommandType  Name      Version  Source
    -----------  ----      -------  ------
    Application  pwsh.exe  7.6.9.0  C:\Program Files\PowerShell\7\pwsh.exe
    ```

- **Module installation**
  - Command:
    ```powershell
    Install-Module -Name Az -Repository PSGallery -Force -AllowClobber
    ```

- **Login**
  - Command:
    ```powershell
    Connect-AzAccount -UseDeviceAuthentication
    ```
  - Output:
    ```text
    Please select the account you want to log in with.

    [Login to Azure] To sign in, use a web browser to open the page https://login.microsoft.com/device and enter the code hogehoge to authenticate.

    Retrieving subscriptions for the selection...

    Subscription name Tenant
    ----------------- ------
    ```
  - Microsoftアカウントによるデバイスコード認証
  - Azureサブスクリプション未登録のため、Subscription無し
  - ※認証情報はセキュリティ上、記載しない

- **Version verification**
  - PowerShell
    - Command:
      ```powershell
      $PSVersionTable.PSVersion
      ```
    - Output:
      ```text
      Major  Minor  Patch  PreReleaseLabel BuildLabel
      -----  -----  -----  --------------- ----------
      7      6      9
      ```
  - Az module
    - Command:
      ```powershell
      Get-InstalledModule -Name Az
      ```
    - Output:
      ```text
      Version  Name  Repository  Description
      -------  ----  ----------  -----------
      16.5.0   Az    PSGallery   Microsoft Azure PowerShell - Cmdlets to manage resources in Azure. This module is compatible with PowerShell and Windows PowerShell.…
      ```
