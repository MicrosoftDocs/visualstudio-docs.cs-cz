---
title: 'Návod: Vytvoření prostředí pro sestavení s použitím více počítačů'
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
ms.openlocfilehash: 11b158854a0026de28cb2fb0a582bbaf764eeaa4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461540"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>Návod: Vytvoření prostředí pro sestavení s použitím více počítačů

Prostředí sestavení můžete vytvořit v rámci organizace instalací sady Visual Studio do hostitelského počítače a kopírováním různých souborů a nastavení do jiného počítače, aby se mohl účastnit sestavení. Není nutné instalovat Visual Studio na jiném počítači.

Tento dokument neuděluje práva k externí distribuci softwaru ani k poskytování prostředí sestavení třetím stranám.

> Disclaimer<br /><br /> Tento dokument je poskytován "tak, jak je". I když jsme testovali popsané kroky, nejsme schopni vyčerpávajícím způsobem otestovat každou konfiguraci. Pokusíme se udržet dokument aktuální s dalšími informacemi. Informace a názory vyjádřené v tomto dokumentu, včetně adres URL a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění. Microsoft neposkytuje žádné záruky, výslovné ani předpokládané, týkající se zde uváděných informací. Riziko spojené s jejich použitím nesete vy.<br /><br /> Tímto dokumentem nevzniká právní nárok na duševní vlastnictví produktů Microsoftu. Dokument můžete kopírovat a používat pro svou vnitřní potřebu nebo jako referenci.<br /><br /> Nemáte žádnou povinnost poskytovat společnosti Microsoft jakékoli návrhy, komentáře nebo jinou zpětnou vazbu ("zpětná vazba") týkající se tohoto dokumentu. Jakákoli zpětná vazba, kterou dobrovolně poskytnete, však může být použita v produktech společnosti Microsoft a souvisejících specifikacích nebo jiné dokumentaci (souhrnně "Nabídky společnosti Microsoft"), na kterou se mohou spolehnout jiné třetí strany při vývoji vlastních produktů. Pokud tedy poskytnete společnosti Microsoft zpětnou vazbu k jakékoli verzi tohoto dokumentu nebo nabídek společnosti Microsoft, na které se vztahují, souhlasíte s tím, že: (a) Společnost Microsoft může volně používat, reprodukovat, licencovat, distribuovat a jinak komerčně využívat vaši zpětnou vazbu v jakékoli společnosti Microsoft. Nabídka; (b) Třetím stranám také udělujete bez poplatku pouze ta patentová práva nezbytná k tomu, aby jiné produkty mohly používat nebo komunikovat s konkrétními částmi produktu společnosti Microsoft, které obsahují vaši zpětnou vazbu; a (c) Nebudete společnosti Microsoft poskytovat žádnou zpětnou vazbu (i), o které máte důvod se domnívat, že podléhá jakémukoli patentu, autorskému právu nebo jinému nároku na duševní vlastnictví nebo právu jakékoli třetí strany; nebo (ii) na základě licenčních podmínek, které se snaží vyžadovat, aby jakákoli nabídka společnosti Microsoft, která zahrnuje nebo je odvozena od takové zpětné vazby nebo jiného duševního vlastnictví společnosti Microsoft, byla licencována nebo jinak sdílena s jakoukoli třetí stranou.

Tento návod byl ověřen proti následujícím operačním systémům:

