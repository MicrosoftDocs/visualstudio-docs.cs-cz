---
title: Vytvoření prostředí pro sestavení s použitím více počítačů
description: Vytvořte prostředí sestavení v rámci vaší organizace tak, že nainstalujete Visual Studio na hostitelský počítač a potom zkopírujete různé soubory a nastavení do jiného počítače.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c8fa7756763a668f6e97d90d8a405c660519189
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136950"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>Návod: Vytvoření prostředí pro sestavení s použitím více počítačů

Prostředí sestavení v rámci vaší organizace můžete vytvořit tak, že nainstalujete Visual Studio na hostitelský počítač a potom zkopírujete různé soubory a nastavení do jiného počítače, aby se mohl zúčastnit sestavení. Nemusíte instalovat Visual Studio na druhý počítač.

Tento dokument nemá oprávnění k distribuci softwaru externě nebo k poskytování prostředí buildu třetím stranám.

> Disclaimer<br /><br /> Tento dokument je k dispozici na bázi "tak, jak je". I když jsme otestovali popsané kroky, nemůžeme provést vyzkoušení všech konfigurací. Pokusíme se zachovat aktuální dokument s dalšími informacemi, které se naučily. Informace a názory vyjádřené v tomto dokumentu, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění. Microsoft neposkytuje žádné záruky, výslovné ani předpokládané, týkající se zde uváděných informací. Riziko spojené s jejich použitím nesete vy.<br /><br /> Tímto dokumentem nevzniká právní nárok na duševní vlastnictví produktů Microsoftu. Dokument můžete kopírovat a používat pro svou vnitřní potřebu nebo jako referenci.<br /><br /> Nemáte žádné povinnosti poskytovat Microsoftu žádné návrhy, komentáře ani jinou zpětnou vazbu ("zpětná vazba") týkající se tohoto dokumentu. Veškerá zpětná vazba, kterou jste dobrovolně poskytnete, ale můžete použít v produktech Microsoftu a souvisejících specifikacích nebo v jiné dokumentaci (souhrnně "nabídky Microsoftu"), na které se zase můžou spoléhat jiné třetí strany na vývoj svých vlastních produktů. Pokud tedy poskytnete zpětnou vazbu Microsoftu k jakékoli verzi tohoto dokumentu nebo nabídky Microsoftu, na které se vztahují, souhlasíte: (a) Společnost Microsoft může volně používat, reprodukována, licencovat a jinak obchodně využívat vaše názory v jakékoli nabídce Microsoftu; (b) udělujete také třetím stranám, aniž byste museli účtovat pouze ta patentová práva, která jsou nutná k tomu, aby mohly jiné produkty využívat nebo používat rozhraní s konkrétními částmi produktu společnosti Microsoft, které zahrnují váš názor. a (c) společnosti Microsoft neposkytnete žádnou zpětnou vazbu (i), že máte důvod na to, že podléhají všem patentům, autorským právům a jiným nárokům na duševní vlastnictví nebo právo jakékoli třetí strany. nebo (II) v souladu s licenčními podmínkami, které mají za cíl vyžadovat jakoukoli nabídku Microsoftu, která zahrnuje nebo odvozují tuto zpětnou vazbu nebo jinou duševní vlastnictví Microsoftu, aby byla licencovaná nebo jinak sdílená s kteroukoli třetí stranou.

Tento názorný postup byl ověřen v následujících operačních systémech:

- Windows 8 (x86 a x64)
- Systém Windows 7 Ultimate
- Windows Server 2008 R2 Standard

Po dokončení kroků v tomto návodu můžete k sestavování těchto typů aplikací použít prostředí pro více počítačů:

- Desktopové aplikace C++, které používají sadu Windows 8 SDK
- Visual Basic nebo aplikace klasické pracovní plochy v jazyce C#, které cílí na .NET Framework 4,5

Prostředí s více počítači se nedá použít k sestavování těchto typů aplikací:

