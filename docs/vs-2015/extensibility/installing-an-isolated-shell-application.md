---
title: Instalace aplikace izolovaného prostředí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a077173a0d095ee10cc1fa16da3db1f3744dafa8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301162"
---
# <a name="installing-an-isolated-shell-application"></a>Instalace aplikací izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete nainstalovat aplikaci prostředí, musíte provést následující kroky.  
  
- Připravte své řešení.  
  
- Vytvořte balíček Instalační služba systému Windows (MSI) pro vaši aplikaci.  
  
- Vytvoření zaváděcího nástroje pro instalaci.  
  
  Celý ukázkový kód v tomto dokumentu pochází z [ukázky nasazení prostředí](https://go.microsoft.com/fwlink/?LinkId=262245), kterou si můžete stáhnout z Galerie kódu na webu MSDN. Ukázka zobrazuje výsledky provedení každého z těchto kroků.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li provést postupy popsané v tomto tématu, je nutné v počítači nainstalovat následující nástroje.  
  
- Sada Visual Studio SDK  
  
- [Sada nástrojů XML Instalační služba systému Windows](https://go.microsoft.com/fwlink/?LinkId=82720) verze 3,6  
  
  Ukázka také vyžaduje sadu Microsoft vizualizace and modeling SDK, která nevyžaduje všechny prostředí.  
  
## <a name="preparing-your-solution"></a>Připravuje se vaše řešení  
 Ve výchozím nastavení šablony prostředí sestavují balíčky VSIX, ale toto chování je určeno primárně pro účely ladění. Při nasazení aplikace prostředí je nutné použít balíčky MSI k povolení přístupu k registru a k restartování během instalace. K přípravě aplikace na nasazení MSI proveďte následující kroky.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Příprava aplikace prostředí pro nasazení MSI  
  
1. Upravte každý soubor. vsixmanifest ve vašem řešení.  
  
     V elementu `Identifier` přidejte prvek `InstalledByMSI` a prvek `SystemComponent` a pak nastavte jejich hodnoty na `true`.  
  
     Tyto prvky brání instalačnímu programu VSIX v pokusu o instalaci vašich komponent a uživatel z jeho odinstalace pomocí dialogového okna **rozšíření a aktualizace** .  
  
2. Pro každý projekt, který obsahuje manifest VSIX, upravte úkoly sestavení pro výstup obsahu do umístění, ze kterého bude nainstalována služba MSI. Zahrňte manifest VSIX do výstupu sestavení, ale Sestavte soubor. VSIX.  
  
## <a name="creating-an-msi-for-your-shell"></a>Vytvoření MSI pro prostředí  
 Pro sestavení balíčku MSI doporučujeme použít [sadu nástrojů Instalační služba systému Windows XML](https://go.microsoft.com/fwlink/?LinkId=82720) , protože poskytuje větší flexibilitu než standardní projekt instalace.  
  
 V souboru Product. wxs nastavte bloky detekce a rozložení komponent prostředí.  
  
 Pak vytvořte položky registru v souboru. reg pro vaše řešení a v ApplicationRegistry. wxs.  
  
### <a name="detection-blocks"></a>Bloky detekce  
 Blok detekce se skládá z prvku `Property`, který určuje předpoklad pro detekci a `Condition` elementu, který určuje zprávu, která se má vrátit, pokud se požadovaná součást nenachází v počítači. Například vaše aplikace prostředí bude vyžadovat redistribuovatelný Microsoft Visual Studio Shell a detekční blok bude vypadat podobně jako následující kód.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Rozložení komponent prostředí  
 Je nutné přidat prvky, které identifikují cílovou adresářovou strukturu a součásti k instalaci.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Nastavení rozložení komponent prostředí  
  
1. Vytvořte hierarchii `Directory` prvků, které reprezentují všechny adresáře, které mají být vytvořeny v systému souborů v cílovém počítači, jak ukazuje následující příklad.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Na tyto adresáře se říká `Id`, když jsou zadané soubory, které se musí nainstalovat.  
  
2. Identifikujte součásti, které prostředí a aplikace prostředí vyžadují, jak ukazuje následující příklad.  
  
    > [!NOTE]
    > Některé elementy můžou odkazovat na definice v jiných souborech. wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. Element `ComponentRef` odkazuje na jiný soubor. WXS, který identifikuje soubory, které aktuální komponenta vyžaduje. Například GeneralProfile má následující definici v HelpAbout. wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         Element `DirectoryRef` určuje, kde tyto soubory přecházejí do počítače uživatele. Element `Directory` určuje, že bude nainstalován do podadresáře, a každý prvek `File` představuje soubor, který je sestaven nebo který existuje jako součást řešení, a identifikuje, kde lze tento soubor najít při vytvoření souboru MSI.  
  
    2. Element `ComponentGroupRef` odkazuje na skupinu dalších komponent (nebo komponent a skupin součástí). Například `ComponentGroupRef` v rámci třídy Application je definována takto v Application. wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    > Požadované závislosti pro aplikace Shell (izolovaný režim) jsou: DebuggerProxy, MasterPkgDef, Resources (obzvláště soubor. winprf), Application a PkgDefs.  
  
### <a name="registry-entries"></a>Položky registru  
 Šablona projektu prostředí (izolovaný režim) obsahuje soubor *ProjectName*. reg pro klíče registru ke sloučení při instalaci. Tyto položky registru musí být součástí MSI pro účely instalace i vyčištění. V ApplicationRegistry. WXS musíte také vytvořit vyhovující bloky registru.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Integrace položek registru do MSI  
  
1. Ve složce **vlastního nastavení prostředí** otevřete *ProjectName*. reg.  
  
2. Nahraďte všechny výskyty $RootFolder $ tokenu cestou k cílovému instalačnímu adresáři.  
  
3. Přidejte další položky registru, které vaše aplikace vyžaduje.  
  
4. Otevřete ApplicationRegistry. wxs.  
  
5. Pro každou položku registru v *ProjectName*. reg přidejte odpovídající blok registru, jak ukazuje následující příklad.  
  
    |*ProjectName*. reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "Objekt DTE PhotoStudio"|\<RegistryKey ID = ' DteClsidRegKey ' root = ' HKCR ' klíč = ' $ (var. DteClsidRegKey) ' Action = ' createAndRemoveOnUninstall ' ><br /><br /> \<RegistryValue Type = ' řetězec ' name = ' @ ' value = ' $ (var. ShortProductName) objekt DTE '/><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey ID = ' DteLocSrv32RegKey ' root = ' HKCR ' klíč = ' $ (var. DteClsidRegKey) \LocalServer32 ' Action = ' createAndRemoveOnUninstall ' ><br /><br /> \<RegistryValue Type='string' Name='@' Value='[INSTALLDIR]$(var.ShortProductName).exe' /><br /><br /> \</RegistryKey>|  
  
     V tomto příkladu var. DteClsidRegKey převede na klíč registru v horním řádku. Var. ShortProductName se překládá na `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Vytvoření zaváděcího nástroje pro instalaci  
 Dokončené MSI se nainstalují jenom v případě, že se nejdřív nainstalují všechny požadované součásti. Chcete-li usnadnit činnost koncového uživatele, vytvořte instalační program, který shromáždí a nainstaluje všechny požadavky před instalací aplikace. Chcete-li zajistit úspěšnou instalaci, proveďte tyto akce:  
  
- Vynuťte instalaci správcem.  
  
- Zjišťuje, zda je nainstalováno prostředí sady Visual Studio (izolovaný režim).  
  
- Spusťte jeden nebo oba instalační programy prostředí v daném pořadí.  
  
- Zpracování žádostí o restartování  
  
- Spusťte soubor MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Vynucování instalace správcem  
 Tento postup je nutný, pokud chcete instalačnímu programu povolit přístup k požadovaným adresářům, například \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Vynutili instalaci správcem  
  
1. Otevřete místní nabídku projektu instalace a pak zvolte možnost **vlastnosti**.  
  
2. V části **Vlastnosti konfigurace/linker/soubor manifestu**nastavte **úroveň spuštění nástroje řízení uživatelských účtů** na **vyžadovat správce**.  
  
     Tato vlastnost vloží atribut, který vyžaduje spuštění programu jako správce, do vloženého souboru manifestu.  
  
### <a name="detecting-shell-installations"></a>Detekce instalací prostředí  
 Chcete-li určit, zda je nutné nainstalovat prostředí sady Visual Studio (izolovaný režim), nejprve určete, zda je již nainstalována, pomocí kontroly hodnoty registru HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
> Tyto hodnoty jsou čteny také blokem detekce prostředí v produktu Product. wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder určuje umístění, kde byla nainstalována prostředí Visual Studio Shell, a můžete vyhledat soubory tam.  
  
 Příklad, jak detekovat instalaci prostředí, najdete v ukázce nasazení prostředí v tématu `GetProductDirFromReg` funkce nástrojů. cpp.  
  
 Pokud jeden nebo oba prostředí sady Visual Studio, které balíček vyžaduje, není v počítači nainstalováno, je nutné je přidat do seznamu součástí, které chcete nainstalovat. Příklad naleznete v tématu funkce `ComponentsPage::OnInitDialog` ComponentsPage. cpp v ukázce nasazení prostředí.  
  
### <a name="running-the-shell-installers"></a>Spuštění instalačních programů prostředí  
 Chcete-li spustit instalační programy prostředí, zavolejte distribuovatelné prostředí sady Visual Studio pomocí správných argumentů příkazového řádku. Aby bylo možné zjistit, co by mělo být provedeno v dalším kroku, je nutné použít argumenty příkazového řádku **/norestart/q** a sledovat návratový kód. Následující příklad spustí prostředí shell (izolovaný režim) Redistributable.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Spuštění instalačních programů jazykové sady pro prostředí  
 Pokud místo toho zjistíte, že prostředí nebo prostředí byly nainstalovány a potřebujete pouze jazykovou sadu, můžete nainstalovat jazykové sady, jak ukazuje následující příklad.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Dešifrování návratových hodnot  
 V některých operačních systémech bude instalace prostředí sady Visual Studio (izolovaný režim) vyžadovat restart. Tuto podmínku lze určit pomocí návratového kódu volání `ExecCmd`.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|ERROR_SUCCESS|Instalace byla dokončena. Nyní můžete nainstalovat aplikaci.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Instalace byla dokončena. Po restartování počítače můžete aplikaci nainstalovat.|  
|3015|Probíhá instalace. Aby bylo možné pokračovat v instalaci, je nutné restartovat počítač.|  
  
### <a name="handling-restarts"></a>Zpracování se restartuje.  
 Při spuštění instalačního programu prostředí pomocí argumentu **/norestart** jste určili, že by nebylo možné restartovat počítač nebo požádat o restartování počítače. Může ale být nutné restartovat počítač a před restartováním počítače je nutné zajistit, že instalační program pokračuje.  
  
 Chcete-li správně zpracovat restart, ujistěte se, že je nastaven pouze jeden instalační program a že proces obnovení bude zpracován správně.  
  
 Pokud se vrátí buď ERROR_SUCCESS_REBOOT_REQUIRED nebo 3015, váš kód by měl restartovat počítač před tím, než bude instalace pokračovat.  
  
 Pro zpracování restartování proveďte tyto akce:  
  
- Nastavte registr tak, aby se při spuštění systému Windows obnovila instalace.  
  
- Proveďte dvakrát restart zaváděcího nástroje.  
  
- Odstraňte ResumeData klíč instalačního programu prostředí.  
  
- Restartujte systém Windows.  
  
- Resetujte počáteční cestu ke službě MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Nastavení registru pro pokračování v instalaci při spuštění systému Windows  
 Klíč registru HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ se spouští při spuštění systému s oprávněními správce a pak se vymaže. HKEY_CURRENT_USER obsahuje podobný klíč, ale běží jako normální uživatel a není vhodný pro instalaci. Instalaci můžete obnovit tak, že do klíče RunOnce vložíte řetězcovou hodnotu, která volá váš instalační program. Nicméně doporučujeme, abyste volali instalační program pomocí **/restart** nebo podobného parametru, který aplikaci upozorní, že se obnovuje, namísto spuštění. Můžete také zahrnout parametry, které označují, kde se nacházíte v procesu instalace, což je zvláště užitečné v instalacích, které mohou vyžadovat více restartování.  
  
 Následující příklad ukazuje hodnotu klíče registru RunOnce pro obnovení instalace.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Instalace dvojitého restartování zaváděcího nástroje  
 Pokud se instalační program používá přímo z RunOnce, plocha se nebude moct úplně načíst. Aby bylo k dispozici úplné uživatelské rozhraní, je nutné vytvořit další spuštění instalačního programu a ukončit instanci RunOnce.  
  
 Musíte znovu spustit instalační program, aby získal správná oprávnění, a musíte mu poskytnout dostatek informací, abyste věděli, kde jste zastavili před restartováním, jak ukazuje následující příklad.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Odstraňuje se ResumeData klíč instalačního programu prostředí  
 Instalační program prostředí nastaví klíč registru HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData s daty, aby se obnovila instalace po restartování. Vzhledem k tomu, že se vaše aplikace, ne Instalační služba prostředí, obnovuje, odstraňte tento klíč registru, jak ukazuje následující příklad.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Restartování systému Windows  
 Po nastavení požadovaných klíčů registru můžete restartovat systém Windows. Následující příklad vyvolá příkazy restartu pro různé operační systémy Windows.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Resetování počáteční cesty MSI  
 Před restartováním je aktuální adresář umístěním instalačního programu, ale po restartování se umístění stalo adresářem System32. Instalační program by měl obnovit aktuální adresář před každým voláním MSI, jak ukazuje následující příklad.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Spuštění MSI aplikace  
 Jakmile instalační program prostředí sady Visual Studio vrátí ERROR_SUCCESS, můžete pro svou aplikaci spustit MSI. Vzhledem k tomu, že instalační program poskytuje uživatelské rozhraní, spusťte soubor MSI v tichém režimu ( **/q**) a pomocí protokolování ( **/l**), jak ukazuje následující příklad.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
