---
title: Instalace aplikací izolovaného prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ecec7963b66c20ef08d1e5f3f0917a66f885aa0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796301"
---
# <a name="installing-an-isolated-shell-application"></a>Instalace aplikací izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K instalaci prostředí aplikace musíte provést následující kroky.  
  
- Příprava vašeho řešení.  
  
- Vytvoření balíčku Instalační služby systému Windows (MSI) pro vaši aplikaci.  
  
- Vytvoření nastavení zaváděcí nástroj.  
  
  Kód příkladu v tomto dokumentu se segmenty Convenience [prostředí nasazení ukázky](http://go.microsoft.com/fwlink/?LinkId=262245), kterou si můžete stáhnout z Galerie kódu na webu MSDN. Vzorek ukazuje výsledky provedení jednotlivých kroků.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li provádět postupy, které toto téma popisuje, musí být v počítači nainstalované následující nástroje.  
  
- Visual Studio SDK  
  
- [Sady nástrojů XML Instalační služby systému Windows](http://go.microsoft.com/fwlink/?LinkId=82720) verze 3.6  
  
  Ukázka vyžaduje také Microsoft Visualization and Modeling SDK, které vyžadují některé prostředí.  
  
## <a name="preparing-your-solution"></a>Příprava vašeho řešení  
 Ve výchozím prostředí šablony sestavení do balíčků VSIX, ale toto chování je určená primárně pro účely ladění. Při nasazení aplikace v jazyce Shell, musíte použít balíčky MSI umožňuje pro přístup k registru a restartování během instalace. Příprava aplikace pro nasazení MSI, proveďte následující kroky.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Příprava aplikace prostředí pro nasazení Instalační služby MSI  
  
1.  Upravte každý soubor .vsixmanifest ve vašem řešení.  
  
     V `Identifier` element, přidejte `InstalledByMSI` elementu a `SystemComponent` prvek a nastavte jejich hodnoty na `true`.  
  
     Tyto prvky zabránit pokusu o instalaci komponenty a uživatele z jejich odinstalace s použitím instalátor VSIX **rozšíření a aktualizace** dialogové okno.  
  
2.  Pro každý projekt, který obsahuje VSIX manifest upravte úlohy sestavení do výstupního obsahu do umístění, ze kterého se nainstaluje vaše MSI. Ve výstupu sestavení obsahovat VSIX manifest, ale nevytvářejte soubor VSIX.  
  
## <a name="creating-an-msi-for-your-shell"></a>Vytváří se soubor MSI pro vaše prostředí  
 K vytvoření vašeho balíčku MSI, doporučujeme použít [sady nástrojů XML Instalační služby systému Windows](http://go.microsoft.com/fwlink/?LinkId=82720) protože nabízí větší flexibilitu než standardní projektu instalace.  
  
 V souboru Product.wxs nastavte bloky detekce a rozložení součásti prostředí.  
  
 V souboru .reg pro vaše řešení a v ApplicationRegistry.wxs vytvořte položky registru.  
  
### <a name="detection-blocks"></a>Detekce bloky  
 Detekce bloku se skládá z `Property` prvek, který určuje předpokladem pro zjišťování a `Condition` prvek, který určuje zprávu, která vrátí, pokud není k dispozici v počítači kontrolu požadovaných součástí. Například aplikace prostředí bude vyžadovat Microsoft prostředí sady Visual Studio distribuovatelné součásti a blok zjišťování bude vypadat podobně jako následující kód.  
  
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
 Je nutné přidat prvky k identifikaci cílové adresářovou strukturu a součástí k instalaci.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Nastavit rozložení součásti prostředí  
  
1.  Vytvořit hierarchii `Directory` prvky představující všechny adresáře vytvořit v systému souborů na cílovém počítači, jak ukazuje následující příklad.  
  
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
  
     Tyto adresáře jsou označovány `Id` při zadané soubory, které musí být nainstalována.  
  
2.  Určete součásti, které prostředí a aplikace prostředí vyžaduje jako v následujícím příkladu.  
  
    > [!NOTE]
    >  Některé prvky mohou odkazovat na definice v jiných souborech WXS.  
  
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
  
    1.  `ComponentRef` Element odkazuje na jiný soubor WXS, který označuje soubory, které vyžaduje aktuální komponenty. Například GeneralProfile má následující definice v HelpAbout.wxs.  
  
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
  
         `DirectoryRef` Element určuje, kde se tyto soubory přejděte v počítači uživatele. `Directory` Element určuje, že se nainstaluje do podadresáře a pro každou `File` element představuje soubor, který je sestaven nebo, který existuje v rámci tohoto řešení a identifikuje, ve kterém tento soubor můžete najít při vytvoření souboru Instalační služby MSI.  
  
    2.  `ComponentGroupRef` Element odkazuje skupina jiných součástí (nebo komponenty a skupiny součástí). Například `ComponentGroupRef` pod proměnná je definovaná následujícím způsobem v Application.wxs.  
  
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
    >  Požadované závislosti pro aplikace prostředí Shell (izolovaný režim) jsou: DebuggerProxy MasterPkgDef, prostředky (hlavně soubor .winprf), aplikace a PkgDefs.  
  
### <a name="registry-entries"></a>Položky registru  
 Šablona projektu Shell (izolovaný režim) obsahuje *ProjectName*soubor .reg pro klíče registru na sloučení na instalaci. Tyto položky registru musí být součástí MSI pro účely čištění a instalaci. Musíte taky vytvořit odpovídající bloky registru v ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>K integraci položky registru do MSI  
  
1.  V **přizpůsobení prostředí** složku, otevřete *ProjectName*. reg.  
  
2.  Nahraďte všechny výskyty $RootFolder$ token s cestou cílový adresář instalace.  
  
3.  Přidejte další položky registru, které vaše aplikace vyžaduje.  
  
4.  Otevřete ApplicationRegistry.wxs.  
  
5.  Pro každou položku registru v *ProjectName*.reg, přidejte odpovídající blok registru, jako následující příklady ukazují.  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "Objekt PhotoStudio DTE"|\<Klíče registru Id = "DteClsidRegKey" Root "HKCR" klíč = = "$(var. DteClsidRegKey) "akce ="createAndRemoveOnUninstall"><br /><br /> \<Hodnota RegistryValue typ = "řetězec" Name = "@" hodnota = "$(var. Objekt ShortProductName) DTE "/ ><br /><br /> \</ Klíč registru >|  
    |[HKEY_CLASSES_ROOT\CLSID\\\LocalServer32 {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "$RootFolder$\PhotoStudio.exe"|\<Klíče registru Id = "DteLocSrv32RegKey" Root "HKCR" klíč = = "$(var. DteClsidRegKey) \LocalServer32 "akce ="createAndRemoveOnUninstall"><br /><br /> \<Hodnota RegistryValue typ = "řetězec" Name = "@" hodnota = "[INSTALLDIR] $(var. ShortProductName) .exe "/ ><br /><br /> \</ Klíč registru >|  
  
     V tomto příkladu překládá Var.DteClsidRegKey ke klíči registru do horního řádku. Var.ShortProductName přeloží na `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Vytvoření nastavení zaváděcí nástroj  
 Dokončené MSI se nainstaluje jenom v případě, že všechny požadované součásti jsou nainstalována jako první. K usnadnění činnost koncového uživatele, vytvořte instalační program, který shromažďuje a nainstaluje všechny požadované součásti před instalací aplikace. Aby se zajistilo úspěšné instalaci, proveďte tyto akce:  
  
-   Vynuťte instalaci správcem.  
  
-   Zjištění, zda je nainstalována aplikace Visual Studio Shell (izolovaný režim).  
  
-   Spuštění prostředí pro jeden nebo oba instalační programy v pořadí.  
  
-   Zpracujte požadavky na restartování.  
  
-   Spusťte vaše MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Vynucování instalace správcem  
 Tento postup je potřeba povolit instalační program pro přístup k požadované adresáře, jako je například \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Vynutit instalaci správcem  
  
1.  Otevřete místní nabídku pro projekt instalace a klikněte na tlačítko **vlastnosti**.  
  
2.  V části **konfigurační vlastnosti/Linkeru/Manifest soubor**, nastavte **úroveň spuštění nástroje Řízení uživatelských účtů** k **requireAdministrator**.  
  
     Tato vlastnost vloží atributu, který vyžaduje, aby program spustit jako správce do vloženého souboru manifestu.  
  
### <a name="detecting-shell-installations"></a>Detekce instalace prostředí  
 Pokud chcete zjistit, jestli se musí nainstalovat Visual Studio Shell (izolovaný režim), nejprve určete, zda je již nainstalován kontrolou hodnotu registru HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Tyto hodnoty jsou také číst detekce blok prostředí v Product.wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder Určuje umístění, kde byl nainstalován prostředí sady Visual Studio a můžete zkontrolovat soubory.  
  
 Příklad toho, jak detekce instalace prostředí, najdete v článku `GetProductDirFromReg` funkce Utilities.cpp v ukázce prostředí nasazení.  
  
 Pokud jeden nebo oba z prostředí Visual Studio, které vyžaduje váš balíček není nainstalovaný na počítači, musíte je přidat na seznam součástí k instalaci. Příklad najdete v tématu `ComponentsPage::OnInitDialog` funkce ComponentsPage.cpp v ukázce prostředí nasazení.  
  
### <a name="running-the-shell-installers"></a>Spuštění instalační programy prostředí  
 Pokud chcete spustit prostředí instalační programy, volání distribuovatelné součásti Visual Studio Shell pomocí správné argumenty příkazového řádku. Minimálně je nutné použít argumenty příkazového řádku **/q/norestart /** a podívejte se pro návratový kód, chcete-li zjistit, co by měl třeba udělat jako další. Následující příklad spustí Shell (izolovaný režim) redistributable.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Spuštění instalační programy Shell Language Pack  
 Pokud zjistíte, že byly nainstalovány prostředí nebo prostředí a potřebujete pouze jazyk pack místo toho, jak ukazuje následující příklad můžete nainstalovat jazykové sady.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Určité návratové hodnoty  
 U některých operačních systémů instalace Visual Studio Shell (izolovaný režim) bude vyžadovat restartování. Tento stav se dají určit pomocí návratový kód volání `ExecCmd`.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|ERROR_SUCCESS|Instalace byla dokončena. Nyní můžete nainstalovat aplikaci.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Instalace byla dokončena. Aplikaci můžete nainstalovat po restartování počítače.|  
|3015|Probíhá instalace. Pokračování instalace vyžaduje restart počítače.|  
  
### <a name="handling-restarts"></a>Zpracování restartování  
 Když jste spustili instalační program prostředí pomocí **/norestart /** , je zadán argument, který nebude restartovat počítač, nebo požádat o restartování počítače. Však může být vyžadováno restartování, a ujistěte se, že instalační program bude pokračovat po restartování počítače.  
  
 Správně zpracovávat restartování, ujistěte se, že pouze jeden instalační program je sada pokračovat a správně zpracovat proces obnovení.  
  
 Pokud ERROR_SUCCESS_REBOOT_REQUIRED nebo 3015 se vrátí, váš kód by měl restart počítače, než bude instalace pokračovat.  
  
 Ke zpracování se restartuje, proveďte tyto akce:  
  
-   Nastavení registru a při spuštění Windows pokračovat instalace.  
  
-   Proveďte restart double zaváděcího nástroje.  
  
-   Odstraňte klíč ResumeData prostředí Instalační služby.  
  
-   Restartujte Windows.  
  
-   Obnovení počáteční cesty MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Nastavení registru, aby při spuštění Windows pokračovat v instalaci  
 Klíč registru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ spustí při spuštění systému s oprávněními správce a pak se vymažou. HKEY_CURRENT_USER obsahuje podobné klíč, ale běží v režimu normálního uživatele a není vhodná pro zařízení. Instalace může pokračovat vložením řetězcovou hodnotu v RunOnce klíč, který volá vaše instalační služby. Doporučujeme však volat instalační služba prostřednictvím **/restartuje** nebo podobně jako parametr, aby aplikaci oznámilo, že je obnovení místo spuštění. Můžete použít také parametry k označení, kde se v procesu instalace, což se hodí hlavně v zařízení, které mohou vyžadovat vícenásobné restartování.  
  
 Následující příklad ukazuje RunOnce registru hodnotu klíče pro obnovení činnosti instalace.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Instalace Double restartování zaváděcího nástroje  
 Pokud se instalační program používá přímo z RunOnce, nepůjde na plochu úplné načtení. Chcete-li k dispozici úplné uživatelské rozhraní, musíte vytvořit jiné spuštění instalačního programu a ukončení RunOnce instance.  
  
 Instalační program musí spustit znovu tak, aby získá správná oprávnění a se musí poskytnout dostatek informací, které vědět, kde jste přestali před restartováním počítače, jak ukazuje následující příklad.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Odstraňuje se klíč ResumeData prostředí instalačního programu  
 Instalační program prostředí nastaví klíč registru HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData s daty a pokračovat v instalaci po restartování. Protože obnovení vaší aplikace, ne prostředí instalačního programu, odstraňte tento klíč registru, jako v následujícím příkladu.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Restartování Windows  
 Jakmile nastavíte požadované klíče registru, můžete restartovat Windows. Následující příklad popisuje vyvolání restartování příkazů pro různé operační systémy Windows.  
  
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
  
### <a name="resetting-the-start-path-of-msi"></a>Resetuje se cesta spuštění Instalační služby MSI  
 Před restartováním aktuální adresář je umístění instalačního programu, ale po restartování, umístění bude adresáři system32. Instalační program by měl obnovit aktuální adresář před každým voláním MSI, jak ukazuje následující příklad.  
  
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
  
### <a name="running-the-application-msi"></a>Spuštění aplikace MSI  
 Po návratu ERROR_SUCCESS instalační program prostředí sady Visual Studio můžete spustit soubor MSI pro vaši aplikaci. Vzhledem k tomu, že instalační program poskytuje uživatelské rozhraní, spusťte váš MSI v tichém režimu (**/q**) a s protokolováním (**/L**), jak ukazuje následující příklad.  
  
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