- Aplikace pro UWP Chcete-li vytvářet aplikace UWP, je nutné nainstalovat aplikaci Visual Studio do počítače sestavení.
- Aplikace klasické pracovní plochy, které cílí na .NET Framework 4 nebo starší. Chcete-li vytvořit tyto typy aplikací, je nutné nainstalovat aplikaci Visual Studio nebo referenční sestavení a nástroje .NET (ze sady Windows 7,1 SDK) na počítač sestavení.

## <a name="prerequisites"></a>Předpoklady

Visual Studio s nainstalovanou úlohou **vývoj desktopových aplikací .NET**

## <a name="install-software-on-the-computers"></a>Instalace softwaru do počítačů

Nejdřív nastavte hostitelský počítač a pak nastavte počítač pro sestavení.

Instalací sady Visual Studio v hostitelském počítači vytvoříte soubory a nastavení, které zkopírujete do počítače sestavení později. Sadu Visual Studio můžete nainstalovat na počítač s procesorem x86 nebo x64, ale architektura sestavení počítače musí odpovídat architektuře hostitelského počítače.

1. V hostitelském počítači nainstalujte Visual Studio.

2. V počítači sestavení nainstalujte .NET Framework 4,5 nebo novější. Chcete-li ověřit, zda je aplikace nainstalována, zkontrolujte, zda položka **verze** v podklíči registru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** má hodnotu **4,5** nebo vyšší.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Kopírovat soubory z hostitelského počítače do počítače sestavení

Tato část popisuje kopírování konkrétních souborů, kompilátorů, nástrojů sestavení, prostředků MSBuild a nastavení registru z hostitelského počítače na počítač sestavení. Tyto pokyny předpokládají, že jste nainstalovali aplikaci Visual Studio ve výchozím umístění v hostitelském počítači. Pokud jste nainstalovali v jiném umístění, upravte kroky odpovídajícím způsobem.

- V počítači x86 je výchozí umístění *C:\Program Files\Microsoft Visual Studio* .
- V počítači x64 je výchozí umístění *C:\Program Files (x86) \Microsoft Visual Studio*

Všimněte si, že název složky *Program Files* závisí na operačním systému, který je nainstalován. V počítači x86 je názvem *Program Files*; v počítači x64 je název *Program Files (x86)*. Bez ohledu na architekturu systému tento návod odkazuje na složku *Program Files* jako *% ProgramFiles%*.

> [!NOTE]
> V počítači sestavení musí být všechny relevantní soubory na stejné jednotce. Písmeno jednotky pro tuto jednotku však může být jiné než písmeno jednotky pro jednotku, na které je nainstalována aplikace Visual Studio v hostitelském počítači. V každém případě je nutné při vytváření položek registru, které jsou popsány dále v tomto dokumentu, brát v úvahu umístění souborů.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Zkopírování souborů Windows SDK do počítače sestavení

1. Pokud máte nainstalováno pouze Windows SDK pro systém Windows 8, zkopírujte tyto složky rekurzivně z hostitelského počítače do počítače sestavení:

   - %ProgramFiles%\Windows Kits\8.0\bin\

   - %ProgramFiles%\Windows Kits\8.0\Catalogs\

   - %ProgramFiles%\Windows Kits\8.0\DesignTime\

   - %ProgramFiles%\Windows Kits\8.0\include\

   - %ProgramFiles%\Windows Kits\8.0\Lib\

   - %ProgramFiles%\Windows Kits\8.0\Redist\

   - %ProgramFiles%\Windows Kits\8.0\References\

   Pokud máte také tyto další sady Windows 8...

   - Sada Microsoft Windows Assessment and Deployment Kit

   - Sada ovladačů Microsoft Windows

   - Hardwarová Certifikační sada Microsoft Windows

   ... můžou mít nainstalované soubory do složek *Kits\8.0%programfiles%\Windows* , které jsou uvedené v předchozím kroku, a jejich licenčních podmínek nemusí pro tyto soubory umožňovat oprávnění sestavení-Server. Zkontrolujte licenční smlouvy pro všechny nainstalované sady Windows a ověřte, zda mohou být soubory zkopírovány do počítače sestavení. Pokud licenční smlouva nepovoluje práva k sestavení a serveru, odeberte soubory z počítače sestavení.

