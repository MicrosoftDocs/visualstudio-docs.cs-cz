---
title: Použití skriptů Windows PowerShellu k publikování do vývojových a testovacích prostředí | Microsoft Docs
description: Naučte se používat skripty prostředí Windows PowerShell ze sady Visual Studio k publikování do vývojových a testovacích prostředí.
author: ghogen
manager: jillfra
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: a6d6611c8ce8bdb09023794b5eca029b6b972afb
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849979"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Použití skriptů PowerShellu k publikování do vývojových a testovacích prostředí

Při vytváření webové aplikace v aplikaci Visual Studio můžete vygenerovat skript prostředí Windows PowerShell, který později můžete použít k automatizaci publikování webu do Azure jako webové aplikace v Azure App Service nebo virtuálního počítače. Skript prostředí Windows PowerShell můžete upravit a roztáhnout v editoru sady Visual Studio tak, aby vyhovoval vašim požadavkům, nebo můžete skript integrovat s existujícími skripty pro sestavení, testování a publikování.

Pomocí těchto skriptů můžete zřídit přizpůsobené verze (označované taky jako vývojová a testovací prostředí) vašeho webu pro dočasné použití. Můžete například nastavit konkrétní verzi webu na virtuálním počítači Azure nebo na přípravném slotu na webu, abyste spustili testovací sadu, reprodukovali chybu, otestovali opravu chyby, vyzkoušeli navrhovanou změnu nebo si pro ukázku nebo prezentaci nastavili vlastní prostředí. Po vytvoření skriptu, který publikuje projekt, můžete znovu vytvořit identická prostředí tím, že skript znovu spustíte znovu, nebo spustíte skript s vlastním sestavením webové aplikace, abyste vytvořili vlastní prostředí pro testování.

## <a name="prerequisites"></a>Požadavky

