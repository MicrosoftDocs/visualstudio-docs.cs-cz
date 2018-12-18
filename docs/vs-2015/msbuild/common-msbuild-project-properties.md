---
title: Obecné vlastnosti projektu nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30371d20e240e5679664a687c5ca098519cac9c0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300050"
---
# <a name="common-msbuild-project-properties"></a>Obecné vlastnosti projektu nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
V následující tabulce jsou uvedeny často používané vlastnosti, které jsou definovány v souborech projektu sady Visual Studio nebo zahrnuté v souborech TARGETS, které poskytuje nástroj MSBuild.  
  
 Soubory projektu v sadě Visual Studio (CSPROJ, vbproj, vcxproj a jiné) obsahují kód XML nástroje MSBuild, která se spouští při vytváření projektu pomocí rozhraní IDE. Projekty obvykle importují jeden nebo více souborů TARGETS pro definování jejich procesu sestavení. Další informace najdete v tématu [. Cílí na soubory](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Seznam běžných vlastností a parametrů  
  
|Vlastnost nebo název parametru|Popis|  
|--------------------------------|-----------------|  
|AdditionalLibPaths|Určuje další složky, ve kterých by měly kompilátory hledat referenční sestavení.|  
|AddModules|Způsobí, že kompilátor zpřístupní všechny typové informace ze zadaných souborů pro projekt, který je aktuálně kompilován. Tato vlastnost je ekvivalentní `/addModules` přepínač kompilátoru.|  
|ALToolPath|Cesta kde lze nalézt AL.exe. Tato vlastnost přepíše aktuální verzi AL.exe a povolí tak používání jiné verze.|  
|ApplicationIcon|Soubor ikony ICO pro předání kompilátoru k vložení v podobě ikony Win32. Vlastnost je ekvivalentní `/win32icon` přepínač kompilátoru.|  
|ApplicationManifest|Určuje cestu k souboru, který se používá ke generování manifestu informace externí řízení uživatelských účtů (UAC). Platí pouze pro projekty Visual Studio, které jsou zacílené [!INCLUDE[windowsver](../includes/windowsver-md.md)].<br /><br /> Ve většině případů je manifest vložený. Nicméně pokud použijete COM bez registrace nebo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení a manifest může být externí soubor, který je nainstalován společně s vaším sestavením aplikace. Další informace viz vlastnost NoWin32Manifest v tomto tématu.|  
|Neexistence souboru AssemblyOriginatorKeyFile|Určuje soubor, který se používá k podepsání sestavení (.snk nebo .pfx) a který je předán [resolvekeysource – úloha](../msbuild/resolvekeysource-task.md) k vygenerování skutečného klíče, který se používá k podepsání sestavení.|  
|AssemblySearchPaths|Seznam umístění pro hledání sestavení referenční sestavení řešení. Pořadí, ve kterém se cesty zobrazují v tomto seznamu má smysl, protože výše uvedené cesty má přednost před pozdějšími položkami.|  
|AssemblyName|Název finálního výstupního sestavení po sestavení projektu.|  
|Vlastnost BaseAddress|Určuje základní adresu hlavního výstupního sestavení. Tato vlastnost je ekvivalentní `/baseaddress` přepínač kompilátoru.|  
|BaseOutputPath|Specifikuje základní cestu pro výstupní soubor. Pokud je nastavena, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] použije `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Příklad syntaxe: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>`|  
|BaseIntermediateOutputPath|Složky nejvyšší úrovně, kde jsou vytvořeny všechny složky zprostředkujících výstupů specifické konfigurace. Výchozí hodnota je `obj\`. Následující kód je příklad: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>`|  
|BuildInParallel|Logická hodnota, která označuje, zda odkazy na projekt jsou vytvořeny nebo vyčištěny paralelně při více procesů [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] se používá. Výchozí hodnota je `true`, což znamená, že projekty budou vytvořeny paralelně, pokud systém obsahuje více jader nebo procesorů.|  
|BuildProjectReferences|Logická hodnota, která určuje, zda jsou odkazy na projekt vytvořil [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Nastavit `false` Pokud vytváříte projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE), `true` -li jinak.|  
|CleanFile|Název souboru, který se použije jako "čistá mezipaměť." Čistá mezipaměť je seznam vygenerovaných souborů mají být odstraněny během operace čištění. Soubor je umístěn v mezilehlé výstupní cestě procesem sestavení.<br /><br /> Tato vlastnost určuje pouze názvy souborů, které nemají informace o cestě.|  
|Znaková stránka|Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace. Tato vlastnost je ekvivalentní `/codepage` přepínač kompilátoru.|  
|CompilerResponseFile|Soubor volitelných odpovědí může být předán úkolům kompilátoru.|  
|Konfigurace|Konfigurace, který vytváříte, buď "Ladění" nebo "Verze".|  
|CscToolPath|Cesta csc.exe, [!INCLUDE[csprcs](../includes/csprcs-md.md)] kompilátoru.|  
|CustomBeforeMicrosoftCommonTargets|Název souboru projektu nebo soubor cílů, které mají být importovány automaticky před importem společných cílů.|  
|DebugSymbols|Logická hodnota, která určuje, zda jsou symboly generovány sestavením.<br /><br /> Nastavení **/p:DebugSymbols = false** na příkazovém řádku zakáže generování souborů symbolů databáze (PDB) programu.|  
|DefineConstants|Definuje podmíněné konstanty kompilátoru. Dvojice symbol/hodnota jsou odděleny středníkem a jsou zadány pomocí následující syntaxe:<br /><br /> *symbol1 = value1; symbol2 = hodnota2*<br /><br /> Vlastnost je ekvivalentní `/define` přepínač kompilátoru.|  
|DefineDebug|Logická hodnota, která určuje, zda má být definována konstanta DEBUG.|  
|DefineTrace|Logická hodnota, která určuje, zda má být definována konstanta TRACE.|  
|DebugType|Definuje úroveň ladění informací, které mají být vygenerovány. Platné hodnoty jsou "full", "pdbonly" a "none".|  
|DelaySign|Logická hodnota, která určuje, zda se má k zpožděný podpis sestavení místo úplného podepsání.|  
|DisabledWarnings|Potlačí zadaná upozornění. Je třeba zadat pouze číselnou část identifikátoru upozornění. Více varování je odděleno středníky. Tento parametr `/nowarn` přepínače kompilátoru vbc.exe.|  
|DisableFastUpToDateCheck|Logická hodnota, která se vztahuje na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pouze. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Sestavení správce používá proces nazývaný FastUpToDateCheck ke zjištění, zda projekt musíte znovu sestavit, aby byl aktuální. Tento proces je rychlejší než použití [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ke zjištění. Nastavení vlastnosti DisableFastUpToDateCheck na `true` umožňuje obejít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] správce sestavení a vynutit používání [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] k určení, zda je aktuální projekt.|  
|DocumentationFile|Název souboru, který je generován jako soubor dokumentace XML. Tento název zahrnuje pouze název souboru a neobsahuje žádné informace o cestě.|  
|ErrorReport|Určuje, jak by měl úkol kompilátor ohlásit interní chyby kompilátoru. Platné hodnoty jsou "prompt", "Odeslat" nebo "none". Tato vlastnost je ekvivalentní `/errorreport` přepínač kompilátoru.|  
|ExcludeDeploymentUrl|[Generatedeploymentmanifest – úloha](../msbuild/generatedeploymentmanifest-task.md) Přidá značku deploymentProvider do manifestu nasazení, pokud soubor projektu obsahuje některé z následujících elementů:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Pomocí ExcludeDeploymentUrl však můžete zabránit značku deploymentProvider přidávaný do manifestu nasazení i v případě, že některé z výše uvedených adres URL zadán. Provedete to tak, přidejte do souboru projektu následující vlastnost:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` **Poznámka:** ExcludeDeploymentUrl není vystaveno v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí a je možné nastavit pouze ruční úpravou souboru projektu. Nastavení této vlastnosti neovlivňuje publikování v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]; to znamená, že značka deploymentProvider bude i tak přidána k adrese URL zadané hodnotou PublishUrl.|  
|Hodnotu FileAlignment|Určuje, v bajtech, kam chcete zarovnat oddíly výstupního souboru. Platné hodnoty jsou 512, 1024, 2048, 4096, 8192. Tato vlastnost je ekvivalentní `/filealignment` přepínač kompilátoru.|  
|FrameworkPathOverride|Určuje umístění knihovny mscorlib.dll a microsoft.visualbasic.dll. Tento parametr je ekvivalentní `/sdkpath` přepínače kompilátoru vbc.exe.|  
|GenerateDocumentation|Parametr logické hodnoty označující, zda je dokumentace generovaná sestavením. Pokud `true`, sestavení generuje informace o dokumentaci a vloží jej do souboru XML s názvem spustitelného souboru nebo knihovnu, která úkol sestavení vytvořen.|  
|IntermediateOutputPath|Úplná cesta zprostředkujících výstupů odvozena z `BaseIntermediateOutputPath`, pokud není zadaná žádná cesta. Například \obj\debug\\. Pokud není tato vlastnost přepsána, nastavení `BaseIntermediateOutputPath` nemá žádný vliv.|  
|KeyContainerName|Název kontejneru klíčů se silným názvem.|  
|KeyOriginatorFile|Název souboru klíče silného názvu.|  
|NoWin32Manifest|Určuje, zda kompilátor generuje výchozí manifest Win32 do výstupu sestavení. Výchozí hodnota `false` znamená, že pro všechny aplikace je generován výchozí manifest Win32. Tato vlastnost je ekvivalentní `/nowin32manifest` přepínač kompilátoru Vbc.exe.|  
|ModuleAssemblyName|Název sestavení, který má být zahrnut do je zkompilovaný modul. Vlastnost je ekvivalentní `/moduleassemblyname` přepínač kompilátoru.|  
|NoLogo|Logická hodnota určující, zda chcete, aby bylo vypnuto logo kompilátoru. Tato vlastnost je ekvivalentní `/nologo` přepínač kompilátoru.|  
|NoStdLib|Logická hodnota určující, zda-li zabránit odkazování standardní knihovnu (mscorlib.dll). Výchozí hodnota je `false`.|  
|NoVBRuntimeReference|Logická hodnota, která určuje, zda [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] modulu runtime (Microsoft.VisualBasic.dll) by měl být zahrnut jako odkaz v projektu.|  
|NoWin32Manifest|Logická hodnota, která určuje, zda informace o manifestu řízení uživatelských účtů (UAC) budou vloženy do aplikace spustitelného souboru. Platí pouze pro projekty Visual Studio, které jsou zacílené [!INCLUDE[windowsver](../includes/windowsver-md.md)]. V projektech, které jsou nasazeny pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a COM bez registrace, tento prvek je ignorován. `False` (výchozí hodnota) určuje, že spustitelný soubor aplikace vložit informace o manifestu řízení uživatelských účtů (UAC). `True` Určuje, že informace o manifestu nástroje Řízení uživatelských účtů nebudou vloženy.<br /><br /> Tato vlastnost se týká pouze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekty cílení [!INCLUDE[windowsver](../includes/windowsver-md.md)]. V projektech, které jsou nasazeny pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a COM bez registrace, tato vlastnost se ignoruje.<br /><br /> Měli byste přidat NoWin32Manifest pouze v případě, že nechcete, aby [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro vložení manifestu všechny informace v aplikaci spustitelného souboru; tento proces se nazývá *virtualizace*. Pro použití virtualizace nastavte `<ApplicationManifest>` ve spojení s `<NoWin32Manifest>` následujícím způsobem:<br /><br /> -Pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty, odeberte `<ApplicationManifest>` uzlu. (V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty, `<NoWin32Manifest>` ignorováno, pokud `<ApplicationManifest>` uzel existuje.)<br />-Pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektů, nastavte `<ApplicationManifest>` k `False` a `<NoWin32Manifest>` k `True`. (V [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekty, `<ApplicationManifest>` přepíše `<NoWin32Manifest>`.)|  
|Optimalizace|Logická hodnota, která pokud je nastavena na `true`, povolí optimalizace kompilátoru. Tato vlastnost je ekvivalentní `/optimize` přepínač kompilátoru.|  
|OptionCompare|Určuje způsob porovnávání řetězců. Platné hodnoty jsou "binární" nebo "text". Tato vlastnost je ekvivalentní `/optioncompare` přepínač kompilátoru Vbc.exe.|  
|OptionExplicit|Logická hodnota, která pokud je nastavena na `true`, vyžaduje explicitní deklaraci proměnných ve zdrojovém kódu. Tato vlastnost je ekvivalentní `/optionexplicit` přepínač kompilátoru.|  
|OptionInfer|Logická hodnota, která pokud je nastavena na `true`, povolí odvozování typů proměnných. Tato vlastnost je ekvivalentní `/optioninfer` přepínač kompilátoru.|  
|OptionStrict|Logická hodnota, která pokud je nastavena na `true`, způsobí, že úkol sestavení vynutí sémantiku přísného typu pro omezení převodů implicitních typů. Tato vlastnost je ekvivalentní `/optionstrict` přepínače kompilátoru vbc.exe.|  
|OutputPath|Určuje cestu k výstupnímu adresáři relativně vzhledem k adresáři projektu, například bin\Debug"".|  
|Element OutputType|Určuje formát výstupního souboru. Tento parametr může mít jednu z následujících hodnot:<br /><br /> -Knihovny. Vytvoří knihovnu kódu. (Výchozí hodnota.)<br />-Exe. Vytvoří konzolovou aplikaci.<br />-Module. Vytvoří modul.<br />-Winexe. Vytvoří program pro systém Windows.<br /><br /> Tato vlastnost je ekvivalentní `/target` přepínače kompilátoru vbc.exe.|  
|OverwriteReadOnlyFiles|Logická hodnota, která určuje, zda chcete povolit sestavení přepsat soubory jen pro čtení nebo vyvolat chybu.|  
|PdbFile|Název souboru, který emitujete souboru .pdb. Tato vlastnost je ekvivalentní `/pdb` přepínače kompilátoru csc.exe.|  
|Platforma|Operační systém, který vytváříte. Platné hodnoty jsou "Any CPU", "x 86" a "x64".|  
|RemoveIntegerChecks|Logická hodnota určující, zda chcete zakázat chyby kontroly přetečení celých čísel. Výchozí hodnota je `false`. Tato vlastnost je ekvivalentní `/removeintchecks` přepínače kompilátoru vbc.exe.|  
|SGenUseProxyTypes|Logická hodnota, která určuje, zda typy proxy měly být generovány pomocí SGen.exe.<br /><br /> Cíl SGen používá tuto vlastnost pro nastavení příznaku UseProxyTypes. Výchozí hodnota této vlastnosti na hodnotu true a neexistuje žádné uživatelské rozhraní pro toto nastavení změnit. Generovat sestavení serializace pro typy bez, přidejte do souboru projektu tuto vlastnost a nastavte ji na hodnotu false před importem cílů Microsoft.Common.Targets nebo webových.|  
|SGenToolPath|Volitelný nástroj pro cestu, která označuje, kde získat SGen.exe, když je aktuální verze SGen.exe přepsána.|  
|StartupObject|Určuje třídu nebo modul, který obsahuje metodu Main nebo Sub Main proceduru. Tato vlastnost je ekvivalentní `/main` přepínač kompilátoru.|  
|Vlastnost ProcessorArchitecture|Architektura procesoru, který se používá, když jsou překládány odkazy na sestavení. Platné hodnoty jsou "msil", "x86," "amd64" nebo "ia64".|  
|RootNamespace|Kořenový obor názvů použijte, pokud pojmenujete integrovaný zdroj. Tento obor názvů je částí názvu vloženého manifestu prostředků.|  
|Satellite_AlgorithmId|ID hashovacího algoritmu AL.exe pro použití při vytváření satelitních sestavení.|  
|Satellite_BaseAddress|Základní adresa pro použití při satelitní sestavení specifická pro jazykovou verzi jsou vytvořeny pomocí `CreateSatelliteAssemblies` cíl.|  
|Satellite_CompanyName|Název společnosti, který má být předán AL.exe během vytváření satelitních sestavení.|  
|Satellite_Configuration|Název konfigurace lze předat do AL.exe během vytváření satelitních sestavení.|  
|Satellite_Description|Text popisu, který má být předán AL.exe během vytváření satelitních sestavení.|  
|Satellite_EvidenceFile|Vloží zadaný soubor do satelitního sestavení, který má název prostředku "Security.Evidence".|  
|Satellite_FileVersion|Určuje řetězec pro pole verze souboru v satelitním sestavení.|  
|Satellite_Flags|Určuje hodnotu pro pole Flags v satelitním sestavení.|  
|Satellite_GenerateFullPaths|Způsobí, že úkol sestavení použije absolutní cesty pro všechny soubory uvedeny v chybové zprávě.|  
|Satellite_LinkResource|Propojí určené soubory prostředků se satelitním sestavením.|  
|Satellite_MainEntryPoint|Určuje plně kvalifikovaný název (tj. class.method) metody pro použití jako vstupní bod při převodu modulu na spustitelný soubor během vytváření satelitních sestavení.|  
|Satellite_ProductName|Určuje řetězec pro pole produktu v satelitním sestavení.|  
|Satellite_ProductVersion|Určuje řetězec pro pole ProductVersion v satelitním sestavení.|  
|Satellite_TargetType|Určuje formát výstupního souboru satelitní sestavení jako "knihovna," "řetězec exe", nebo "win". Výchozí hodnota je "library".|  
|Satellite_Title|Určuje řetězec pro pole Title v satelitním sestavení.|  
|Satellite_Trademark|Určuje řetězec pro pole Trademark v satelitním sestavení.|  
|Satellite_Version|Určuje informace o verzi satelitního sestavení.|  
|Satellite_Win32Icon|Vloží soubor ikony .ico do satelitního sestavení.|  
|Satellite_Win32Resource|Vloží prostředek systému Win32 (soubor .res) do satelitního sestavení.|  
|SubsystemVersion|Určuje minimální verzi podsystému, který může používat vygenerovaný spustitelný soubor. Tato vlastnost je ekvivalentní `/subsystemversion` přepínač kompilátoru. Informace o výchozí hodnota této vlastnosti naleznete v tématu [/subsystemversion (Visual Basic)](http://msdn.microsoft.com/library/08be22b2-f447-4cd3-8203-120b1b920b54) nebo [/subsystemversion (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/a99fce81-9d92-4813-9874-bee777041445).|  
|TargetCompactFramework|Verze .NET Compact Framework, která je nutná ke spuštění aplikace, kterou vytváříte. Určení tohoto umožňuje odkazovat na určitá sestavení rozhraní, které nelze odkazovat, jinak.|  
|Parametr targetFrameworkVersion|Verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , který se vyžaduje pro spuštění aplikace, kterou vytváříte. Určení tohoto umožňuje odkazovat na určitá sestavení rozhraní, které nelze odkazovat, jinak.|  
|TreatWarningsAsErrors|Parametr logické hodnoty, pokud `true`, způsobí, že všechna upozornění budou považována za chyby. Tento parametr je ekvivalentní `/nowarn` přepínač kompilátoru.|  
|UseHostCompilerIfAvailable|Parametr logické hodnoty, pokud `true`, způsobí, že úkol sestavení použije objekt vnitroprocesového kompilátoru, pokud je k dispozici. Tento parametr je používán pouze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|Utf8Output|Parametr logické hodnoty, pokud `true`, protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr je ekvivalentní `/utf8Output` přepínač kompilátoru.|  
|VbcToolPath|Volitelná cesta označuje jiné umístění pro vbc.exe, když je přepsána aktuální verze vbc.exe.|  
|VbcVerbosity|Určuje úroveň podrobností [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] výstupu kompilátoru. Platné hodnoty jsou "Quiet", "Normal" (výchozí hodnota), nebo "Verbose".|  
|VisualStudioVersion|Určuje verzi sady Visual Studio, pod kterým tohoto projektu by měly být považovány za aplikace běžící. Pokud není tato vlastnost určena, nástroj MSBuild ji nastaví na rozumnou výchozí hodnotu.<br /><br /> Tato vlastnost se používá v několika typech projektů pro určení sady cílů, které se používají pro sestavení. Pokud `ToolsVersion` je nastavena na hodnotu 4.0 nebo vyšší pro projekt, `VisualStudioVersion` slouží k určení, které dílčí nástroje použít. Další informace najdete v tématu [sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).|  
|WarningsAsErrors|Označí seznam upozornění pro nakládání s chybami. Tento parametr je ekvivalentní `/warnaserror` přepínač kompilátoru.|  
|WarningsNotAsErrors|Označí seznam upozornění, která nemají být považována za chyby. Tento parametr je ekvivalentní `/warnaserror` přepínač kompilátoru.|  
|Win32Manifest|Název souboru manifestu, který má být vložen v konečném sestavení. Tento parametr je ekvivalentní `/win32Manifest` přepínač kompilátoru.|  
|Win32Resource|Název souboru prostředků Win32, který má být vložen v konečném sestavení. Tento parametr je ekvivalentní `/win32resource` přepínač kompilátoru.|  
  
## <a name="see-also"></a>Viz také  
 [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)