2. Zkopírujte následující složky rekurzivně z hostitelského počítače do počítače sestavení:

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Tools \

    - Files\Merge moduly pro%ProgramFiles%\Common \

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework \\ . NETCore\v4.5\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework \\ . NETFramework\v4.5\

3. Zkopírujte tyto soubory z hostitelského počítače do počítače sestavení:

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\vsvars32.bat

4. Následující knihovny modulu runtime Visual C++ jsou požadovány pouze v případě, že spustíte výstupy sestavení na počítači sestavení – například jako součást automatického testování. Soubory jsou obvykle umístěny v podsložkách složky *%ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\redist\x86* nebo *%ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\redist\x64* , v závislosti na architektuře systému. V systémech x86 zkopírujte binární soubory x86 do složky *Windows\System32* . V systémech x64 zkopírujte binární soubory x86 do složky *Windows\SysWOW64* a binární soubory x64 do složky *Windows\System32* .

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

5. Zkopírujte pouze následující soubory ze složky *Debug_NonRedist \x86* nebo *Debug_NonRedist \x64* do počítače sestavení, jak je popsáno v tématu [Příprava testovacího počítače ke spuštění ladicího spustitelného souboru](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable). Žádné jiné soubory nelze zkopírovat.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>Vytvořit nastavení registru

Je nutné vytvořit položky registru ke konfiguraci nastavení pro MSBuild.

1. Identifikujte nadřazenou složku pro položky registru. Všechny položky registru se vytvoří pod stejným nadřazeným klíčem. V počítači x86 je nadřazený klíč **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**. V počítači x64 je nadřazený klíč **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft**. Bez ohledu na architekturu systému tento návod odkazuje na nadřazený klíč jako% RegistryRoot%.

    > [!NOTE]
    > Pokud se architektura hostitelského počítače liší od počítače sestavení, nezapomeňte použít příslušný nadřazený klíč na každém počítači. To je obzvláště důležité, pokud automatizujete proces exportu.
    >
    > Pokud používáte jiné písmeno jednotky v počítači sestavení, než je ten, který používáte v hostitelském počítači, nezapomeňte změnit hodnoty položek registru tak, aby odpovídaly.

2. Vytvořte následující položky registru v počítači sestavení. Všechny tyto položky jsou řetězce (Type = = "REG_SZ" v registru). Hodnoty těchto položek nastavte stejně jako hodnoty srovnatelných položek v hostitelském počítači.

   - **% RegistryRoot% \\ . NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild veřejné Assemblies@ (výchozí)**

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **% RegistryRoot% \VisualStudio\11.0@Source adresářů**

   - <strong>%RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **%RegistryRoot%\VisualStudio\SxS\VC7@11.0**

   - **%RegistryRoot%\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Windows Kits\Installed Roots@KitsRoot</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   V počítači sestavení x64 vytvořte také následující položku registru a zjistěte, jak ji nastavit, v hostitelském počítači.

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   Pokud je počítač sestavení x64 a chcete použít 64 verzi nástroje MSBuild, nebo pokud používáte Team Foundation Server službu sestavení v počítači x64, vytvořte v nativním 64 bitovém registru následující položky registru. Chcete-li určit, jak tyto položky nastavit, přečtěte si hostitelský počítač.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Nastavení proměnných prostředí v počítači sestavení

Chcete-li použít nástroj MSBuild v počítači sestavení, je nutné nastavit proměnné prostředí PATH. K nastavení proměnných můžete použít *vcvarsall.bat* , nebo je můžete nakonfigurovat ručně.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Nastavení proměnných prostředí pomocí vcvarsall.bat

