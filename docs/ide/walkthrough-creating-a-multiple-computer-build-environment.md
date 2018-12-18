---
title: 'Návod: Vytvoření prostředí více počítačů sestavení'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2dc88c3861adb8b1d9f239d6ceedee2b76bc2e25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951610"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>Návod: Vytvoření prostředí více počítačů sestavení

Můžete vytvořit prostředí sestavení v rámci organizace nainstalováním sady Visual Studio v hostitelském počítači a následným kopírováním různých souborů a nastavení do jiného počítače tak, aby se mohl podílet na sestavení. Není nutné k instalaci sady Visual Studio na jiném počítači.

Tento dokument neuděluje práva k distribuci softwaru externě, nebo k poskytování prostředí sestavení třetím stranám.

> Právní omezení<br /><br /> Tento dokument je k dispozici na "jako-je" základ. Když jsme otestovali popsané kroky, nepovedlo se nám otestovat vyčerpávajícím způsobem všechny konfigurace. Pokusíme se zachovat dokument aktuální se všemi dalšími informacemi, které se naučili. Informace a názory vyjádřené v tomto dokumentu včetně adres URL a jiných odkazů na internetové weby, mohou změnit bez předchozího upozornění. Společnost Microsoft neposkytuje žádné záruky, vyjádřené nebo předpokládané, s ohledem na uvedené informace. Nesete veškerá rizika s jejich použitím.<br /><br /> Tento dokument neobsahuje jste žádná zákonná práva na duševní vlastnictví produktů společnosti Microsoft. Můžete kopírovat a používat tento dokument pro osobní a referenční účely.<br /><br /> Nemáte žádné závazky poskytovat společnosti Microsoft, máte nějaké návrhy, komentáře ani jinou zpětnou vazbu ("zpětná vazba") týkající se tohoto dokumentu. Žádné dobrovolně poskytnutá zpětná však lze v Microsoft Products a souvisejících specifikacích nebo v jiné dokumentaci (souhrnně "Offerings Microsoft"), které pak mohou spoléhat další třetí strany při vývoji vlastních produktů. Proto pokud dáte Microsoft Feedback na kteroukoli verzi tohoto dokumentu nebo Offerings společnosti Microsoft, ke které se vztahují, vyjadřujete svůj souhlas: (a) společnosti Microsoft mohou volně používat, reprodukovat, licence, distribuovat a jinak komerčně využívat vaše názory ve společnosti Microsoft Nabídkou; (b) je také nutné udělit třetím stranám bez poplatků, pouze ta patentová práva nutná pro povolení jiných produktů pro použití nebo komunikaci s jakoukoli konkrétní částí Microsoft Product, které obsahují vaše zpětná vazba. a (c) vám nebude dát společnosti Microsoft jakoukoli zpětnou vazbu (i), které máte důvod se domnívat, podléhá všechny deklarace identity patentů, o autorských právech nebo jiné duševního vlastnictví nebo práva jakékoli třetí strany; nebo (ii) předmět licenčními podmínkami, které vyžadují žádné začlenění Offering Microsoft se snaží nebo odvozený od těchto zpětnou vazbu nebo jinému duševnímu vlastnictví společnosti Microsoft licencován nebo jinak sdílet s žádnou třetí stranou.

Tento návod byl ověřen pro následující operační systémy:

- Windows 8 (x86 a x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

Po dokončení kroků v tomto podrobném návodu, můžete použít prostředí více počítačů k vytváření těchto druhů aplikací:

- Aplikace klasické pracovní plochy jazyka C++, které používají sadu SDK Windows 8
- Visual Basic nebo C# aplikace klasické pracovní plochy, které se zaměřují na rozhraní .NET Framework 4.5

Prostředí s více počítači nelze použít k vytvoření těchto typů aplikací:

- Aplikace UWP. K vytváření aplikací pro UPW, nainstalujte Visual Studio v počítači sestavení.
- Desktopové aplikace, které jsou cíleny rozhraní .NET Framework 4 nebo dřívější. K vytvoření těchto typů aplikací, musíte nainstalovat Visual Studio nebo odkaz na sestavení rozhraní .NET a nástroje (ze sady Windows SDK 7.1) v počítači sestavení.

## <a name="prerequisites"></a>Požadavky

- Visual Studio s **vývoj desktopových aplikací .NET** nainstalovaná úloha.

## <a name="install-software-on-the-computers"></a>Instalovat software na počítačích

Nejprve nastavte hostitelský počítač a pak znovu nainstalovat na počítač sestavení.

Nainstalováním sady Visual Studio v hostitelském počítači vytvořte soubory a nastavení, které zkopírujete do počítače sestavení později. Visual Studio můžete nainstalovat na x x86 nebo x x64 počítač, ale architektura počítače sestavení musí odpovídat architektuře hostitelského počítače.

1. Na hostitelském počítači nainstalujte Visual Studio.

2. V počítači sestavení nainstalujte rozhraní .NET Framework 4.5 nebo novější. Pokud chcete ověřit, jestli je nainstalovaný, zkontrolujte, že **verze** v podklíči registru položku **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** má hodnotu **4.5** nebo vyšší.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Kopírování souborů z hostitelského počítače do počítače sestavení

Tato část zahrnuje kopírování určitých souborů, kompilátory, nástroje pro vytváření, aktiva MSBuild a nastavení registru z hostitelského počítače do počítače sestavení. Tyto pokyny předpokládají, že jste nainstalovali aplikaci Visual Studio ve výchozím umístění v hostitelském počítači. Pokud jste nainstalovali do jiného umístění, postup odpovídajícím způsobem upravte.

- Na x x86 počítače, výchozí umístění je *C:\Program Files\Microsoft Visual Studio 11.0*
- X x64 počítače, výchozí umístění je *C:\Program Files (x86) \Microsoft Visual Studio 11.0*

Všimněte si, že název *Program Files* složky závisí na operačním systému, který je nainstalován. Na x x86 je název počítače, *Program Files*; x x64 je název počítače, *Program Files (x86)*. Bez ohledu na architekturu systému tento návod odkazuje *Program Files* složky jako *% ProgramFiles %*.

> [!NOTE]
> V počítači sestavení všechny relevantní soubory musí být na stejné jednotce; písmeno jednotky pro tuto jednotku však může být jiné než písmeno jednotky pro jednotku, kde je nainstalovaný Visual Studio v hostitelském počítači. V každém případě musíte vzít v úvahu umístění souborů při vytváření položky registru, jak je popsáno dále v tomto dokumentu.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Kopírování souborů Windows SDK do počítače sestavení

1. Pokud máte pouze Windows SDK pro Windows 8 nainstalované, zkopírujte tyto složky rekurzivně z hostitelského počítače do počítače sestavení:

   - %ProgramFiles%\Windows Kits\8.0\bin\

   - %ProgramFiles%\Windows Kits\8.0\Catalogs\

   - %ProgramFiles%\Windows Kits\8.0\DesignTime\

   - %ProgramFiles%\Windows Kits\8.0\include\

   - %ProgramFiles%\Windows Kits\8.0\Lib\

   - %ProgramFiles%\Windows Kits\8.0\Redist\

   - %ProgramFiles%\Windows Kits\8.0\References\

     Pokud máte také tyto jiné sady Windows 8...

   - Microsoft Windows Assessment and Deployment Kit

   - Microsoft Windows Driver Kit

   - Microsoft Windows Hardware Certification Kit

     .. .mohou mít nainstalovány soubory do *%ProgramFiles%\Windows Kits\8.0* složky, které jsou uvedeny v předchozím kroku a jejich licenční podmínky neumožňují práva sestavení serveru pro tyto soubory. Zkontrolujte licenční podmínky pro každý nainstalovanou sadu SDK Windows k ověření, zda mohou být soubory zkopírovány do počítače sestavení. Pokud licenční podmínky neumožňují práva sestavení serveru, odeberte soubory z počítače sestavení.

2. Zkopírujte následující složky rekurzivně z hostitelského počítače do počítače sestavení:

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\

    - %ProgramFiles%\Common Files\Common Files\Merge Modules\

    - 11.0\VC\ %ProgramFiles%\Microsoft visual Studio

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETFramework\v4.5\

3. Zkopírujte tyto soubory z hostitelského počítače do počítače sestavení:

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\vsvars32.bat

4. Následující knihovny runtime Visual C++ se vyžadují jenom v případě, že spustíte výstupy sestavení na počítači sestavení, například jako součást automatizovaného testování. Soubory jsou obvykle umístěny v podsložkách ve složce *%ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x86* nebo *%ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x64* složce v závislosti na architektuře systému. Na x86 systémy, zkopírujte x86 binární soubory do *Windows\System32* složky. Na x64 systémy, zkopírujte x86 binární soubory do *Windows\SysWOW64* složky a x64 binární soubory *Windows\System32* složky.

    - \Microsoft.VC110.ATL\atl110.dll

    - \Microsoft.VC110.CRT\msvcp110.dll

    - \Microsoft.VC110.CRT\msvcr110.dll

    - \Microsoft.VC110.CXXAMP\vcamp110.dll

    - \Microsoft.VC110.MFC\mfc110.dll

    - \Microsoft.VC110.MFC\mfc110u.dll

    - \Microsoft.VC110.MFC\mfcm110.dll

    - \Microsoft.VC110.MFC\mfcm110u.dll

    - \Microsoft.VC110.MFCLOC\mfc110chs.dll

    - \Microsoft.VC110.MFCLOC\mfc110cht.dll

    - \Microsoft.VC110.MFCLOC\mfc110deu.dll

    - \Microsoft.VC110.MFCLOC\mfc110enu.dll

    - \Microsoft.VC110.MFCLOC\mfc110esn.dll

    - \Microsoft.VC110.MFCLOC\mfc110fra.dll

    - \Microsoft.VC110.MFCLOC\mfc110ita.dll

    - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

    - \Microsoft.VC110.MFCLOC\mfc110kor.dll

    - \Microsoft.VC110.MFCLOC\mfc110rus.dll

    - \Microsoft.VC110.OPENMP\vcomp110.dll

5. Zkopírujte pouze následující soubory z *Debug_NonRedist\x86* nebo *Debug_NonRedist\x64* složky do počítače sestavení, jak je popsáno v [Příprava testovacího počítače ke spuštění spustitelného souboru ladění](/cpp/ide/preparing-a-test-machine-to-run-a-debug-executable). Nelze zkopírovat žádné jiné soubory.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>Vytvoření nastavení registru

Je nutné vytvořit položky registru ke konfiguraci nastavení pro MSBuild.

1. Určení nadřazené složky pro položky registru. Všechny položky registru jsou vytvořeny pod stejným nadřazeným klíčem. Na x x86 je nadřazený klíč počítače, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**. X x64 počítače nadřazený klíč je **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft**. Bez ohledu na architekturu systému tento návod odkazuje na nadřazený klíč jako % RegistryRoot %.

    > [!NOTE]
    > Pokud se architektura hostitelského počítače liší od vašeho počítače sestavení, nezapomeňte použít odpovídající nadřazený klíč na každém počítači. To je obzvláště důležité, pokud používáte automatizaci procesu exportu.
    >
    > Pokud používáte jiné písmeno jednotky v počítači sestavení než ten, který používáte v hostitelském počítači, ujistěte se také, chcete-li změnit hodnoty položek registru tak, aby odpovídaly.

2. Vytvořte následující položky registru v počítači sestavení. Všechny tyto položky jsou řetězce (typ == "REG_SZ" v registru). Nastavte hodnoty těchto položek, které se stejný jako hodnoty srovnatelných položek v hostitelském počítači.

   - **% RegistryRoot %\\. Veřejné Assemblies@(Default) NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild**

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **% RegistryRoot %\VisualStudio\11.0@Source adresáře**

   - <strong>% RegistryRoot %\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>% RegistryRoot %\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>% RegistryRoot %\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>% RegistryRoot %\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>% RegistryRoot %\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **% RegistryRoot %\VisualStudio\SxS\VC7@11.0**

   - **% RegistryRoot %\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Windows Kits\Installed Roots@KitsRoot</strong>

   - <strong>% RegistryRoot %\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>% RegistryRoot %\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>% RegistryRoot %\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   Počítač sestavení x x64, také vytvořte následující položku registru a odkazovat na hostitelském počítači zjistěte, jak ji nastavit.

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   Pokud je počítač sestavení x64 a chcete použít 64bitovou verzi nástroje MSBuild, nebo pokud používáte službu sestavení serveru Team Foundation Server na x x64 počítače, vytvořte následující položky registru v nativním 64bitovém registru. Odkazovat na hostitelském počítači zjistěte, jak nastavit tyto položky.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Nastavení proměnných prostředí v počítači sestavení

Pokud chcete použít nástroj MSBuild v počítači sestavení, musíte nastavit proměnné prostředí PATH. Můžete použít *vcvarsall.bat* k nastavení proměnných, nebo můžete nakonfigurovat ručně.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Nastavení proměnných prostředí pomocí vcvarsall.bat

Otevřít **příkazového řádku** na sestavovacím počítači a spusťte okno *% Program Files%\Microsoft Visual Studio 11.0\VC\vcvarsall.bat*. Argument příkazového řádku můžete použít k určení sady nástrojů, kterou chcete použít – x86, nativní x64 nebo x64 křížový kompilátor. Pokud nezadáte argument příkazového řádku, x86 se sada nástrojů.

V této tabulce jsou uvedeny podporované argumenty pro *vcvarsall.bat*:

|Vcvarsall.bat argument|Kompilátor|Architektura sestavovacího počítače|Architektura výstupu sestavení|
| - |--------------| - | - |
|x86 (výchozí)|32bitová nativní|x86, x64|x86|
|x86_amd64|x64 křížové|x86, x64|x64|
|amd64|x64 nativní|x64|x64|

Pokud *vcvarsall.bat* proběhne úspěšně – tedy žádná chybová zpráva se zobrazí – můžete následující krok přeskočit a pokračovat na [sestavení nainstalovat nástroje MSBuild k globální mezipaměti sestavení (GAC) v počítači sestavení](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)část tohoto dokumentu.

### <a name="manually-set-environment-variables"></a>Ruční nastavení proměnných prostředí

1. Chcete-li ručně konfigurovat prostředí příkazového řádku, přidáte tuto cestu do proměnné prostředí PATH:

    - % Program Files%\Microsoft Visual Studio 11.0\Common7\IDE

2. Volitelně můžete také přidat následující cesty do proměnné PATH, aby bylo snazší používat nástroj MSBuild pro vytváření řešení.

   Pokud chcete použít nativní 32bitový MSBuild, přidejte tyto cesty do proměnné PATH:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 nástroje

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   Pokud chcete použít nativní 64bitový MSBuild, přidejte tyto cesty do proměnné PATH:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a>Instalace sestavení nástroje MSBuild k globální mezipaměti sestavení (GAC) v počítači sestavení

Nástroj MSBuild vyžaduje některých dalších sestavení nainstalovaná v GAC v počítači sestavení.

1. Kopírování následujících sestavení z hostitelského počítače do počítače sestavení. Vzhledem k tomu, že se nainstalují do mezipaměti GAC, nezáleží, kde je umístíte v počítači sestavení.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Chcete-li nainstalovat sestavení do mezipaměti GAC, vyhledejte *gacutil.exe* v počítači sestavení – obvykle je to v %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 nástroje\\. Pokud tuto složku nemůžete najít, opakujte kroky v [kopírování souborů z hostitelského počítače do počítače sestavení](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) části tohoto názorného postupu.

     Otevřít **příkazového řádku** okna, který má práva správce a spusťte tento příkaz u každého souboru:

     **Gacutil -i \<souboru >**

    > [!NOTE]
    > Restartování může být vyžadováno pro sestavení plně nainstalovalo do GAC.

## <a name="build-projects"></a>Sestavení projektů

Kanály Azure můžete použít k sestavení řešení a projektů sady Visual Studio, nebo je můžete vytvořit na příkazovém řádku. Pokud používáte kanály Azure k sestavení projektů, vyvolá spustitelný soubor MSBuild, který odpovídá architektuře systému. Na příkazovém řádku můžete použít 32bitový nástroj MSBuild nebo 64bitový MSBuild a můžete zvolit architekturu nástroje MSBuild nastavením proměnné prostředí PATH nebo přímo vyvoláním spustitelného souboru specifického pro architekturu MSBuild.

Chcete-li použít *msbuild.exe* na příkazovém řádku spusťte následující příkaz, ve kterém *solution.sln* je zástupný symbol pro název vašeho řešení.

**Nástroj MSBuild** *solution.sln*

Další informace o tom, jak používat MSBuild na příkazovém řádku naleznete v tématu [odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Vytvořit prostředí sestavení tak, aby mohla být zařazena do správy zdrojového kódu

Můžete vytvořit prostředí sestavení, který je možné nasadit na různých počítačích a nevyžaduje soubory "GAC"-ing ani změny nastavení registru. Následující kroky jsou jen jedním ze způsobů jak toho dosáhnout. Přizpůsobit tento postup na jedinečné znaky prostředí sestavení.

> [!NOTE]
> Musíte zakázat přírůstkové sestavování tak, aby *tracker.exe* nevyvolala chybu během sestavení. Chcete-li zakázat přírůstkové sestavování, nastavte tento parametr sestavení:
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. Vytvoření *Depot* adresáře v hostitelském počítači.

     Tyto kroky odkazují na adresář jako % Depot %.

2. Kopírování adresářů a souborů, jak je popsáno v [kopírování souborů z hostitelského počítače do počítače sestavení](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) části tohoto názorného postupu, s výjimkou jejich pod vložení *% Depot %* adresář, který jste právě vytvořit. Například zkopírujte z *%ProgramFiles%\Windows Kits\8.0\bin* k *%Depot%\Windows Kits\8.0\bin*.

3. Když jsou soubory vloženy do *% Depot %*, proveďte tyto změny:

    - V % Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\a \Microsoft.CppCommon.targets\\, změňte každou instanci z

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, verze = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         až

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         Dřívější pojmenování je založena na sestavení GAC.

    - V % Depot % \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets změňte každou instanci

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, verze = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         až

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. Vytvoření *.props* souboru – například *Partner.AutoImports.props*– a vložit ho do kořenové složky, která obsahuje vaše projekty. Tento soubor slouží k nastavení proměnné, které jsou používány nástrojem MSBuild k vyhledávání různých zdrojů. Pokud proměnné nejsou nastaveny tímto souborem, jsou nastaveny v jiných *.props* soubory a *.targets* soubory, které spoléhají na hodnoty registru. Protože nenastavujeme žádné hodnoty registru, tyto proměnné budou prázdné a sestavení selže. Místo toho přidejte sem *Partner.AutoImports.props*:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. V každém ze souborů projektu přidejte následující řádek nahoře, za `<Project Default Targets...>` řádku.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

6. Změna prostředí příkazového řádku takto:

    - Nastavte Depot =*umístění Depot adresáře, který jste vytvořili v kroku 1*

    - Nastavení cesty k = % path %; *umístění nástroje MSBuild v počítači*; %D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D 15.0\Common7\IDE\ epot%\Microsoft sady Visual Studio

       Pro nativní 64bitové sestavení přejděte na 64bitový MSBuild.

## <a name="see-also"></a>Viz také:

- [Příprava testovacího počítače ke spuštění ladicího spustitelného souboru](/cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)
- [Odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md)