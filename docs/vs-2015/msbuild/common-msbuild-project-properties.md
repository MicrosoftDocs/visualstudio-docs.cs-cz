---
title: Obecné vlastnosti projektu nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 1eb56d1334eb18dd5872457d032e5780a3f75eb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698711"
---
# <a name="common-msbuild-project-properties"></a>Obecné vlastnosti projektu nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V následující tabulce jsou uvedeny často používané vlastnosti, které jsou definovány v souborech projektu sady Visual Studio nebo zahrnuté v souborech. targets, které poskytuje MSBuild.  
  
 Soubory projektu v aplikaci Visual Studio (. csproj, vbproj, vcxproj a jiné) obsahují kód XML nástroje MSBuild, který se spouští při vytváření projektu pomocí integrovaného vývojového prostředí (IDE). Projekty obvykle importují jeden nebo více souborů. targets pro definování svého procesu sestavení. Další informace najdete v tématu [. Cílí na soubory](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Seznam běžných vlastností a parametrů  
  
|Název vlastnosti nebo parametru|Popis|  
|--------------------------------|-----------------|  
|AdditionalLibPaths|Určuje další složky, ve kterých mají kompilátory Hledat referenční sestavení.|  
|AddModules|Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který kompilujete. Tato vlastnost je ekvivalentní `/addModules` přepínači kompilátoru.|  
|ALToolPath|Cesta, kde lze nalézt AL.exe. Tato vlastnost přepíše aktuální verzi AL.exe, aby bylo možné použít jinou verzi.|  
|ApplicationIcon|Soubor ikony. ico, který se předá kompilátoru pro vložení jako ikona Win32. Vlastnost je ekvivalentní `/win32icon` přepínači kompilátoru.|  
|Souboru ApplicationManifest|Určuje cestu k souboru, který se používá ke generování informací o manifestu nástroje řízení externích uživatelských účtů (UAC). Platí pouze pro cílení projektů sady Visual Studio [!INCLUDE[windowsver](../includes/windowsver-md.md)] .<br /><br /> Ve většině případů je manifest vložen. Pokud však použijete registrační model COM nebo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení Free, manifest může být externí soubor, který je nainstalován společně se sestaveními vaší aplikace. Další informace najdete v tomto tématu v vlastnosti NoWin32Manifest.|  
|AssemblyOriginatorKeyFile|Určuje soubor, který se používá k podepsání sestavení (. snk nebo. pfx) a který je předán [úloze ResolveKeySource –](../msbuild/resolvekeysource-task.md) , aby vygeneroval skutečný klíč, který se používá k podepsání sestavení.|  
|AssemblySearchPaths|Seznam umístění, která se mají hledat během překladu referenčního sestavení v době sestavení Pořadí, ve kterém se cesty zobrazují v tomto seznamu, je smysluplné, protože cesty uvedené dříve mají přednost před pozdějšími položkami.|  
|Doplňk|Název konečného výstupního sestavení po sestavení projektu.|  
|BaseAddress|Určuje základní adresu hlavního výstupního sestavení. Tato vlastnost je ekvivalentní `/baseaddress` přepínači kompilátoru.|  
|BaseOutputPath|Určuje základní cestu pro výstupní soubor. Pokud je nastaven, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bude používat `OutputPath = $(BaseOutputPath)\$(Configuration)\` . Příklad syntaxe: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>`|  
|BaseIntermediateOutputPath|Složka na nejvyšší úrovni, kde jsou vytvořeny všechny přechodné výstupní složky specifické pro konfiguraci. Výchozí hodnota je `obj\`. Následující kód je příklad: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>`|  
|BuildInParallel|Logická hodnota, která označuje, zda jsou odkazy na projekt vytvářeny nebo čištěny paralelně při použití více procesů [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Výchozí hodnota je `true` , což znamená, že projekty budou sestaveny paralelně, pokud má systém více jader nebo procesorů.|  
|BuildProjectReferences|Logická hodnota, která určuje, zda jsou vytvořeny odkazy na projekt [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Nastavte `false` při sestavování projektu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE), `true` Pokud je to jinak.|  
|CleanFile|Název souboru, který se použije jako "čistá mezipaměť". Čistá mezipaměť je seznam generovaných souborů, které mají být odstraněny během operace čištění. Soubor je umístěn do mezilehlé výstupní cesty procesem sestavení.<br /><br /> Tato vlastnost určuje pouze názvy souborů, které nemají informace o cestě.|  
|Stránky|Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci. Tato vlastnost je ekvivalentní `/codepage` přepínači kompilátoru.|  
|CompilerResponseFile|Volitelný soubor odpovědí, který lze předat úlohám kompilátoru.|  
|Konfigurace|Konfigurace, kterou vytváříte, buď "ladit" nebo "Release".|  
|CscToolPath|Cesta csc.exe, [!INCLUDE[csprcs](../includes/csprcs-md.md)] kompilátor.|  
|CustomBeforeMicrosoftCommonTargets|Název souboru projektu nebo souboru cílů, který má být importován automaticky před importem běžných cílů.|  
|DebugSymbols|Logická hodnota, která určuje, zda jsou symboly generovány sestavením.<br /><br /> Nastavení parametru **/p: DebugSymbols = false** na příkazovém řádku zakáže generování souborů symbolů databáze programu (PDB).|  
|DefineConstants|Definuje podmíněné konstanty kompilátoru. Páry symbol/hodnota jsou odděleny středníky a jsou určeny pomocí následující syntaxe:<br /><br /> *symbol1 = hodnota1; symbol2 = hodnota2*<br /><br /> Vlastnost je ekvivalentní `/define` přepínači kompilátoru.|  
|DefineDebug|Logická hodnota, která určuje, zda má být definována konstanta ladění.|  
|DefineTrace|Logická hodnota, která určuje, zda má být definována konstanta TRACE.|  
|DebugType|Definuje úroveň ladicích informací, které chcete vygenerovat. Platné hodnoty jsou "Full", "pdbonly" a "none".|  
|DelaySign|Logická hodnota, která označuje, zda chcete sestavení zpozdit podpisem, nikoli úplným podepsáním.|  
|DisabledWarnings|Potlačí zadaná upozornění. Je třeba zadat pouze číselnou část identifikátoru upozornění. Několik upozornění je odděleno středníky. Tento parametr odpovídá `/nowarn` přepínači vbc.exe kompilátoru.|  
|DisableFastUpToDateCheck|Logická hodnota, která se vztahuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pouze na. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Správce sestavení používá proces nazvaný FastUpToDateCheck k určení, zda projekt musí být znovu sestaven, aby byl aktuální. Tento proces je rychlejší než použití [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] k určení tohoto procesu. Nastavení vlastnosti DisableFastUpToDateCheck na `true` umožňuje obejít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] správce sestavení a vynutit, aby bylo možné použít [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] k určení, zda je projekt aktuální.|  
|DocumentationFile|Název souboru, který je generován jako soubor dokumentace XML. Tento název obsahuje pouze název souboru a neobsahuje informace o cestě.|  
|ErrorReport|Určuje, jak má úloha kompilátoru nahlásit interní chyby kompilátoru. Platné hodnoty jsou "prompt", "Odeslat" nebo "none". Tato vlastnost je ekvivalentní `/errorreport` přepínači kompilátoru.|  
|ExcludeDeploymentUrl|[Úloha GenerateDeploymentManifest –](../msbuild/generatedeploymentmanifest-task.md) Přidá značku deploymentProvider do manifestu nasazení, pokud soubor projektu obsahuje některý z následujících prvků:<br /><br /> - UpdateUrl<br />– InstallUrl<br />- PublishUrl<br /><br /> Pomocí ExcludeDeploymentUrl však můžete zabránit přidání značky deploymentProvider do manifestu nasazení, i když je zadána kterákoli z výše uvedených adres URL. Chcete-li to provést, přidejte do souboru projektu následující vlastnost:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>`**Poznámka:**  ExcludeDeploymentUrl se nezveřejňuje v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní IDE a dá se nastavit jenom ruční úpravou souboru projektu. Nastavení této vlastnosti neovlivní publikování v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ; to znamená, že značka deploymentProvider bude stále přidána k adrese URL určené parametrem PublishURL.|  
|Zarovnání.|Určuje, kam se v bajtech mají zarovnat oddíly výstupního souboru. Platné hodnoty jsou 512, 1024, 2048, 4096, 8192. Tato vlastnost je ekvivalentní `/filealignment` přepínači kompilátoru.|  
|FrameworkPathOverride|Určuje umístění mscorlib.dll a microsoft.visualbasic.dll. Tento parametr je ekvivalentní `/sdkpath` přepínači vbc.exe kompilátoru.|  
|GenerateDocumentation|Logický parametr, který označuje, zda je dokumentace generována sestavením. Pokud `true` , sestavení generuje informace o dokumentaci a umístí je do souboru. XML spolu s názvem spustitelného souboru nebo knihovny, kterou vytvořil úkol sestavení.|  
|IntermediateOutputPath|Úplná zprostředkující výstupní cesta odvozená od `BaseIntermediateOutputPath` , pokud není zadána žádná cesta. Například \obj\debug \\ . Pokud je tato vlastnost přepsána, nastavení `BaseIntermediateOutputPath` nemá žádný vliv.|  
|ContainerName|Název kontejneru klíčů se silným názvem.|  
|KeyOriginatorFile|Název souboru klíče se silným názvem.|  
|NoWin32Manifest|Určuje, zda kompilátor generuje výchozí manifest Win32 do výstupního sestavení. Výchozí hodnota `false` znamená, že výchozí manifest Win32 je vygenerován pro všechny aplikace. Tato vlastnost je ekvivalentní `/nowin32manifest` přepínači kompilátoru vbc.exe.|  
|Moduleassemblyname –|Název sestavení, do kterého má být kompilovaný modul začleněn. Vlastnost je ekvivalentní `/moduleassemblyname` přepínači kompilátoru.|  
|NoLogo|Logická hodnota, která označuje, zda má být vypnuto logo kompilátoru. Tato vlastnost je ekvivalentní `/nologo` přepínači kompilátoru.|  
|NoStdLib|Logická hodnota, která označuje, zda se má vyhýbat odkazování na standardní knihovnu (mscorlib.dll). Výchozí hodnota je `false`.|  
|NoVBRuntimeReference|Logická hodnota, která určuje, zda má [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] být modul runtime (Microsoft.VisualBasic.dll) zahrnut jako odkaz v projektu.|  
|NoWin32Manifest|Logická hodnota, která označuje, zda informace o manifestu nástroje řízení uživatelských účtů (UAC) budou vloženy do spustitelného souboru aplikace. Platí pouze pro cílení projektů sady Visual Studio [!INCLUDE[windowsver](../includes/windowsver-md.md)] . V projektech nasazených pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a modelu COM bez registrace je tento prvek ignorován. `False` (výchozí hodnota) určuje, že informace o manifestu nástroje řízení uživatelských účtů (UAC) budou vloženy do spustitelného souboru aplikace. `True` Určuje, že informace o manifestu nástroje řízení uživatelských účtů nebudou vloženy.<br /><br /> Tato vlastnost se vztahuje pouze na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cílení na projekty [!INCLUDE[windowsver](../includes/windowsver-md.md)] . V projektech nasazených pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a modelu COM bez registrace je tato vlastnost ignorována.<br /><br /> NoWin32Manifest byste měli přidat pouze v případě, že nechcete [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vkládat žádné informace o manifestech do spustitelného souboru aplikace. Tento proces se nazývá *virtualizace*. Chcete-li použít virtualizaci, nastavte `<ApplicationManifest>` ve spojení s `<NoWin32Manifest>` následujícím způsobem:<br /><br /> – Pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty odeberte `<ApplicationManifest>` uzel. (V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektech se `<NoWin32Manifest>` ignoruje, když `<ApplicationManifest>` uzel existuje.)<br />– Pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekty nastavte `<ApplicationManifest>` na `False` a `<NoWin32Manifest>` na `True` . (V [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektech, `<ApplicationManifest>` Overrides `<NoWin32Manifest>` .)|  
|Optimalizace|Logická hodnota, která Pokud je nastavena na `true` , umožňuje optimalizace kompilátoru. Tato vlastnost je ekvivalentní `/optimize` přepínači kompilátoru.|  
|OptionCompare –|Určuje, jak se provádí porovnávání řetězců. Platné hodnoty jsou "Binary" nebo "text". Tato vlastnost je ekvivalentní `/optioncompare` přepínači kompilátoru vbc.exe.|  
|OptionExplicit –|Logická hodnota, která Pokud je nastavena na `true` , vyžaduje explicitní deklaraci proměnných ve zdrojovém kódu. Tato vlastnost je ekvivalentní `/optionexplicit` přepínači kompilátoru.|  
|Optioninfer –|Logická hodnota, která Pokud je nastavena na `true` , umožňuje odvozování typů proměnných. Tato vlastnost je ekvivalentní `/optioninfer` přepínači kompilátoru.|  
|OptionStrict –|Logická hodnota, která Pokud je nastavena na `true` , způsobí, že úloha sestavení vynutí striktní sémantiku typu pro omezení implicitních převodů typu. Tato vlastnost je ekvivalentní `/optionstrict` přepínači vbc.exe kompilátoru.|  
|OutputPath|Určuje cestu k výstupnímu adresáři vzhledem k adresáři projektu, například "bin\Debug".|  
|OutputType|Určuje formát výstupního souboru. Tento parametr může mít jednu z následujících hodnot:<br /><br /> Knihovna. Vytvoří knihovnu kódu. (Výchozí hodnota.)<br />Programu. Vytvoří konzolovou aplikaci.<br />Čipu. Vytvoří modul.<br />Winexe. Vytvoří program založený na systému Windows.<br /><br /> Tato vlastnost je ekvivalentní `/target` přepínači vbc.exe kompilátoru.|  
|OverwriteReadOnlyFiles|Logická hodnota, která označuje, zda chcete povolit sestavení pro přepsání souborů jen pro čtení nebo spuštění chyby.|  
|PdbFile|Název souboru. pdb, který vysíláte. Tato vlastnost je ekvivalentní `/pdb` přepínači csc.exe kompilátoru.|  
|Platforma|Operační systém, pro který sestavíte. Platné hodnoty jsou "any CPU", "x86" a "x64".|  
|RemoveIntegerChecks|Logická hodnota, která označuje, zda se mají zakázat kontroly chyb přetečení celých čísel. Výchozí hodnota je `false`. Tato vlastnost je ekvivalentní `/removeintchecks` přepínači vbc.exe kompilátoru.|  
|SGenUseProxyTypes|Logická hodnota, která určuje, zda mají být generovány typy proxy pomocí SGen.exe.<br /><br /> Cíl SGen používá tuto vlastnost k nastavení příznaku UseProxyTypes. Tato vlastnost je nastavena na hodnotu true a neexistuje žádné uživatelské rozhraní, které by bylo možné změnit. Chcete-li vygenerovat sestavení serializace pro typy non-WebService, přidejte tuto vlastnost do souboru projektu a nastavte ji na false před importem Microsoft. Common. Targets nebo C#/VB.targets.|  
|SGenToolPath|Volitelná cesta nástroje, která označuje, kde získat SGen.exe, když je aktuální verze SGen.exe přepsána.|  
|StartupObject|Určuje třídu nebo modul, který obsahuje metodu Main nebo Sub Main Procedure. Tato vlastnost je ekvivalentní `/main` přepínači kompilátoru.|  
|ProcessorArchitecture|Architektura procesoru, která se používá, když jsou přeloženy odkazy na sestavení. Platné hodnoty jsou "MSIL", "x86", "amd64" nebo "ia64".|  
|RootNamespace|Kořenový obor názvů, který se má použít při pojmenování vloženého prostředku. Tento obor názvů je součástí názvu vloženého manifestu prostředku.|  
|Satellite_AlgorithmId|ID algoritmu hash AL.exe, který se má použít při vytváření satelitních sestavení.|  
|Satellite_BaseAddress|Základní adresa, která se použije v případě satelitních sestavení specifických pro jazykovou verzi, se vytváří pomocí `CreateSatelliteAssemblies` cíle.|  
|Satellite_CompanyName|Název společnosti, který se má předat AL.exe během generování satelitního sestavení.|  
|Satellite_Configuration|Název konfigurace, který se má předat AL.exe během generování satelitního sestavení.|  
|Satellite_Description|Text popisu, který se má předat AL.exe během generování satelitního sestavení.|  
|Satellite_EvidenceFile|Vloží zadaný soubor do satelitního sestavení, které má název prostředku "Security. evidence".|  
|Satellite_FileVersion|Určuje řetězec pro pole verze souboru v satelitním sestavení.|  
|Satellite_Flags|Určuje hodnotu pro pole flags v satelitním sestavení.|  
|Satellite_GenerateFullPaths|Způsobí, že úloha sestavení použije absolutní cesty pro všechny soubory hlášené v chybové zprávě.|  
|Satellite_LinkResource|Propojí zadané soubory prostředků se satelitním sestavením.|  
|Satellite_MainEntryPoint|Určuje plně kvalifikovaný název (tj. Class. Method) metody pro použití jako vstupní bod při převodu modulu na spustitelný soubor během generování satelitního sestavení.|  
|Satellite_ProductName|Určuje řetězec pro pole produktu v satelitním sestavení.|  
|Satellite_ProductVersion|Určuje řetězec pro pole ProductVersion v satelitním sestavení.|  
|Satellite_TargetType|Určuje formát výstupního souboru satelitního sestavení jako "Library", "exe" nebo "Win". Výchozí hodnota je "Library".|  
|Satellite_Title|Určuje řetězec pro pole title v satelitním sestavení.|  
|Satellite_Trademark|Určuje řetězec pro pole ochranné známky v satelitním sestavení.|  
|Satellite_Version|Určuje informace o verzi satelitního sestavení.|  
|Satellite_Win32Icon|Vloží soubor ikony. ico do satelitního sestavení.|  
|Satellite_Win32Resource|Vloží prostředek systému Win32 (soubor. res) do satelitního sestavení.|  
|SubsystemVersion|Určuje minimální verzi subsystému, kterou může vygenerovaný spustitelný soubor použít. Tato vlastnost je ekvivalentní `/subsystemversion` přepínači kompilátoru. Informace o výchozí hodnotě této vlastnosti naleznete v tématu [/subsystemversion (Visual Basic)](https://msdn.microsoft.com/library/08be22b2-f447-4cd3-8203-120b1b920b54) nebo [/subsystemversion (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/a99fce81-9d92-4813-9874-bee777041445).|  
|TargetCompactFramework|Verze prostředí .NET Compact Framework potřebná ke spuštění aplikace, kterou vytváříte. Zadáním této možnosti můžete odkazovat na konkrétní sestavení rozhraní, která pravděpodobně nebudete moci odkazovat jinak.|  
|TargetFrameworkVersion|Verze nástroje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , která je vyžadována pro spuštění aplikace, kterou vytváříte. Zadáním této možnosti můžete odkazovat na konkrétní sestavení rozhraní, která pravděpodobně nebudete moci odkazovat jinak.|  
|TreatWarningsAsErrors|Logický parametr, který v případě `true` , že způsobí, že všechna upozornění budou považována za chyby. Tento parametr je ekvivalentní `/nowarn` přepínači kompilátoru.|  
|UseHostCompilerIfAvailable|Logický parametr, který v případě `true` způsobí, že úloha sestavení použije vnitroprocesové objekt kompilátoru, pokud je k dispozici. Tento parametr je používán pouze pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|Utf8output –|Logický parametr, který v případě `true` , protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr je ekvivalentní `/utf8Output` přepínači kompilátoru.|  
|VbcToolPath|Volitelná cesta, která označuje jiné umístění pro vbc.exe, pokud je aktuální verze vbc.exe přepsána.|  
|VbcVerbosity|Určuje podrobnost [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] výstupu kompilátoru. Platné hodnoty jsou "quiet", "normální" (výchozí hodnota) nebo "Verbose".|  
|VisualStudioVersion|Určuje verzi sady Visual Studio, ve které se má tento projekt považovat za spuštěný. Pokud tato vlastnost není zadána, MSBuild ji nastaví na rozumnou výchozí hodnotu.<br /><br /> Tato vlastnost se používá v několika typech projektů k určení sady cílů, které se používají pro sestavení. Pokud `ToolsVersion` je nastaven na 4,0 nebo vyšší pro projekt, `VisualStudioVersion` slouží k určení, kterou dílčí sadu nástrojů použít. Další informace najdete v tématu [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).|  
|WarningsAsErrors|Určuje seznam upozornění, která mají být považována za chyby. Tento parametr je ekvivalentní `/warnaserror` přepínači kompilátoru.|  
|WarningsNotAsErrors|Určuje seznam upozornění, která nejsou považována za chyby. Tento parametr je ekvivalentní `/warnaserror` přepínači kompilátoru.|  
|Win32Manifest|Název souboru manifestu, který má být vložen do konečného sestavení. Tento parametr je ekvivalentní `/win32Manifest` přepínači kompilátoru.|  
|Win32Resource|Název souboru prostředku Win32, který se má vložit do konečného sestavení Tento parametr je ekvivalentní `/win32resource` přepínači kompilátoru.|  
  
## <a name="see-also"></a>Viz také  
 [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