Otevřete okno **příkazového řádku** v počítači sestavení a spusťte *% Program Files%\Microsoft Visual Studio \\ \<version> \\ \<edition>\VC\vcvarsall.bat*. Argument příkazového řádku můžete použít k určení sady nástrojů, kterou chcete použít – x86, Native x64 nebo x64 pro více kompilátorů. Pokud nezadáte argument příkazového řádku, bude použita sada nástrojů x86.

Tato tabulka popisuje podporované argumenty pro *vcvarsall.bat*:

|Argument Vcvarsall.bat|Compiler|Architektura sestavení počítače|Architektura výstupu sestavení|
| - |--------------| - | - |
|x86 (výchozí)|32 – bit Native|x86, x64|x86|
|x86_amd64|x64 – křížení|x86, x64|x64|
|amd64|Nativní verze x64|x64|x64|

Pokud se *vcvarsall.bat* spustí úspěšně – to znamená, že se nezobrazí žádná chybová zpráva – můžete přeskočit další krok a pokračovat v [instalaci sestavení MSBuild do globální mezipaměti sestavení (GAC) v](#install-msbuild-to-gac) tomto dokumentu v části sestavení nástroje MSBuild.

### <a name="manually-set-environment-variables"></a>Ruční nastavení proměnných prostředí

1. Chcete-li ručně nakonfigurovat prostředí příkazového řádku, přidejte tuto cestu do proměnné prostředí PATH:

    - % Program Files%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\IDE

2. Volitelně můžete také přidat následující cesty do proměnné PATH, abyste usnadnili použití nástroje MSBuild k sestavení vašich řešení.

   Pokud chcete použít nativní 32 MSBuild, přidejte tyto cesty do proměnné PATH:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 – nástroje

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   Pokud chcete použít nativní 64 MSBuild, přidejte tyto cesty do proměnné PATH:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" /> Nainstalovat sestavení nástroje MSBuild do globální mezipaměti sestavení (GAC) v počítači sestavení

Nástroj MSBuild vyžaduje, aby byla do GAC v počítači sestavení nainstalována nějaká další sestavení.

1. Zkopírujte následující sestavení z hostitelského počítače do počítače sestavení. Protože budou nainstalovány do mezipaměti GAC, nezáleží na tom, kde je umístíte do počítače sestavení.

    - % ProgramFiles% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Chcete-li nainstalovat sestavení do globální mezipaměti sestavení (GAC), vyhledejte *gacutil.exe* v počítači sestavení – obvykle se jedná o nástroje%programfiles%\microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 \\ . Pokud tuto složku nemůžete najít, opakujte postup v části [kopírování souborů z hostitelského počítače do počítače sestavení](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) tohoto návodu.

     Otevřete okno **příkazového řádku** , které má oprávnění správce, a spusťte tento příkaz pro každý soubor:

     **Gacutil – i \<file>**

    > [!NOTE]
    > Může být vyžadován restart pro sestavení k úplné instalaci do globální mezipaměti sestavení (GAC).

## <a name="build-projects"></a>Sestavit projekty

Můžete použít Azure Pipelines k sestavení projektů a řešení v aplikaci Visual Studio nebo je můžete sestavit na příkazovém řádku. Když použijete Azure Pipelines k sestavení projektů, vyvolá spustitelný soubor MSBuild, který odpovídá architektuře systému. Na příkazovém řádku můžete použít buď 32 nástroje MSBuild nebo 64 nástroje MSBuild, a můžete zvolit architekturu nástroje MSBuild nastavením proměnné prostředí PATH nebo přímo vyvoláním spustitelného souboru nástroje MSBuild pro konkrétní architekturu.

Chcete-li použít *msbuild.exe* na příkazovém řádku, spusťte následující příkaz, ve kterém *Solution. sln* je zástupný symbol pro název vašeho řešení.

řešení **MSBuild** *. sln*

Další informace o použití nástroje MSBuild na příkazovém řádku naleznete v tématu Reference k [příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Vytvořte prostředí sestavení tak, aby bylo možné ho zkontrolovat do správy zdrojového kódu.

Můžete vytvořit sestavovací prostředí, které lze nasadit do různých počítačů a nevyžaduje "GAC"-navýšení souborů nebo úpravy nastavení registru. Následující kroky jsou pouze jedním ze způsobů, jak to provést. Přizpůsobte tyto kroky na jedinečné charakteristiky prostředí sestavení.

> [!NOTE]
> Je nutné zakázat přírůstkové sestavování, aby *tracker.exe* při sestavování nevyvolaly chybu. Chcete-li zakázat přírůstkové sestavování, nastavte tento parametr sestavení:
>
> **msbuild** *řešení MSBuild. sln* **/p: TrackFileAccess = false**

1. Vytvořte adresář *skladu* v hostitelském počítači.

     Tyto kroky odkazují na adresář jako na sklad%.

2. Zkopírujte adresáře a soubory, jak je popsáno v části [kopírování souborů z hostitelského počítače do počítače sestavení](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) v tomto návodu, s výjimkou jejich vložení do adresáře *% skladu%* , který jste právě vytvořili. Například zkopírujte z *%programfiles%\Windows Kits\8.0\Bin* na *%Depot%\Windows Kits\8.0\Bin*.

3. Když jsou soubory vloženy do *% skladu%*, proveďte tyto změny:

    - V%Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets \\ , \Microsoft.cppbuild.targets \\ a \Microsoft.CppCommon.targets \\ změňte všechny instance

         AssemblyName = "Microsoft. Build. CppTasks. Common. v110, verze = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         na

         AssemblyFile = "$ (VCTargetsPath11) Microsoft.Build.CppTasks.Common.v110.dll".

         Předchozí pojmenování spoléhá na sestavení, které se GAC'ed.

    - V% skladu% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets změňte všechny instance

         AssemblyName = "Microsoft. Build. CppTasks. Common. v110, verze = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         na

         AssemblyFile = "$ (VCTargetsPath11) Microsoft.Build.CppTasks.Common.v110.dll".

4. Vytvořte soubor *. props* – například *partner. AutoImports. props*– a vložte ho do kořenové složky, která obsahuje vaše projekty. Tento soubor slouží k nastavení proměnných používaných nástrojem MSBuild k nalezení různých prostředků. Pokud proměnné nejsou nastaveny tímto souborem, jsou nastaveny jinými soubory *. props* a soubory *. targets* , které jsou závislé na hodnotách registru. Vzhledem k tomu, že nenastavujeme žádné hodnoty registru, tyto proměnné by byly prázdné a sestavení by nebylo úspěšné. Místo toho ho přidejte do *partner. AutoImports. props*:

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
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio\2017\Enterprise\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. V každém z vašich souborů projektu přidejte na začátek řádku následující řádek `<Project Default Targets...>` .

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. Změňte prostředí příkazového řádku následujícím způsobem:

    - Set sklad =*umístění adresáře skladu, který jste vytvořili v kroku 1*

    - Nastavte cestu =% Path%; *umístění MSBuild na počítači*;% D epot%\Windows\System32;% D epot%\Windows\SysWOW64;% D epot%\Microsoft Visual Studio 15.0 \ Common7\IDE\

       V případě nativního sestavení 64 ukažte na 64 bitovou verzi nástroje MSBuild.

::: moniker-end

::: moniker range=">=vs-2019"

6. Změňte prostředí příkazového řádku následujícím způsobem:

    - Set sklad =*umístění adresáře skladu, který jste vytvořili v kroku 1*

    - Nastavte cestu =% Path%; *umístění MSBuild na počítači*;% D epot%\Windows\System32;% D epot%\Windows\SysWOW64;% D epot%\Microsoft Visual Studio 16.0 \ Common7\IDE\

       V případě nativního sestavení 64 ukažte na 64 bitovou verzi nástroje MSBuild.

::: moniker-end

## <a name="see-also"></a>Viz také

- [Příprava testovacího počítače na spuštění ladicího spustitelného souboru](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [Referenční dokumentace k příkazovému řádku](../msbuild/msbuild-command-line-reference.md)