- Windows 8 (x86 a x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

Po dokončení kroků v tomto návodu můžete k vytvoření těchto typů aplikací použít prostředí s více počítači:

- Desktopové aplikace C++, které používají windows 8 SDK
- Desktopové aplikace Visual Basic nebo C# zaměřené na rozhraní .NET Framework 4.5

Prostředí s více počítači nelze použít k vytváření těchto typů aplikací:

- Aplikace UPW. Chcete-li vytvořit aplikace UPW, musíte nainstalovat Visual Studio do počítače sestavení.
- Desktopové aplikace, které cílí na rozhraní .NET Framework 4 nebo starší. Chcete-li vytvořit tyto druhy aplikací, musíte nainstalovat visual studio nebo .NET reference sestavení a nástroje (z Windows 7.1 SDK) v počítači sestavení.

## <a name="prerequisites"></a>Požadavky

Visual Studio s nainstalovanou **úlohou pro vývoj pracovních prostředí .NET.**

## <a name="install-software-on-the-computers"></a>Instalace softwaru do počítačů

Nejprve nastavte hostitelský počítač a potom nastavte počítač sestavení.

Instalací sady Visual Studio do hostitelského počítače vytvoříte soubory a nastavení, které později zkopírujete do počítače sestavení. Visual Studio můžete nainstalovat do počítače x86 nebo x64, ale architektura počítače sestavení musí odpovídat architektuře hostitelského počítače.

1. V hostitelském počítači nainstalujte visual studio.

2. V počítači sestavení nainstalujte rozhraní .NET Framework 4.5 nebo novější. Chcete-li ověřit, zda je nainstalována, zkontrolujte, zda položka **Verze** v podklíči registru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** má hodnotu **4,5** nebo vyšší.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Kopírování souborů z hostitelského počítače do počítače sestavení

Tato část popisuje kopírování konkrétních souborů, kompilátorů, nástrojů pro sestavení, prostředků MSBuild a nastavení registru z hostitelského počítače do počítače sestavení. Tyto pokyny předpokládají, že jste nainstalovali Visual Studio ve výchozím umístění v hostitelském počítači. Pokud jste nainstalovali do jiného umístění, upravte podle toho kroky.

- V počítači x86 je výchozím umístěním *C:\Program Files\Microsoft Visual Studio*
- V počítači x64 je výchozím umístěním *C:\Program Files (x86)\Microsoft Visual Studio*

Všimněte si, že název složky *Program Files* závisí na nainstalovaném operačním systému. V počítači s x86 se jmenuje *Program Files*; v počítači x64 je název *Program Files (x86)*. Bez ohledu na architekturu systému tento návod odkazuje na složku *Program Files* jako *%ProgramFiles%*.

> [!NOTE]
> V počítači sestavení musí být všechny příslušné soubory na stejné jednotce. Písmeno jednotky pro tuto jednotku se však může lišit od písmena jednotky pro jednotku, na které je sada Visual Studio nainstalována v hostitelském počítači. V každém případě je nutné při vytváření položek registru, jak je popsáno dále v tomto dokladu, zohlednit umístění souborů.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Kopírování souborů sady Windows SDK do počítače sestavení

1. Pokud máte nainstalovanou jenom sadu Windows SDK pro Windows 8, zkopírujte tyto složky rekurzivně z hostitelského počítače do počítače sestavení:

   - %ProgramFiles%\Windows Kit\8.0\bin\

   - %ProgramFiles%\Windows Kit\8.0\Katalogy\

   - %ProgramFiles%\Windows Kit\8.0\DesignTime\

   - %ProgramFiles%\Windows Kit\8.0\include\

   - %ProgramFiles%\Sady Windows\8.0\Lib\

   - %ProgramFiles%\Sady Windows\8.0\Redist\

   - %ProgramFiles%\Windows Kit\8.0\Reference\

   Pokud máte také tyto další sady windows 8 ...

   - Microsoft Windows Assessment and Deployment Kit

   - Sada ovladačů systému Microsoft Windows

   - Microsoft Windows Hardware Certification Kit

   ... je možné, že nainstalovali soubory do složek *%ProgramFiles%\Windows Kits\8.0,* které jsou uvedeny v předchozím kroku, a jejich licenční podmínky nemusí umožňovat práva na serveru sestavení těchto souborů. Zkontrolujte licenční podmínky pro každou nainstalovanou sadu systému Windows a ověřte, zda mohou být soubory zkopírovány do počítače sestavení. Pokud licenční podmínky neumožňují práva na server sestavení, odeberte soubory z počítače sestavení.

2. Z hostitelského počítače do počítače sestavení rekurzivně zkopírujte následující složky:

    - %ProgramFiles%\Microsoft SDKS\Windows\v8.0A\bin\NETFX 4.0 Tools\

    - %ProgramFiles%\Common Files\Merge Modules\

    - %ProgramFiles%\Verze aplikace\\\<Microsoft \\ \<Visual Studio>edition>\VC\

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>edition>\Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETFramework\v4.5\

3. Zkopírujte tyto soubory z hostitelského počítače do počítače sestavení:

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>edition>\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>edition>\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>edition>\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>vydání>\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>edition>\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>vydání>\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>vydání>\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>vydání>\Common7\Tools\vsvars32.bat

4. Následující knihovny runtime Visual C++ jsou vyžadovány pouze v případě, že spustíte výstupy sestavení v počítači sestavení – například jako součást automatizovaného testování. Soubory jsou obvykle umístěny v podsložkách ve složce *%ProgramFiles%\Microsoft Visual\\\<Studio verze \\ \<>edition>\VC\redist\x86* nebo *%ProgramFiles%\Microsoft Visual Studio\\\<verze>\\ \<edition>\VC\redist\x64,* v závislosti na architektuře systému. V systémech x86 zkopírujte binární soubory x86 do složky *Windows\System32.* V systémech x64 zkopírujte binární soubory x86 do složky *Windows\SysWOW64* a binární soubory x64 do složky *Windows\System32.*

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

5. Zkopírujte do počítače sestavení pouze následující soubory ze složky *Debug_NonRedist\x86* nebo *Debug_NonRedist\x64,* jak je popsáno v [části Příprava testovacího počítače na spuštění spustitelného ladicího souboru](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable). Žádné další soubory nesmí být kopírovány.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>Vytvoření nastavení registru

Chcete-li konfigurovat nastavení pro msbuild, je nutné vytvořit položky registru.

1. Identifikujte nadřazenou složku pro položky registru. Všechny položky registru jsou vytvořeny pod stejným nadřazeným klíčem. V počítači x86 je nadřazený klíč **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**. V počítači x64 je nadřazený klíč **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft**. Bez ohledu na architekturu systému tento návod odkazuje na nadřazený klíč jako %RegistryRoot%.

    > [!NOTE]
    > Pokud se architektura hostitelského počítače liší od architektury počítače sestavení, nezapomeňte v každém počítači použít příslušný nadřazený klíč. To je obzvláště důležité, pokud automatizujete proces exportu.
    >
    > Pokud v počítači sestavení používáte jiné písmeno jednotky než ten, který používáte v hostitelském počítači, nezapomeňte změnit hodnoty položek registru tak, aby odpovídaly.

2. Vytvořte následující položky registru v počítači sestavení. Všechny tyto položky jsou řetězce (Typ == "REG_SZ" v registru). Nastavte hodnoty těchto položek stejné jako hodnoty srovnatelných položek v hostitelském počítači.

   - **%Kořenový\\adresář registru% . NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(Default)**

   - <strong>%Kořenový adresář registru%\MicrosoftSDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%Kořenový adresář registru%\MicrosoftSDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%Kořenový adresář registru%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%Kořenový adresář registru%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **%Kořenový\VisualStudio\11.0@Source adresář registru% adresářů**

   - <strong>%Kořenový adresář registru%\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>%Kořenový adresář registru%\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>%Kořenový adresář registru%\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>%Kořenový adresář registru%\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>%Kořenový adresář registru%\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **%Kořenový adresář registru%\VisualStudio\SxS\VC7@11.0**

   - **%Kořenový adresář registru%\VisualStudio\SxS\VS7@11.0**

   - <strong>%Název_registru%\Sady Windows\NainstalovánoRoots@KitsRoot</strong>

   - <strong>%Kořenový adresář registru%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>%Kořenový adresář registru%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>%Kořenový adresář registru%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   V počítači sestavení x64 také vytvořte následující položku registru a vyhledejte hostitelský počítač a zjistěte, jak ji nastavit.

   - <strong>%Kořenový adresář registru%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   Pokud je počítač sestavení x64 a chcete použít 64bitovou verzi služby MSBuild nebo pokud používáte službu Team Foundation Server Build Service v počítači x64, vytvořte následující položky registru v nativním 64bitovém registru. Informace o nastavení těchto položek naleznete v hostitelském počítači.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Nastavení proměnných prostředí v počítači sestavení

Chcete-li použít MSBuild v počítači sestavení, musíte nastavit proměnné prostředí PATH. Můžete použít *vcvarsall.bat* nastavit proměnné, nebo můžete ručně nakonfigurovat.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Použití vcvarsall.bat k nastavení proměnných prostředí

Otevřete okno **příkazového řádku** v počítači sestavení a spusťte *%Program Files%\Microsoft Visual Studio\\\<verze>\\ \<edition>\VC\vcvarsall.bat*. Argument příkazového řádku můžete použít k určení sady nástrojů, kterou chcete použít – x86, nativní x64 nebo x64 křížový kompilátor. Pokud nezadáte argument příkazového řádku, použije se sada nástrojů x86.

Tato tabulka popisuje podporované argumenty pro *vcvarsall.bat*:

|Vcvarsall.bat argument|Kompilátoru|Sestavení počítačové architektury|Sestavení výstupní architektury|
| - |--------------| - | - |
|x86 (výchozí)|32bitový nativní|x86, x64|x86|
|x86_amd64|x64 Kříž|x86, x64|x64|
|amd64|x64 Nativní|x64|x64|

Pokud *vcvarsall.bat* běží úspěšně – to znamená, že se nezobrazí žádná chybová zpráva – můžete přeskočit další krok a pokračovat v [instalaci sestavení MSBuild do globální mezipaměti sestavení (GAC) v](#install-msbuild-to-gac) části sestavení počítače tohoto dokumentu.

### <a name="manually-set-environment-variables"></a>Ruční nastavení proměnných prostředí

1. Chcete-li ručně nakonfigurovat prostředí příkazového řádku, přidejte tuto cestu do proměnné prostředí PATH:

    - %Program Files%\Microsoft\\\<Visual \\ \<Studio verze>edition>\Common7\IDE

2. Volitelně můžete také přidat následující cesty do proměnné PATH, aby bylo snazší použít MSBuild k sestavení řešení.

   Pokud chcete použít nativní 32bitové MSBuild, přidejte tyto cesty do proměnné PATH:

   - %Program Files%\Microsoft SDKS\Windows\v8.0A\bin\NETFX 4.0 Tools

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   Pokud chcete použít nativní 64bitový MSBuild, přidejte tyto cesty do proměnné PATH:

   - %Program Files%\Microsoft SDKS\Windows\v8.0A\BIN\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" />Instalace sestavení MSBuild do globální mezipaměti sestavení (GAC) v počítači sestavení

MSBuild vyžaduje některé další sestavení, které mají být nainstalovány do GAC v počítači sestavení.

1. Zkopírujte následující sestavení z hostitelského počítače do počítače sestavení. Vzhledem k tomu, že budou nainstalovány do GAC, nezáleží na tom, kde si dát je na sestavení počítače.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>vydání>\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<verze>vydání>\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Chcete-li nainstalovat sestavení do gac, vyhledejte *soubor gacutil.exe* v počítači sestavení – obvykle je v %ProgramFiles%\Microsoft SDKS\Windows\v8.0A\bin\NETFX 4.0 Tools\\. Pokud tuto složku nemůžete najít, opakujte kroky v části [Kopírování souborů z hostitelského počítače do](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) části sestavení počítače v tomto návodu.

     Otevřete okno **příkazového řádku,** které má práva správce, a spusťte tento příkaz pro každý soubor:

     **gacutil -i \<soubor>**

    > [!NOTE]
    > Restartování může být nutné pro sestavení plně nainstalovat do GAC.

## <a name="build-projects"></a>Vytváření projektů

Můžete použít Azure Pipelines k vytváření projektů a řešení sady Visual Studio, nebo je můžete sestavit na příkazovém řádku. Při použití Azure Pipelines k vytváření projektů, vyvolá spustitelný soubor MSBuild, který odpovídá architektuře systému. Na příkazovém řádku můžete použít buď 32bitový MSBuild nebo 64bitový MSBuild a můžete zvolit architekturu MSBuild nastavením proměnné prostředí PATH nebo přímým vyvoláním spustitelného souboru MSBuild specifického pro architekturu.

Chcete-li použít *msbuild.exe* na příkazovém řádku, spusťte následující příkaz, ve kterém *solution.sln* je zástupný symbol pro název vašeho řešení.

**msbuild** *solution.sln*

Další informace o použití msbuildu na příkazovém řádku naleznete v [tématu Reference příkazového řádku](../msbuild/msbuild-command-line-reference.md).

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Vytvoření prostředí sestavení tak, aby bylo možné jej zařazovat do správy zdrojového kódu

Můžete vytvořit prostředí sestavení, které lze nasadit do různých počítačů a nevyžaduje soubory "GAC" ing nebo úpravy nastavení registru. Následující kroky jsou pouze jedním ze způsobů, jak toho dosáhnout. Tyto kroky přizpůsobte jedinečným charakteristikám prostředí sestavení.

> [!NOTE]
> Je nutné zakázat přírůstkové sestavení tak, aby *nástroj tracker.exe* nevyvolá chybu během sestavení. Chcete-li zakázat přírůstkové sestavení, nastavte tento parametr sestavení:
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. Vytvořte adresář *Depot* v hostitelském počítači.

     Tyto kroky odkazují na adresář jako %Depot%.

2. Zkopírujte adresáře a soubory popsané v části [Kopírování souborů z hostitelského počítače do](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) části sestavení počítače v tomto návodu, s výjimkou jejich vložení do adresáře *%Depot%,* který jste právě vytvořili. Zkopírujte například z *%ProgramFiles%\Windows Kits\8.0\bin* do *%Depot%\Windows Kit\8.0\bin*.

3. Při vkládání souborů do *%Depot%* proveďte tyto změny:

    - V %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\a \Microsoft.CppCommon.targets\\, změňte každou instanci

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f11d50a3a"

         na

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         První pojmenování závisí na sestavení je GAC'ed.

    - V %Depot% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets změňte každou instanci

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f11d50a3a"

         na

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. Vytvořte soubor *.props* – například *Partner.AutoImports.props*– a vložte jej do kořenového adresáře složky, která obsahuje vaše projekty. Tento soubor se používá k nastavení proměnných, které jsou používány MSBuild najít různé prostředky. Pokud proměnné nejsou nastaveny tímto souborem, jsou nastaveny jinými soubory *.props* a *.targets,* které jsou závislé na hodnotách registru. Vzhledem k tomu, že nenastavujeme žádné hodnoty registru, tyto proměnné by byly prázdné a sestavení by se nezdaří. Místo toho přidejte do *Partner.AutoImports.props*:

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

5. Do každého souboru projektu přidejte následující řádek nahoře za `<Project Default Targets...>` řádek.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. Prostředí příkazového řádku můžete změnit následujícím způsobem:

    - Set Depot =*umístění adresáře Depot, který jste vytvořili v kroku 1*

    - Nastavit cestu=%cesta%; *umístění MSBuild v počítači*;%D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D epot%\Microsoft Visual Studio 15.0\Common7\IDE\

       Pro nativní 64bitové sestavení přejděte na 64bitovou verzi MSBuild.

::: moniker-end

::: moniker range=">=vs-2019"

6. Prostředí příkazového řádku můžete změnit následujícím způsobem:

    - Set Depot =*umístění adresáře Depot, který jste vytvořili v kroku 1*

    - Nastavit cestu=%cesta%; *umístění MSBuild v počítači*;%D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D epot%\Microsoft Visual Studio 16.0\Common7\IDE\

       Pro nativní 64bitové sestavení přejděte na 64bitovou verzi MSBuild.

::: moniker-end

## <a name="see-also"></a>Viz také

- [Příprava testovacího počítače na spuštění ladicího spustitelného souboru](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [Odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md)