* Azure SDK 2,3 nebo novější. Viz [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/). (Nepotřebujete, aby sada Azure SDK generovala skripty pro webové projekty. Tato funkce je určena pro webové projekty, nikoli pro webové role v Cloud Services.)
* Azure PowerShell 0.7.4 nebo novější. Viz téma [Instalace a konfigurace prostředí Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3,0](https://docs.microsoft.com/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control) nebo novější.

## <a name="additional-tools"></a>Další nástroje

K dispozici jsou další nástroje a prostředky pro práci s prostředím PowerShell v aplikaci Visual Studio pro vývoj pro Azure. Viz [PowerShell Tools for Visual Studio](https://visualstudiogallery.msdn.microsoft.com/c9eb3ba8-0c59-4944-9a62-6eee37294597).

## <a name="generating-the-publish-scripts"></a>Generování publikačních skriptů

Můžete vygenerovat skripty pro publikování pro virtuální počítač, který je hostitelem webu při vytváření nového projektu pomocí následujících [pokynů](/azure/virtual-machines/windows/classic/web-app-visual-studio?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json). Můžete také [vygenerovat publikační skripty pro webové aplikace v Azure App Service](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Skripty vygenerované v aplikaci Visual Studio

Visual Studio vygeneruje složku na úrovni řešení s názvem **PublishScripts** , která obsahuje dva soubory Windows PowerShellu, skript pro publikování pro virtuální počítač nebo web a modul obsahující funkce, které můžete ve skriptech použít. Visual Studio také generuje soubor ve formátu JSON, který určuje podrobnosti projektu, který nasazujete.

### <a name="windows-powershell-publish-script"></a>Skript publikování Windows PowerShellu

Skript publikování obsahuje konkrétní kroky publikování pro nasazení na web nebo virtuální počítač. Visual Studio poskytuje zvýraznění syntaxe pro vývoj v prostředí Windows PowerShell. K dispozici je nápovědu pro funkce a můžete volně upravovat funkce ve skriptu, aby vyhovovaly vašim měnícím se požadavkům.

### <a name="windows-powershell-module"></a>Modul Windows PowerShell

Modul prostředí Windows PowerShell, který generuje aplikace Visual Studio, obsahuje funkce, které používá skript pro publikování. Tyto funkce Azure PowerShell nejsou určeny pro úpravy. Viz téma [Instalace a konfigurace prostředí Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>Konfigurační soubor JSON

Soubor JSON se vytvoří ve složce **Konfigurace** a obsahuje konfigurační data, která přesně určují, které prostředky se mají nasadit do Azure. Název souboru, který vygeneruje aplikace Visual Studio, je Project-Name-WAWS-dev. JSON, pokud jste vytvořili web nebo název projektu-VM-dev. JSON, pokud jste vytvořili virtuální počítač. Tady je příklad konfiguračního souboru JSON, který se generuje při vytváření webu. Většina hodnot je zřejmá. Název webu vygeneruje Azure, takže se nemusí shodovat s názvem projektu.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Když vytváříte virtuální počítač, konfigurační soubor JSON vypadá podobně jako následující. Cloudová služba je vytvořená jako kontejner pro virtuální počítač. Virtuální počítač obsahuje obvyklé koncové body pro webový přístup prostřednictvím protokolů HTTP a HTTPS a také koncových bodů pro Nasazení webu, které vám umožní publikovat na webu z místního počítače, vzdálené plochy a prostředí Windows PowerShell.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Můžete upravit konfiguraci JSON, abyste mohli změnit to, co se stane při spuštění skriptů pro publikování. Oddíly `cloudService` a `virtualMachine` jsou povinné, ale pokud ji nepotřebujete, můžete ji `databases` odstranit. Vlastnosti, které jsou prázdné ve výchozím konfiguračním souboru, který vygeneruje aplikace Visual Studio, jsou volitelné; jsou požadovány vlastnosti, které mají hodnoty ve výchozím konfiguračním souboru.

Pokud máte web s více prostředími nasazení (označovanými jako sloty) místo jediného produkčního webu v Azure, můžete do konfiguračního souboru JSON přidat název slotu do názvu webu. Pokud máte například web s názvem **Web** a slot pro IT s názvem **test** , je identifikátor URI `mysite-test.cloudapp.net`, ale správný název, který se má použít v konfiguračním souboru, je web (test). To lze provést pouze v případě, že web a sloty již existují v rámci vašeho předplatného. Pokud neexistují, vytvořte web spuštěním skriptu bez zadání slotu a pak vytvořte slot v [Azure Portal](https://portal.azure.com/)a potom spusťte skript s upraveným názvem webu. Další informace o slotech nasazení pro webové aplikace najdete [v tématu Nastavení přípravného prostředí pro webové aplikace v Azure App Service](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Spuštění skriptů pro publikování

Pokud jste nikdy nespouštěli skript prostředí Windows PowerShell, musíte nejprve nastavit zásady spouštění, aby bylo možné spouštět skripty. Zásada je funkce zabezpečení, která uživatelům brání v spouštění skriptů prostředí Windows PowerShell, pokud jsou zranitelná proti malwaru nebo virům, které zahrnují spouštění skriptů.

### <a name="run-the-script"></a>Spuštění skriptu

1. Vytvořte balíček Nasazení webu pro svůj projekt. Nasazení webu balíček je komprimovaný archivní soubor (ZIP) obsahující soubory, které chcete zkopírovat do vašeho webu nebo virtuálního počítače. V aplikaci Visual Studio můžete vytvořit balíčky Nasazení webu pro všechny webové aplikace.

   ![Vytvořit balíček Nasazení webu](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Další informace najdete v tématu [Postup: vytvoření balíčku pro nasazení webu v aplikaci Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx). Můžete také automatizovat vytváření balíčku Nasazení webu, jak je popsáno v tématu [přizpůsobení a rozšíření publikačních skriptů](#customizing-and-extending-the-publish-scripts).

1. V **Průzkumník řešení**otevřete kontextovou nabídku pro skript a pak zvolte **otevřít v prostředí PowerShell ISE**.
1. Pokud na tomto počítači spouštíte skripty prostředí Windows PowerShell poprvé, otevřete okno příkazového řádku s oprávněními správce a zadejte následující příkaz:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Přihlaste se k Azure pomocí následujícího příkazu.

    ```powershell
    Add-AzureAccount
    ```

    Po zobrazení výzvy zadejte své uživatelské jméno a heslo.

    Všimněte si, že při automatizaci skriptu Tato metoda poskytování přihlašovacích údajů Azure nefunguje. Místo toho byste měli použít soubor `.publishsettings` k zadání přihlašovacích údajů. Jenom jednou použijte příkaz **Get-AzurePublishSettingsFile** ke stažení souboru z Azure a pak použijte **Import-AzurePublishSettingsFile** k importu tohoto souboru. Podrobné pokyny najdete v tématu [Instalace a konfigurace prostředí Azure PowerShell](/powershell/azure/overview).

1. Volitelné Pokud chcete vytvořit prostředky Azure, jako je například virtuální počítač, databáze a web bez publikování webové aplikace, použijte příkaz **Publish-WebApplication. ps1** s argumentem **-Configuration** nastaveným na konfigurační soubor JSON. Tento příkazový řádek pomocí konfiguračního souboru JSON určí, které prostředky se mají vytvořit. Protože používá výchozí nastavení pro jiné argumenty příkazového řádku, vytvoří prostředky, ale nepublikuje webovou aplikaci. Možnost – verbose vám poskytne další informace o tom, co se děje.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Použijte příkaz **Publish-WebApplication. ps1** , jak je znázorněno v jednom z následujících příkladů k vyvolání skriptu a publikování webové aplikace. Pokud potřebujete přepsat výchozí nastavení pro některý z dalších argumentů, jako je název předplatného, název balíčku pro publikování, přihlašovací údaje virtuálního počítače nebo pověření pro databázový server, můžete tyto parametry zadat. K zobrazení dalších informací o průběhu procesu publikování použijte možnost **– verbose** .

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Pokud vytváříte virtuální počítač, příkaz vypadá následovně. Tento příklad také ukazuje, jak zadat pověření pro více databází. Pro virtuální počítače, které tyto skripty vytvářejí, není certifikát SSL od důvěryhodné kořenové autority. Proto je nutné použít možnost **– AllowUntrusted** .

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Skript může vytvořit databáze, ale nevytváří databázové servery. Pokud chcete vytvořit databázový server, můžete použít funkci **New-AzureSqlDatabaseServer** v modulu Azure.

## <a name="customizing-and-extending-the-publish-scripts"></a>Přizpůsobení a rozšíření publikačních skriptů

Můžete přizpůsobit skript pro publikování a konfigurační soubor JSON. Funkce v modulu Windows PowerShell **AzureWebAppPublishModule. psm1** nejsou určeny pro úpravy. Pokud chcete pouze zadat jinou databázi nebo změnit některé z vlastností virtuálního počítače, upravte konfigurační soubor JSON. Chcete-li rozšířené funkce skriptu pro automatizaci vytváření a testování projektu, můžete implementovat zástupné procedury funkce v **Publish-WebApplication. ps1**.

Chcete-li automatizovat sestavování projektu, přidejte kód, který volá MSBuild pro `New-WebDeployPackage`, jak je znázorněno v tomto příkladu kódu. Cesta k příkazu MSBuild se liší v závislosti na verzi sady Visual Studio, kterou jste nainstalovali. Chcete-li získat správnou cestu, můžete použít funkci **Get-MSBuildCmd**, jak je znázorněno v tomto příkladu.

### <a name="to-automate-building-your-project"></a>Automatizace sestavení projektu

1. Přidejte parametr `$ProjectFile` do oddílu globální param.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Zkopírujte funkci `Get-MSBuildCmd` do souboru skriptu.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. Nahraďte `New-WebDeployPackage` následujícím kódem a nahraďte zástupné symboly v `$msbuildCmd`konstrukce čáry. Tento kód je určen pro Visual Studio 2015. Pokud používáte Visual Studio 2017, změňte vlastnost **VisualStudioVersion** na `15.0` (`12.0` pro Visual Studio 2013).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    K sestavení webové aplikace použijte nástroj MsBuild. exe. Nápovědu najdete v tématu Reference k příkazovému řádku MSBuild na adrese: [http://go.microsoft.com/fwlink/?LinkId=391339](https://msdn.microsoft.com/library/ms164311.aspx)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Spustit provádění příkazu buildu

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. Před tímto řádkem volejte funkci `New-WebDeployPackage`: `$Config = Read-ConfigFile $Configuration` pro webové aplikace nebo `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` pro virtuální počítače.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Vyvolejte přizpůsobený skript z příkazového řádku pomocí předání argumentu `$Project`, jak je uvedeno v následujícím příkladu:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    K automatizaci testování vaší aplikace přidejte kód do `Test-WebApplication`. Nezapomeňte odkomentovat řádky v **Publish-WebApplication. ps1** , kde jsou tyto funkce volány. Pokud neposkytnete implementaci, můžete projekt sestavit ručně pomocí sady Visual Studio a potom spuštěním publikačního skriptu publikovat do Azure.

## <a name="publishing-function-summary"></a>Souhrn funkcí publikování
Nápovědu k funkcím, které můžete použít na příkazovém řádku prostředí Windows PowerShell, získáte, když použijete příkaz `Get-Help function-name`. Help obsahuje parametr a příklady. Stejný text v nápovědě je také ve zdrojových souborech skriptu **AzureWebAppPublishModule. psm1** a **Publish-WebApplication. ps1**. Skript a nápovědě jsou lokalizovány do jazyka Visual Studio.

**AzureWebAppPublishModule**

| Název funkce | Popis |
| --- | --- |
| Add-AzureSQLDatabase |Vytvoří novou databázi SQL Azure. |
| Add-AzureSQLDatabases |Vytvoří databáze Azure SQL z hodnot v konfiguračním souboru JSON, který generuje aplikace Visual Studio. |
| Add-AzureVM |Vytvoří virtuální počítač Azure a vrátí adresu URL nasazeného virtuálního počítače. Tato funkce nastaví požadavky a potom zavolá funkci **New-AzureVM** (modul Azure), která vytvoří nový virtuální počítač. |
| Add-AzureVMEndpoints |Přidá nové vstupní koncové body do virtuálního počítače a vrátí virtuální počítač s novým koncovým bodem. |
| Add-AzureVMStorage |Vytvoří nový účet úložiště Azure v aktuálním předplatném. Název účtu začíná řetězcem "DevTest" následovaným jedinečným alfanumerickým řetězcem. Funkce vrátí název nového účtu úložiště. Zadejte buď umístění, nebo skupinu vztahů pro nový účet úložiště. |
| Add-AzureWebsite |Vytvoří web se zadaným názvem a umístěním. Tato funkce volá funkci **New-AzureWebsite** v modulu Azure. Pokud předplatné ještě neobsahuje web se zadaným názvem, tato funkce vytvoří web a vrátí objekt webu. V opačném případě vrátí `$null`. |
| Backup – předplatné |Uloží aktuální předplatné Azure do proměnné `$Script:originalSubscription` v oboru skriptu. Tato funkce uloží aktuální předplatné Azure (získané `Get-AzureSubscription -Current`) a jeho účet úložiště a předplatné, které tento skript změnil (uložený v proměnné `$UserSpecifiedSubscription`) a jeho účet úložiště v oboru skriptu. Uložením hodnot můžete použít funkci, například `Restore-Subscription`, k obnovení původního aktuálního předplatného a účtu úložiště na aktuální stav, pokud se změní aktuální stav. |
| Find-AzureVM |Načte zadaný virtuální počítač Azure. |
| Format – DevTestMessageWithTime |Dořadí datum a čas do zprávy. Tato funkce je navržena pro zprávy zapsané do chyby a podrobné datové proudy. |
| Get-AzureSQLDatabaseConnectionString |Sestaví připojovací řetězec pro připojení k databázi SQL Azure. |
| Get-AzureVMStorage |Vrátí název prvního účtu úložiště se vzorem názvu "DevTest *" (bez rozlišení malých a velkých písmen) v zadaném umístění nebo skupině vztahů. Pokud účet úložiště "DevTest*" neodpovídá umístění nebo skupině vztahů, funkce ho ignoruje. Zadejte buď umístění, nebo skupinu vztahů. |
| Get-MSDeployCmd |Vrátí příkaz pro spuštění nástroje MsDeploy. exe. |
| New-AzureVMEnvironment |Najde nebo vytvoří v předplatném virtuální počítač, který odpovídá hodnotám v konfiguračním souboru JSON. |
| Publish – balíček publikování |Používá soubor MsDeploy. exe a balíček pro publikování na webu. Soubor zip k nasazení prostředků na web. Tato funkce negeneruje žádný výstup. Pokud volání MSDeploy. exe neproběhne úspěšně, funkce vyvolá výjimku. Chcete-li získat podrobnější výstup, použijte možnost **-verbose** . |
| Publish-WebPackageToVM |Ověří hodnoty parametru a potom zavolá funkci **Publish-webpackage** . |
| Číst – ConfigFile |Ověří konfigurační soubor JSON a vrátí zatřiďovací tabulku vybraných hodnot. |
| Obnovení předplatného |Obnoví aktuální předplatné na původní předplatné. |
| Test-AzureModule |Vrátí `$true`, pokud je nainstalovaná verze modulu Azure 0.7.4 nebo novější. Pokud modul není nainstalovaný nebo má starší verzi, vrátí se `$false`. Tato funkce nemá žádné parametry. |
| Test-AzureModuleVersion |Vrátí `$true`, pokud je verze modulu Azure 0.7.4 nebo novější. Pokud modul není nainstalovaný nebo má starší verzi, vrátí se `$false`. Tato funkce nemá žádné parametry. |
| Test-HttpsUrl |Převede vstupní adresu URL na objekt System. URI. Vrátí `$True`, pokud je adresa URL absolutní a její schéma je HTTPS. Vrátí `$false`, pokud je adresa URL relativní, její schéma není HTTPS, nebo vstupní řetězec nelze převést na adresu URL. |
| Testovací člen |Vrátí `$true`, je-li vlastnost nebo metoda členem objektu. V opačném případě vrátí `$false`. |
| Zápis – ErrorWithTime |Zapíše chybovou zprávu s aktuálním časem. Tato funkce volá funkci **Format-DevTestMessageWithTime** , aby předpsala čas před zápisem zprávy do datového proudu chyb. |
| Zápis – HostWithTime |Zapíše zprávu do hostitelského programu (**Write-Host**) s aktuálním časem. Účinek psaní do hostitelského programu se liší. Většina programů, které hostují Windows PowerShell, zapíše tyto zprávy do standardního výstupu. |
| Write-VerboseWithTime |Zapíše podrobnou zprávu s aktuálním časem. Vzhledem k tomu, že volá metodu **Write-verbose**, zpráva se zobrazí pouze v případě, že se skript spustí s parametrem **verbose** nebo pokud je nastavená předvolby **VerbosePreference** na **pokračovat**. |

**Publikování – WebApplication**

| Název funkce | Popis |
| --- | --- |
| New-AzureWebApplicationEnvironment |Vytvoří prostředky Azure, jako je například web nebo virtuální počítač. |
| New-WebDeployPackage |Tato funkce není implementovaná. Můžete přidat příkazy v této funkci pro sestavení projektu. |
| Publish-AzureWebApplication |Publikuje webovou aplikaci do Azure. |
| Publikování – WebApplication |Vytvoří a nasadí Web Apps, virtuální počítače, databáze SQL a účty úložiště pro webový projekt sady Visual Studio. |
| Test – WebApplication |Tato funkce není implementovaná. K otestování aplikace můžete do této funkce přidat příkazy. |

## <a name="next-steps"></a>Další kroky
Další informace o skriptování PowerShellu najdete v tématu [skriptování v prostředí Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx) a další Azure PowerShell skripty najdete v [centru skriptů](https://azure.microsoft.com/documentation/scripts/).
