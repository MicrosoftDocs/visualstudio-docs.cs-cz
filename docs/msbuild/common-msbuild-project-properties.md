---
title: Obecné vlastnosti projektu nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2018
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe2c39fc08528886e143bd51eb1f33219b386807
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921714"
---
# <a name="common-msbuild-project-properties"></a>Obecné vlastnosti projektu nástroje MSBuild
V následující tabulce je často používané seznamy vlastností, které jsou definovány v souborech projektu sady Visual Studio nebo součástí *.targets* soubory, které poskytuje nástroj MSBuild.  
  
 Soubory v sadě Visual Studio projektu (*.csproj*, *.vbproj*, *.vcxproj*a jiné) obsahují kód XML nástroje MSBuild, která se spouští při vytváření projektu pomocí rozhraní IDE. Projekty obvykle importují jeden nebo více *.targets* soubory pro definování jejich procesu sestavení. Další informace najdete v tématu [MSBuild – soubory .targets](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Seznam běžných vlastností a parametrů  
  
| Název vlastnosti nebo parametr | Popis |
|------------------------------------| - |
| AdditionalLibPaths | Určuje další složky, ve kterých by měly kompilátory hledat referenční sestavení. |
| AddModules | Způsobí, že kompilátor zpřístupní všechny typové informace ze zadaných souborů pro projekt, který je aktuálně kompilován. Tato vlastnost je ekvivalentní `/addModules` přepínač kompilátoru. |
| ALToolPath | Cesta kde *AL.exe* najdete. Tato vlastnost přepíše aktuální verzi *AL.exe* povolit používání jiné verze. |
| ApplicationIcon | *.Ico* soubor ikony pro předání kompilátoru k vložení v podobě ikony Win32. Vlastnost je ekvivalentní `/win32icon` přepínač kompilátoru. |
| ApplicationManifest | Určuje cestu k souboru, který se používá ke generování manifestu informace externí řízení uživatelských účtů (UAC). Platí pouze pro projekty Visual Studio, které jsou zacílené [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].<br /><br /> Ve většině případů je manifest vložený. Nicméně pokud použijete COM bez registrace nebo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení a manifest může být externí soubor, který je nainstalován společně s vaším sestavením aplikace. Další informace viz vlastnost NoWin32Manifest v tomto tématu. |
| Neexistence souboru AssemblyOriginatorKeyFile | Určuje soubor, který se používá k podepsání sestavení (*.snk* nebo *.pfx*) a který je předán [resolvekeysource – úloha](../msbuild/resolvekeysource-task.md) k vygenerování skutečného klíče, který se používá k podepsání sestavení. |
| AssemblySearchPaths | Seznam umístění pro hledání sestavení referenční sestavení řešení. Pořadí, ve kterém se cesty zobrazují v tomto seznamu má smysl, protože výše uvedené cesty má přednost před pozdějšími položkami. |
| AssemblyName | Název finálního výstupního sestavení po sestavení projektu. |
| Vlastnost BaseAddress | Určuje základní adresu hlavního výstupního sestavení. Tato vlastnost je ekvivalentní `/baseaddress` přepínač kompilátoru. |
| BaseOutputPath | Specifikuje základní cestu pro výstupní soubor. Pokud je nastavena, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] použije `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Příklad syntaxe: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BaseIntermediateOutputPath | Složky nejvyšší úrovně, kde jsou vytvořeny všechny složky zprostředkujících výstupů specifické konfigurace. Výchozí hodnota je `obj\`. Následující kód je příklad: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BuildInParallel | Logická hodnota, která označuje, zda odkazy na projekt jsou vytvořeny nebo vyčištěny paralelně při více procesů [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se používá. Výchozí hodnota je `true`, což znamená, že projekty budou vytvořeny paralelně, pokud systém obsahuje více jader nebo procesorů. |
| BuildProjectReferences | Logická hodnota, která určuje, zda jsou odkazy na projekt vytvořil [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Automaticky nastaví na `false` Pokud vytváříte projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE), `true` -li jinak. `-p:BuildProjectReferences=false` můžete zadat na příkazovém řádku, aby se zabránilo kontroluje se, že odkazované projekty jsou aktuální. |
| CleanFile | Název souboru, který se použije jako "čistá mezipaměť." Čistá mezipaměť je seznam vygenerovaných souborů mají být odstraněny během operace čištění. Soubor je umístěn v mezilehlé výstupní cestě procesem sestavení.<br /><br /> Tato vlastnost určuje pouze názvy souborů, které nemají informace o cestě. |
| Znaková stránka | Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace. Tato vlastnost je ekvivalentní `/codepage` přepínač kompilátoru. |
| CompilerResponseFile | Soubor volitelných odpovědí může být předán úkolům kompilátoru. |
| Konfigurace | Konfigurace, který vytváříte, buď "Ladění" nebo "Verze". |
| CscToolPath | Cesta k *csc.exe*, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] kompilátoru. |
| CustomBeforeMicrosoftCommonTargets | Název souboru projektu nebo soubor cílů, které mají být importovány automaticky před importem společných cílů. |
| DebugSymbols | Logická hodnota, která určuje, zda jsou symboly generovány sestavením.<br /><br /> Nastavení **- p: DebugSymbols = false** na příkazovém řádku zakáže generování databázi programu (*PDB*) soubory symbolů. |
| DefineConstants | Definuje podmíněné konstanty kompilátoru. Dvojice symbol/hodnota jsou odděleny středníkem a jsou zadány pomocí následující syntaxe:<br /><br /> *symbol1 = value1; symbol2 = hodnota2*<br /><br /> Vlastnost je ekvivalentní `/define` přepínač kompilátoru. |
| DefineDebug | Logická hodnota, která určuje, zda má být definována konstanta DEBUG. |
| DefineTrace | Logická hodnota, která určuje, zda má být definována konstanta TRACE. |
| DebugType | Definuje úroveň ladění informací, které mají být vygenerovány. Platné hodnoty jsou "full", "pdbonly" a "none". |
| DelaySign | Logická hodnota, která určuje, zda se má k zpožděný podpis sestavení místo úplného podepsání. |
| Deterministické | Logická hodnota, která určuje, zda kompilátor by měl vytvářet identické sestavení pro stejné vstupy. Tento parametr `/deterministic` přepnout z *vbc.exe* a *csc.exe* kompilátory. |
| DisabledWarnings | Potlačí zadaná upozornění. Je třeba zadat pouze číselnou část identifikátoru upozornění. Více varování je odděleno středníky. Tento parametr `/nowarn` přepnout z *vbc.exe* kompilátoru. |
| DisableFastUpToDateCheck | Logická hodnota, která se vztahuje na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pouze. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Sestavení správce používá proces nazývaný FastUpToDateCheck ke zjištění, zda projekt musíte znovu sestavit, aby byl aktuální. Tento proces je rychlejší než použití [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ke zjištění. Nastavení vlastnosti DisableFastUpToDateCheck na `true` umožňuje obejít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] správce sestavení a vynutit používání [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] k určení, zda je aktuální projekt. |
| DocumentationFile | Název souboru, který je generován jako soubor dokumentace XML. Tento název zahrnuje pouze název souboru a neobsahuje žádné informace o cestě. |
| ErrorReport | Určuje, jak by měl úkol kompilátor ohlásit interní chyby kompilátoru. Platné hodnoty jsou "prompt", "Odeslat" nebo "none". Tato vlastnost je ekvivalentní `/errorreport` přepínač kompilátoru. |
| ExcludeDeploymentUrl | [Generatedeploymentmanifest – úloha](../msbuild/generatedeploymentmanifest-task.md) Přidá značku deploymentProvider do manifestu nasazení, pokud soubor projektu obsahuje některé z následujících elementů:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Pomocí ExcludeDeploymentUrl však můžete zabránit značku deploymentProvider přidávaný do manifestu nasazení i v případě, že některé z výše uvedených adres URL zadán. Provedete to tak, přidejte do souboru projektu následující vlastnost:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Poznámka:** ExcludeDeploymentUrl není vystaveno v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí a je možné nastavit pouze ruční úpravou souboru projektu. Nastavení této vlastnosti neovlivňuje publikování v rámci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; to znamená, že značka deploymentProvider bude i tak přidána k adrese URL zadané hodnotou PublishUrl. |
| Hodnotu FileAlignment | Určuje, v bajtech, kam chcete zarovnat oddíly výstupního souboru. Platné hodnoty jsou 512, 1024, 2048, 4096, 8192. Tato vlastnost je ekvivalentní `/filealignment` přepínač kompilátoru. |
| FrameworkPathOverride | Určuje umístění *mscorlib.dll* a *microsoft.visualbasic.dll*. Tento parametr je ekvivalentní `/sdkpath` přepnout z *vbc.exe* kompilátoru. |
| GenerateDocumentation | (Pouze Visual Basic) Parametr logické hodnoty označující, zda je dokumentace generovaná sestavením. Pokud `true`, sestavení generuje informace o dokumentaci a vloží je *.xml* soubor společně s názvem spustitelného souboru nebo knihovnu, která úkol sestavení vytvořen. |
| IntermediateOutputPath | Úplná cesta zprostředkujících výstupů odvozena z `BaseIntermediateOutputPath`, pokud není zadaná žádná cesta. Například *\obj\debug\\*. |
| KeyContainerName | Název kontejneru klíčů se silným názvem. |
| KeyOriginatorFile | Název souboru klíče silného názvu. |
| MSBuildProjectExtensionsPath | Určuje cestu, kde se nachází projektu rozšíření. Ve výchozím nastavení, tato akce trvá stejnou hodnotu jako `BaseIntermediateOutputPath`. |
| ModuleAssemblyName | Název sestavení, který má být zahrnut do je zkompilovaný modul. Vlastnost je ekvivalentní `/moduleassemblyname` přepínač kompilátoru. |
| NoLogo | Logická hodnota určující, zda chcete, aby bylo vypnuto logo kompilátoru. Tato vlastnost je ekvivalentní `/nologo` přepínač kompilátoru. |
| NoStdLib | Logická hodnota určující, zda-li zabránit odkazování standardní knihovnu (*mscorlib.dll*). Výchozí hodnota je `false`. |
| NoVBRuntimeReference | Logická hodnota, která určuje, zda [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] modulu runtime (*Microsoft.VisualBasic.dll*) by měl být zahrnut jako odkaz v projektu. |
| NoWin32Manifest | Logická hodnota, která určuje, zda informace o manifestu řízení uživatelských účtů (UAC) budou vloženy do aplikace spustitelného souboru. Platí pouze pro projekty Visual Studio, které jsou zacílené [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. V projektech, které jsou nasazeny pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a COM bez registrace, tento prvek je ignorován. `False` (výchozí hodnota) určuje, že spustitelný soubor aplikace vložit informace o manifestu řízení uživatelských účtů (UAC). `True` Určuje, že informace o manifestu nástroje Řízení uživatelských účtů nebudou vloženy.<br /><br /> Tato vlastnost se týká pouze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekty cílení [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. V projektech, které jsou nasazeny pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a COM bez registrace, tato vlastnost se ignoruje.<br /><br /> Měli byste přidat NoWin32Manifest pouze v případě, že nechcete, aby [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pro vložení manifestu všechny informace v aplikaci spustitelného souboru; tento proces se nazývá *virtualizace*. Pro použití virtualizace nastavte `<ApplicationManifest>` ve spojení s `<NoWin32Manifest>` následujícím způsobem:<br /><br /> -Pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty, odeberte `<ApplicationManifest>` uzlu. (V [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty, `<NoWin32Manifest>` ignorováno, pokud `<ApplicationManifest>` uzel existuje.)<br />-Pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektů, nastavte `<ApplicationManifest>` k `False` a `<NoWin32Manifest>` k `True`. (V [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekty, `<ApplicationManifest>` přepíše `<NoWin32Manifest>`.)<br /> Tato vlastnost je ekvivalentní `/nowin32manifest` přepínači kompilátoru *vbc.exe*. |
| Optimalizace | Logická hodnota, která pokud je nastavena na `true`, povolí optimalizace kompilátoru. Tato vlastnost je ekvivalentní `/optimize` přepínač kompilátoru. |
| OptionCompare | Určuje způsob porovnávání řetězců. Platné hodnoty jsou "binární" nebo "text". Tato vlastnost je ekvivalentní `/optioncompare` přepínači kompilátoru *vbc.exe*. |
| OptionExplicit | Logická hodnota, která pokud je nastavena na `true`, vyžaduje explicitní deklaraci proměnných ve zdrojovém kódu. Tato vlastnost je ekvivalentní `/optionexplicit` přepínač kompilátoru. |
| OptionInfer | Logická hodnota, která pokud je nastavena na `true`, povolí odvozování typů proměnných. Tato vlastnost je ekvivalentní `/optioninfer` přepínač kompilátoru. |
| OptionStrict | Logická hodnota, která pokud je nastavena na `true`, způsobí, že úkol sestavení vynutí sémantiku přísného typu pro omezení převodů implicitních typů. Tato vlastnost je ekvivalentní `/optionstrict` přepnout z *vbc.exe* kompilátoru. |
| OutputPath | Určuje cestu k výstupnímu adresáři relativně vzhledem k adresáři projektu, například *bin\Debug*. |
| Element OutputType | Určuje formát výstupního souboru. Tento parametr může mít jednu z následujících hodnot:<br /><br /> -Knihovny. Vytvoří knihovnu kódu. (Výchozí hodnota.)<br />-Exe. Vytvoří konzolovou aplikaci.<br />-Module. Vytvoří modul.<br />-Winexe. Vytvoří program pro systém Windows.<br /><br /> Tato vlastnost je ekvivalentní `/target` přepnout z *vbc.exe* kompilátoru. |
| OverwriteReadOnlyFiles | Logická hodnota, která určuje, zda chcete povolit sestavení přepsat soubory jen pro čtení nebo vyvolat chybu. |
| PdbFile | Název souboru *PDB* soubor, který emitujete. Tato vlastnost je ekvivalentní `/pdb` přepnout z *csc.exe* kompilátoru. |
| Platforma | Operační systém, který vytváříte. Platné hodnoty jsou "Any CPU", "x 86" a "x64". |
| ProduceReferenceAssembly | Logická hodnota, která pokud je nastavena na `true` umožňuje produkce [odkazovat na sestavení](https://github.com/dotnet/roslyn/blob/master/docs/features/refout.md) pro aktuální sestavení. `Deterministic` by měl být `true` při použití této funkce. Tato vlastnost odpovídá `/refout` přepnout z *vbc.exe* a *csc.exe* kompilátory. |
| RemoveIntegerChecks | Logická hodnota určující, zda chcete zakázat chyby kontroly přetečení celých čísel. Výchozí hodnota je `false`. Tato vlastnost je ekvivalentní `/removeintchecks` přepnout z *vbc.exe* kompilátoru. |
| SGenUseProxyTypes | Logická hodnota, která určuje, zda typy proxy měly být generovány pomocí *SGen.exe*.<br /><br /> Cíl SGen používá tuto vlastnost pro nastavení příznaku UseProxyTypes. Výchozí hodnota této vlastnosti na hodnotu true a neexistuje žádné uživatelské rozhraní pro toto nastavení změnit. Generovat sestavení serializace pro typy bez, přidejte do souboru projektu tuto vlastnost a nastavte ji na hodnotu false před importem *cílů Microsoft.Common.Targets* nebo *webových*. |
| SGenToolPath | Volitelný nástroj pro cestu, která označuje, kde můžete získat *SGen.exe* při aktuální verzi *SGen.exe* je přepsána. |
| StartupObject | Určuje třídu nebo modul, který obsahuje metodu Main nebo Sub Main proceduru. Tato vlastnost je ekvivalentní `/main` přepínač kompilátoru. |
| Vlastnost ProcessorArchitecture | Architektura procesoru, který se používá, když jsou překládány odkazy na sestavení. Platné hodnoty jsou "msil", "x86," "amd64" nebo "ia64". |
| RootNamespace | Kořenový obor názvů použijte, pokud pojmenujete integrovaný zdroj. Tento obor názvů je částí názvu vloženého manifestu prostředků. |
| Satellite_AlgorithmId | ID *AL.exe* algoritmu pro použití při vytváření satelitních sestavení. |
| Satellite_BaseAddress | Základní adresa pro použití při satelitní sestavení specifická pro jazykovou verzi jsou vytvořeny pomocí `CreateSatelliteAssemblies` cíl. |
| Satellite_CompanyName | Název společnosti, který má být předán *AL.exe* během vytváření satelitních sestavení. |
| Satellite_Configuration | Název konfigurace má být předán *AL.exe* během vytváření satelitních sestavení. |
| Satellite_Description | Text popisu, který má být předán *AL.exe* během vytváření satelitních sestavení. |
| Satellite_EvidenceFile | Vloží zadaný soubor do satelitního sestavení, který má název prostředku "Security.Evidence". |
| Satellite_FileVersion | Určuje řetězec pro pole verze souboru v satelitním sestavení. |
| Satellite_Flags | Určuje hodnotu pro pole Flags v satelitním sestavení. |
| Satellite_GenerateFullPaths | Způsobí, že úkol sestavení použije absolutní cesty pro všechny soubory uvedeny v chybové zprávě. |
| Satellite_LinkResource | Propojí určené soubory prostředků se satelitním sestavením. |
| Satellite_MainEntryPoint | Určuje plně kvalifikovaný název (tj. class.method) metody pro použití jako vstupní bod při převodu modulu na spustitelný soubor během vytváření satelitních sestavení. |
| Satellite_ProductName | Určuje řetězec pro pole produktu v satelitním sestavení. |
| Satellite_ProductVersion | Určuje řetězec pro pole ProductVersion v satelitním sestavení. |
| Satellite_TargetType | Určuje formát výstupního souboru satelitní sestavení jako "knihovna," "řetězec exe", nebo "win". Výchozí hodnota je "library". |
| Satellite_Title | Určuje řetězec pro pole Title v satelitním sestavení. |
| Satellite_Trademark | Určuje řetězec pro pole Trademark v satelitním sestavení. |
| Satellite_Version | Určuje informace o verzi satelitního sestavení. |
| Satellite_Win32Icon | Vloží *.ico* soubor ikony v satelitním sestavení. |
| Satellite_Win32Resource | Vloží prostředek systému Win32 (*.res* soubor) do satelitního sestavení. |
| SubsystemVersion | Určuje minimální verzi podsystému, který může používat vygenerovaný spustitelný soubor. Tato vlastnost je ekvivalentní `/subsystemversion` přepínač kompilátoru. Informace o výchozí hodnota této vlastnosti naleznete v tématu [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) nebo [/subsystemversion (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Verze .NET Compact Framework, která je nutná ke spuštění aplikace, kterou vytváříte. Určení tohoto umožňuje odkazovat na určitá sestavení rozhraní, které nelze odkazovat, jinak. |
| Parametr targetFrameworkVersion | Verze [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , který se vyžaduje pro spuštění aplikace, kterou vytváříte. Určení tohoto umožňuje odkazovat na určitá sestavení rozhraní, které nelze odkazovat, jinak. |
| TreatWarningsAsErrors | Parametr logické hodnoty, pokud `true`, způsobí, že všechna upozornění budou považována za chyby. Tento parametr je ekvivalentní `/nowarn` přepínač kompilátoru. |
| UseHostCompilerIfAvailable | Parametr logické hodnoty, pokud `true`, způsobí, že úkol sestavení použije objekt vnitroprocesového kompilátoru, pokud je k dispozici. Tento parametr je používán pouze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| Utf8Output | Parametr logické hodnoty, pokud `true`, protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr je ekvivalentní `/utf8Output` přepínač kompilátoru. |
| VbcToolPath | Volitelná cesta označuje jiné umístění pro *vbc.exe* při aktuální verzi *vbc.exe* je přepsána. |
| VbcVerbosity | Určuje úroveň podrobností [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] výstupu kompilátoru. Platné hodnoty jsou "Quiet", "Normal" (výchozí hodnota), nebo "Verbose". |
| VisualStudioVersion | Určuje verzi sady Visual Studio, pod kterým tohoto projektu by měly být považovány za aplikace běžící. Pokud není tato vlastnost určena, nástroj MSBuild ji nastaví na rozumnou výchozí hodnotu.<br /><br /> Tato vlastnost se používá v několika typech projektů pro určení sady cílů, které se používají pro sestavení. Pokud `ToolsVersion` je nastavena na hodnotu 4.0 nebo vyšší pro projekt, `VisualStudioVersion` slouží k určení, které dílčí nástroje použít. Další informace najdete v tématu [sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Označí seznam upozornění pro nakládání s chybami. Tento parametr je ekvivalentní `/warnaserror` přepínač kompilátoru. |
| WarningsNotAsErrors | Označí seznam upozornění, která nemají být považována za chyby. Tento parametr je ekvivalentní `/warnaserror` přepínač kompilátoru. |
| Win32Manifest | Název souboru manifestu, který má být vložen v konečném sestavení. Tento parametr je ekvivalentní `/win32Manifest` přepínač kompilátoru. |
| Win32Resource | Název souboru prostředků Win32, který má být vložen v konečném sestavení. Tento parametr je ekvivalentní `/win32resource` přepínač kompilátoru. |
  
## <a name="see-also"></a>Viz také:  
 [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
