---
title: Obecné vlastnosti projektu nástroje MSBuild | Microsoft Docs
ms.date: 01/18/2018
ms.topic: reference
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4fd82cee49c698c9244a2851d4e671ae6a94508
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557883"
---
# <a name="common-msbuild-project-properties"></a>Obecné vlastnosti projektu nástroje MSBuild
V následující tabulce jsou uvedeny často používané vlastnosti, které jsou definovány v souborech projektu sady Visual Studio nebo zahrnuté v souborech *. targets* , které poskytuje MSBuild.

 Soubory projektu v aplikaci Visual Studio ( *. csproj*, *. vbproj*, *. vcxproj*a jiné) obsahují kód XML nástroje MSBuild, který se spouští při vytváření projektu pomocí integrovaného vývojového prostředí (IDE). Projekty obvykle importují jeden nebo více souborů *. targets* pro definování svého procesu sestavení. Další informace naleznete v tématu [MSBuild. targets Files](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Seznam společných vlastností a parametrů

| Název vlastnosti nebo parametru | Popis |
|------------------------------------| - |
| AdditionalLibPaths | Určuje další složky, ve kterých mají kompilátory Hledat referenční sestavení. |
| AddModules | Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který kompilujete. Tato vlastnost je ekvivalentní k přepínači `/addModules` kompilátoru. |
| ALToolPath | Cesta, kde lze nalézt *Al. exe* . Tato vlastnost přepíše aktuální verzi *Al. exe* , aby bylo možné použít jinou verzi. |
| ApplicationIcon | Soubor ikony *. ico* , který se předá kompilátoru pro vložení jako ikona Win32. Vlastnost je ekvivalentní k přepínači `/win32icon` kompilátoru. |
| Souboru ApplicationManifest | Určuje cestu k souboru, který se používá ke generování informací o manifestu nástroje řízení externích uživatelských účtů (UAC). Platí pouze pro projekty aplikace Visual Studio cílené [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].<br /><br /> Ve většině případů je manifest vložen. Nicméně pokud používáte nasazení Free COM nebo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Deployment, manifest může být externí soubor, který je nainstalován společně se sestaveními vaší aplikace. Další informace najdete v tomto tématu v vlastnosti NoWin32Manifest. |
| AssemblyOriginatorKeyFile | Určuje soubor, který se používá k podepsání sestavení ( *. snk* nebo *. pfx*) a který je předán [úloze ResolveKeySource –](../msbuild/resolvekeysource-task.md) , aby vygeneroval skutečný klíč, který se používá k podepsání sestavení. |
| AssemblySearchPaths | Seznam umístění, která se mají hledat během překladu referenčního sestavení v době sestavení Pořadí, ve kterém se cesty zobrazují v tomto seznamu, je smysluplné, protože cesty uvedené dříve mají přednost před pozdějšími položkami. |
| Doplňk | Název konečného výstupního sestavení po sestavení projektu. |
| BaseAddress | Určuje základní adresu hlavního výstupního sestavení. Tato vlastnost je ekvivalentní k přepínači `/baseaddress` kompilátoru. |
| BaseIntermediateOutputPath | Složka na nejvyšší úrovni, kde jsou vytvořeny všechny přechodné výstupní složky specifické pro konfiguraci. Výchozí hodnota je `obj\`. Následující kód je příklad: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Určuje základní cestu pro výstupní soubor. Pokud je nastavená, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] použije `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Příklad syntaxe: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Logická hodnota, která označuje, zda jsou odkazy na projekt vytvářeny nebo čištěny paralelně při použití [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] více procesů. Výchozí hodnota je `true`, což znamená, že projekty budou sestaveny paralelně, pokud má systém více jader nebo procesorů. |
| BuildProjectReferences | Logická hodnota, která určuje, zda jsou odkazy na projekt vytvořeny pomocí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Automaticky nastaveno na `false`, pokud sestavíte projekt v integrovaném vývojovém prostředí (IDE) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], `true` Pokud jinak. `-p:BuildProjectReferences=false` můžete zadat na příkazovém řádku, abyste se vyhnuli kontrole, jestli jsou odkazované projekty aktuální. |
| CleanFile | Název souboru, který se použije jako "čistá mezipaměť". Čistá mezipaměť je seznam generovaných souborů, které mají být odstraněny během operace čištění. Soubor je umístěn do mezilehlé výstupní cesty procesem sestavení.<br /><br /> Tato vlastnost určuje pouze názvy souborů, které nemají informace o cestě. |
| Stránky | Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci. Tato vlastnost je ekvivalentní k přepínači `/codepage` kompilátoru. |
| CompilerResponseFile | Volitelný soubor odpovědí, který lze předat úlohám kompilátoru. |
| Konfigurace | Konfigurace, kterou vytváříte, buď "ladit" nebo "Release". |
| CscToolPath | Cesta k souboru *CSc. exe*, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] kompilátorem. |
| CustomBeforeMicrosoftCommonTargets | Název souboru projektu nebo souboru cílů, který má být importován automaticky před importem běžných cílů. |
| DebugSymbols | Logická hodnota, která určuje, zda jsou symboly generovány sestavením.<br /><br /> Nastavení **-p:DebugSymbols = false** na příkazovém řádku zakáže generování souborů symbolů databáze programu (*PDB*). |
| DebugType | Definuje úroveň ladicích informací, které chcete vygenerovat. Platné hodnoty jsou "Full", "pdbonly", "Portable", "Embedded" a "none". |
| DefineConstants | Definuje podmíněné konstanty kompilátoru. Páry symbol/hodnota jsou odděleny středníky a jsou určeny pomocí následující syntaxe:<br /><br /> *symbol1 = hodnota1; symbol2 = hodnota2*<br /><br /> Vlastnost je ekvivalentní k přepínači `/define` kompilátoru. |
| DefineDebug | Logická hodnota, která určuje, zda má být definována konstanta ladění. |
| DefineTrace | Logická hodnota, která určuje, zda má být definována konstanta TRACE. |
| DelaySign | Logická hodnota, která označuje, zda chcete sestavení zpozdit podpisem, nikoli úplným podepsáním. |
| Deterministický | Logická hodnota, která určuje, zda má kompilátor vytvořit identická sestavení pro stejné vstupy. Tento parametr odpovídá `/deterministic`mu přepínači kompilátorů *Vbc. exe* a *CSc. exe* . |
| DisabledWarnings | Potlačí zadaná upozornění. Je třeba zadat pouze číselnou část identifikátoru upozornění. Několik upozornění je odděleno středníky. Tento parametr odpovídá `/nowarn` přepínači kompilátoru *Vbc. exe* . |
| DisableFastUpToDateCheck | Logická hodnota, která se vztahuje pouze na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] správce sestavení používá proces nazvaný FastUpToDateCheck k určení, zda projekt musí být znovu sestaven, aby byl aktuální. Tento proces je rychlejší než použití [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] k jeho určení. Nastavením vlastnosti DisableFastUpToDateCheck na `true` můžete obejít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] správce sestavení a vynutit použití [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] k určení, zda je projekt aktuální. |
| DocumentationFile | Název souboru, který je generován jako soubor dokumentace XML. Tento název obsahuje pouze název souboru a neobsahuje informace o cestě. |
| ErrorReport | Určuje, jak má úloha kompilátoru nahlásit interní chyby kompilátoru. Platné hodnoty jsou "prompt", "Odeslat" nebo "none". Tato vlastnost je ekvivalentní k přepínači `/errorreport` kompilátoru. |
| ExcludeDeploymentUrl | [Úloha GenerateDeploymentManifest –](../msbuild/generatedeploymentmanifest-task.md) Přidá značku deploymentProvider do manifestu nasazení, pokud soubor projektu obsahuje některý z následujících prvků:<br /><br /> - UpdateUrl<br />– InstallUrl<br />- PublishUrl<br /><br /> Pomocí ExcludeDeploymentUrl však můžete zabránit přidání značky deploymentProvider do manifestu nasazení, i když je zadána kterákoli z výše uvedených adres URL. Chcete-li to provést, přidejte do souboru projektu následující vlastnost:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Poznámka:**  ExcludeDeploymentUrl se nezveřejňuje v rozhraní IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a dá se nastavit jenom ruční úpravou souboru projektu. Nastavení této vlastnosti neovlivní publikování v rámci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; To znamená, že značka deploymentProvider bude stále přidána na adresu URL určenou parametrem PublishUrl. |
| Zarovnání. | Určuje, kam se v bajtech mají zarovnat oddíly výstupního souboru. Platné hodnoty jsou 512, 1024, 2048, 4096, 8192. Tato vlastnost je ekvivalentní k přepínači `/filealignment` kompilátoru. |
| FrameworkPathOverride | Určuje umístění *knihovny mscorlib. dll* a *Microsoft. VisualBasic. dll*. Tento parametr je ekvivalentní `/sdkpath` přepínači kompilátoru *Vbc. exe* . |
| GenerateDocumentation | (C#, Visual Basic) Logický parametr, který označuje, zda je dokumentace generována sestavením. Pokud `true`, sestavení vygeneruje informace o dokumentaci a umístí je do souboru *. XML* spolu s názvem spustitelného souboru nebo knihovny, kterou vytvořil úkol sestavení. |
| GenerateFullPaths | (C#) Vygenerujte úplné cesty pro názvy souborů ve výstupu pomocí možnosti kompilátoru [-fullpaths –](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) . |
| GenerateSerializationAssemblies | Určuje, zda by měla být sestavení serializace XML generována nástrojem *Sgen. exe*, který lze nastavit na hodnotu on, auto nebo off. Tato vlastnost se používá pouze pro sestavení, která cílí pouze na .NET Framework. Chcete-li generovat sestavení serializace XML pro sestavení .NET Standard nebo .NET Core, odkazujte na balíček NuGet *Microsoft. XmlSerializer. Generator* . |
| IntermediateOutputPath | Úplná zprostředkující výstupní cesta odvozená od `BaseIntermediateOutputPath`, pokud není zadána žádná cesta. Například *\obj\debug\\* . |
| KeyContainerName | Název kontejneru klíčů se silným názvem. |
| KeyOriginatorFile | Název souboru klíče se silným názvem. |
| ModuleAssemblyName | Název sestavení, do kterého má být kompilovaný modul začleněn. Vlastnost je ekvivalentní k přepínači `/moduleassemblyname` kompilátoru. |
| MSBuildProjectExtensionsPath | Určuje cestu, kde se nachází rozšíření projektu. Ve výchozím nastavení má tato hodnota stejnou hodnotu jako `BaseIntermediateOutputPath`. |
| NoLogo | Logická hodnota, která označuje, zda má být vypnuto logo kompilátoru. Tato vlastnost je ekvivalentní k přepínači `/nologo` kompilátoru. |
| NoStdLib | Logická hodnota, která označuje, zda se má vyhýbat odkazování na standardní knihovnu (*mscorlib. dll*). Výchozí hodnota je `false`. |
| NoVBRuntimeReference | Logická hodnota, která označuje, zda [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] modul runtime (*Microsoft. VisualBasic. dll*) by měl být zahrnut jako odkaz v projektu. |
| NoWin32Manifest | Logická hodnota, která označuje, zda informace o manifestu nástroje řízení uživatelských účtů (UAC) budou vloženy do spustitelného souboru aplikace. Platí pouze pro projekty aplikace Visual Studio cílené [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. V projektech nasazených pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a modelu COM bez registrace se tento element ignoruje. `False` (výchozí hodnota) určuje, že informace o manifestu nástroje řízení uživatelských účtů (UAC) budou vloženy do spustitelného souboru aplikace. `True` určuje, že informace o manifestu nástroje řízení uživatelských účtů nebudou vloženy.<br /><br /> Tato vlastnost se vztahuje pouze na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekty cílené na [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. V projektech nasazených pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a modelu COM bez registrace je tato vlastnost ignorována.<br /><br /> NoWin32Manifest byste měli přidat pouze v případě, že nechcete, aby [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do spustitelného souboru aplikace vkládat žádné informace o manifestu. Tento proces se nazývá *virtualizace*. Pokud chcete použít virtualizaci, nastavte `<ApplicationManifest>` ve spojení s `<NoWin32Manifest>` následujícím způsobem:<br /><br /> – Pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty odeberte `<ApplicationManifest>` uzel. (V [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty `<NoWin32Manifest>` je ignorováno, pokud existuje `<ApplicationManifest>` uzel.)<br />– Pro projekty [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nastavte `<ApplicationManifest>` na `False` a `<NoWin32Manifest>` na `True`. (V [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektech `<ApplicationManifest>` Přepisuje `<NoWin32Manifest>`.)<br /> Tato vlastnost je ekvivalentní k přepínači `/nowin32manifest` kompilátoru *Vbc. exe*. |
| Optimalizace | Logická hodnota, která Pokud je nastavena na `true`, umožňuje optimalizace kompilátoru. Tato vlastnost je ekvivalentní k přepínači `/optimize` kompilátoru. |
| OptionCompare – | Určuje, jak se provádí porovnávání řetězců. Platné hodnoty jsou "Binary" nebo "text". Tato vlastnost je ekvivalentní k přepínači `/optioncompare` kompilátoru *Vbc. exe*. |
| OptionExplicit – | Logická hodnota, která Pokud je nastavena na `true`, vyžaduje explicitní deklaraci proměnných ve zdrojovém kódu. Tato vlastnost je ekvivalentní k přepínači `/optionexplicit` kompilátoru. |
| Optioninfer – | Logická hodnota, která Pokud je nastavena na `true`, umožňuje odvozování typů proměnných. Tato vlastnost je ekvivalentní k přepínači `/optioninfer` kompilátoru. |
| OptionStrict – | Logická hodnota, která Pokud je nastavena na `true`, způsobí, že úloha sestavení vynutí striktní sémantiku typu pro omezení implicitních převodů typu. Tato vlastnost je ekvivalentní `/optionstrict` přepínači kompilátoru *Vbc. exe* . |
| OutDir | Označuje konečné výstupní umístění projektu nebo řešení. Při sestavování řešení lze OutDir použít ke shromáždění více výstupů projektu na jednom místě. Kromě toho je OutDir zahrnut v AssemblySearchPaths, který se používá pro překládání odkazů. Například *bin\Debug*. |
| OutputPath | Určuje cestu k výstupnímu adresáři vzhledem k adresáři projektu, například *bin\Debug*. |
| OutputType | Určuje formát výstupního souboru. Tento parametr může mít jednu z následujících hodnot:<br /><br /> Knihovna. Vytvoří knihovnu kódu. (Výchozí hodnota.)<br />Programu. Vytvoří konzolovou aplikaci.<br />Čipu. Vytvoří modul.<br />Winexe. Vytvoří program založený na systému Windows.<br /><br /> Tato vlastnost je ekvivalentní `/target` přepínači kompilátoru *Vbc. exe* . |
| OverwriteReadOnlyFiles | Logická hodnota, která označuje, zda chcete povolit sestavení pro přepsání souborů jen pro čtení nebo spuštění chyby. |
| PathMap | Určuje, jak namapovat fyzické cesty na výstup názvů zdrojových cest kompilátorem. Tato vlastnost je ekvivalentní `/pathmap` přepínači kompilátoru *CSc. exe* . |
| PdbFile | Název souboru *. pdb* , který vysíláte. Tato vlastnost je ekvivalentní `/pdb` přepínači kompilátoru *CSc. exe* . |
| Platforma | Operační systém, pro který sestavíte. Platné hodnoty jsou "any CPU", "x86" a "x64". |
| ProcessorArchitecture | Architektura procesoru, která se používá, když jsou přeloženy odkazy na sestavení. Platné hodnoty jsou "MSIL", "x86", "amd64" nebo "ia64". |
| ProduceOnlyReferenceAssembly | Logická hodnota, která instruuje kompilátor, aby vygenerovala pouze referenční sestavení namísto zkompilovaného kódu. Nelze použít ve spojení s `ProduceReferenceAssembly`.  Tato vlastnost odpovídá `/refonly`mu přepínači kompilátorů *Vbc. exe* a *CSc. exe* . |
| ProduceReferenceAssembly | Logická hodnota, která Pokud je nastavena na `true` povolí výrobu [referenčních sestavení](/dotnet/standard/assembly/reference-assemblies) pro aktuální sestavení. Při použití této funkce by se měla `true` `Deterministic`. Tato vlastnost odpovídá `/refout`mu přepínači kompilátorů *Vbc. exe* a *CSc. exe* . |
| RemoveIntegerChecks | Logická hodnota, která označuje, zda se mají zakázat kontroly chyb přetečení celých čísel. Výchozí hodnota je `false`. Tato vlastnost je ekvivalentní `/removeintchecks` přepínači kompilátoru *Vbc. exe* . |
| RootNamespace | Kořenový obor názvů, který se má použít při pojmenování vloženého prostředku. Tento obor názvů je součástí názvu vloženého manifestu prostředku. |
| Satellite_AlgorithmId | ID algoritmu hash *Al. exe* , který má být použit při vytváření satelitních sestavení. |
| Satellite_BaseAddress | Základní adresa, která se použije v případě satelitních sestavení specifických pro jazykovou verzi, se vytváří pomocí cíle `CreateSatelliteAssemblies`. |
| Satellite_CompanyName | Název společnosti, který se má předat *Al. exe* během vytváření satelitních sestavení. |
| Satellite_Configuration | Název konfigurace, který se má předat *Al. exe* během vytváření satelitních sestavení. |
| Satellite_Description | Text popisu, který se má předat souboru *Al. exe* během vytváření satelitních sestavení. |
| Satellite_EvidenceFile | Vloží zadaný soubor do satelitního sestavení, které má název prostředku "Security. evidence". |
| Satellite_FileVersion | Určuje řetězec pro pole verze souboru v satelitním sestavení. |
| Satellite_Flags | Určuje hodnotu pro pole flags v satelitním sestavení. |
| Satellite_GenerateFullPaths | Způsobí, že úloha sestavení použije absolutní cesty pro všechny soubory hlášené v chybové zprávě. |
| Satellite_LinkResource | Propojí zadané soubory prostředků se satelitním sestavením. |
| Satellite_MainEntryPoint | Určuje plně kvalifikovaný název (tj. Class. Method) metody pro použití jako vstupní bod při převodu modulu na spustitelný soubor během generování satelitního sestavení. |
| Satellite_ProductName | Určuje řetězec pro pole produktu v satelitním sestavení. |
| Satellite_ProductVersion | Určuje řetězec pro pole ProductVersion v satelitním sestavení. |
| Satellite_TargetType | Určuje formát výstupního souboru satelitního sestavení jako "Library", "exe" nebo "Win". Výchozí hodnota je "Library". |
| Satellite_Title | Určuje řetězec pro pole title v satelitním sestavení. |
| Satellite_Trademark | Určuje řetězec pro pole ochranné známky v satelitním sestavení. |
| Satellite_Version | Určuje informace o verzi satelitního sestavení. |
| Satellite_Win32Icon | Vloží soubor ikony *. ico* do satelitního sestavení. |
| Satellite_Win32Resource | Vloží prostředek systému Win32 (soubor *. res* ) do satelitního sestavení. |
| SGenToolPath | Volitelná cesta nástroje, která označuje, kde získat *Sgen. exe* , když je aktuální verze *Sgen. exe* přepsána. Tato vlastnost se používá jenom pro .NET Framework.|
| SGenUseProxyTypes | Logická hodnota, která určuje, zda mají být typy proxy generovány pomocí *Sgen. exe*. To platí jenom v případě, že je *GenerateSerializationAssemblies* nastavené na zapnuto a jenom pro .NET Framework.<br /><br /> Cíl SGen používá tuto vlastnost k nastavení příznaku UseProxyTypes. Tato vlastnost je nastavena na hodnotu true a neexistuje žádné uživatelské rozhraní, které by bylo možné změnit. Chcete-li vygenerovat sestavení serializace pro typy non-WebService, přidejte tuto vlastnost do souboru projektu a nastavte ji na false před importem *Microsoft. Common. targets* nebo  *C#/VB.targets*. |
| StartupObject | Určuje třídu nebo modul, který obsahuje metodu Main nebo Sub Main Procedure. Tato vlastnost je ekvivalentní k přepínači `/main` kompilátoru. |
| SubsystemVersion | Určuje minimální verzi subsystému, kterou může vygenerovaný spustitelný soubor použít. Tato vlastnost je ekvivalentní k přepínači `/subsystemversion` kompilátoru. Informace o výchozí hodnotě této vlastnosti naleznete v tématu [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) nebo [/subsystemversion (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Verze prostředí .NET Compact Framework potřebná ke spuštění aplikace, kterou vytváříte. Zadáním této možnosti můžete odkazovat na konkrétní sestavení rozhraní, která pravděpodobně nebudete moci odkazovat jinak. |
| TargetFrameworkVersion | Verze .NET Framework potřebná ke spuštění aplikace, kterou vytváříte. Zadáním této možnosti můžete odkazovat na konkrétní sestavení rozhraní, která pravděpodobně nebudete moci odkazovat jinak. |
| TreatWarningsAsErrors | Logický parametr, který při `true`způsobí, že všechna upozornění budou považována za chyby. Tento parametr je ekvivalentní k přepínači `/nowarn` kompilátoru. |
| UseHostCompilerIfAvailable | Logický parametr, který Pokud `true`, způsobí, že úloha sestavení použije vnitroprocesové objekt kompilátoru, pokud je k dispozici. Tento parametr je používán pouze pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| Utf8output – | Logický parametr, který Pokud `true`, protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr je ekvivalentní k přepínači `/utf8Output` kompilátoru. |
| VbcToolPath | Volitelná cesta, která označuje jiné umístění pro *Vbc. exe* , když je aktuální verze *Vbc. exe* přepsána. |
| VbcVerbosity | Určuje podrobnost výstupu kompilátoru [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Platné hodnoty jsou "quiet", "normální" (výchozí hodnota) nebo "Verbose". |
| VisualStudioVersion | Určuje verzi sady Visual Studio, ve které se má tento projekt považovat za spuštěný. Pokud tato vlastnost není zadána, MSBuild ji nastaví na rozumnou výchozí hodnotu.<br /><br /> Tato vlastnost se používá v několika typech projektů k určení sady cílů, které se používají pro sestavení. Pokud je `ToolsVersion` nastaveno na 4,0 nebo vyšší pro projekt, `VisualStudioVersion` se používá k určení, kterou dílčí sadu nástrojů použít. Další informace najdete v tématu [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Určuje seznam upozornění, která mají být považována za chyby. Tento parametr je ekvivalentní k přepínači `/warnaserror` kompilátoru. |
| WarningsNotAsErrors | Určuje seznam upozornění, která nejsou považována za chyby. Tento parametr je ekvivalentní k přepínači `/warnaserror` kompilátoru. |
| Win32Manifest | Název souboru manifestu, který má být vložen do konečného sestavení. Tento parametr je ekvivalentní k přepínači `/win32Manifest` kompilátoru. |
| Win32Resource | Název souboru prostředku Win32, který se má vložit do konečného sestavení Tento parametr je ekvivalentní k přepínači `/win32resource` kompilátoru. |

## <a name="see-also"></a>Viz také
- [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
