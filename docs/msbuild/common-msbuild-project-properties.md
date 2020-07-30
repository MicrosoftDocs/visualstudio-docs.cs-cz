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
ms.openlocfilehash: 08c790af5504c902bf5fe37d2cddba9b9f63aa40
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425365"
---
# <a name="common-msbuild-project-properties"></a>Obecné vlastnosti projektu nástroje MSBuild

V následující tabulce jsou uvedeny často používané vlastnosti, které jsou definovány v souborech projektu sady Visual Studio nebo zahrnuté v souborech *. targets* , které poskytuje MSBuild.

 Soubory projektu v aplikaci Visual Studio (*. csproj*, *. vbproj*, *. vcxproj*a jiné) obsahují kód XML nástroje MSBuild, který se spouští při vytváření projektu pomocí integrovaného vývojového prostředí (IDE). Projekty obvykle importují jeden nebo více souborů *. targets* pro definování svého procesu sestavení. Další informace naleznete v tématu [MSBuild. targets Files](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Seznam společných vlastností a parametrů

| Název vlastnosti nebo parametru | Typy projektů | Popis |
|------------------------------------| - | - |
| AdditionalLibPaths | .NET | Určuje další složky, ve kterých mají kompilátory Hledat referenční sestavení. |
| AddModules | .NET | Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který kompilujete. Tato vlastnost je ekvivalentní `/addModules` přepínači kompilátoru. |
| ALToolPath | .NET | Cesta, kde lze nalézt *AL.exe* . Tato vlastnost přepíše aktuální verzi *AL.exe* , aby bylo možné použít jinou verzi. |
| ApplicationIcon | .NET | Soubor ikony *. ico* , který se předá kompilátoru pro vložení jako ikona Win32. Vlastnost je ekvivalentní `/win32icon` přepínači kompilátoru. |
| Souboru ApplicationManifest | Vše | Určuje cestu k souboru, který se používá ke generování informací o manifestu nástroje řízení externích uživatelských účtů (UAC). Platí pouze pro projekty aplikace Visual Studio cílené na systém Windows Vista.<br /><br /> Ve většině případů je manifest vložen. Nicméně pokud používáte registraci bezplatného modelu COM nebo ClickOnce, manifest může být externí soubor, který je nainstalován společně se sestaveními vaší aplikace. Další informace najdete v tomto tématu v vlastnosti NoWin32Manifest. |
| AssemblyOriginatorKeyFile | .NET | Určuje soubor, který se používá k podepsání sestavení (*. snk* nebo *. pfx*) a který je předán [úloze ResolveKeySource –](../msbuild/resolvekeysource-task.md) , aby vygeneroval skutečný klíč, který se používá k podepsání sestavení. |
| AssemblySearchPaths | .NET | Seznam umístění, která se mají hledat během překladu referenčního sestavení v době sestavení Pořadí, ve kterém se cesty zobrazují v tomto seznamu, je smysluplné, protože cesty uvedené dříve mají přednost před pozdějšími položkami. |
| Doplňk | .NET | Název konečného výstupního sestavení po sestavení projektu. |
| BaseAddress | .NET | Určuje základní adresu hlavního výstupního sestavení. Tato vlastnost je ekvivalentní `/baseaddress` přepínači kompilátoru. |
| BaseIntermediateOutputPath | Vše | Složka na nejvyšší úrovni, kde jsou vytvořeny všechny přechodné výstupní složky specifické pro konfiguraci. Výchozí hodnota je `obj\`. Následující kód je příklad:`<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Vše | Určuje základní cestu pro výstupní soubor. Pokud je nastaveno, nástroj MSBuild bude používat `OutputPath = $(BaseOutputPath)\$(Configuration)\` . Příklad syntaxe:`<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Vše | Logická hodnota, která označuje, zda jsou odkazy na projekt vytvářeny nebo čištěny paralelně při použití nástroje MSBuild pro více procesů. Výchozí hodnota je `true` , což znamená, že projekty budou sestaveny paralelně, pokud má systém více jader nebo procesorů. |
| BuildProjectReferences | Vše | Logická hodnota, která určuje, zda jsou odkazy na projekt sestaveny nástrojem MSBuild. Automaticky nastaveno na `false` , pokud vytváříte projekt v integrovaném vývojovém prostředí sady Visual Studio (IDE), `true` Pokud je v opačném případě. `-p:BuildProjectReferences=false`dá se zadat na příkazovém řádku, abyste se vyhnuli kontrole, jestli jsou odkazované projekty aktuální. |
| CleanFile | Vše | Název souboru, který se použije jako "čistá mezipaměť". Čistá mezipaměť je seznam generovaných souborů, které mají být odstraněny během operace čištění. Soubor je umístěn do mezilehlé výstupní cesty procesem sestavení.<br /><br /> Tato vlastnost určuje pouze názvy souborů, které nemají informace o cestě. |
| Stránky | .NET | Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci. Tato vlastnost je ekvivalentní `/codepage` přepínači kompilátoru. |
| CompilerResponseFile | .NET | Volitelný soubor odpovědí, který lze předat úlohám kompilátoru. |
| Konfigurace | Vše | Konfigurace, kterou vytváříte, obecně `Debug` nebo `Release` , ale konfigurovatelné na úrovni řešení a projektu. |
| CscToolPath | C# | Cesta *csc.exe*, kompilátor jazyka C#. |
| CustomBeforeMicrosoftCommonTargets | Vše | Název souboru projektu nebo souboru cílů, který má být importován automaticky před importem běžných cílů. |
| DebugSymbols | Vše | Logická hodnota, která určuje, zda jsou symboly generovány sestavením.<br /><br /> Nastavení **-p:DebugSymbols = false** na příkazovém řádku zakáže generování souborů symbolů databáze programu (*PDB*). |
| DebugType | Vše | Definuje úroveň ladicích informací, které chcete vygenerovat. Platné hodnoty jsou "Full", "pdbonly", "Portable", "Embedded" a "none". |
| DefineConstants | .NET | Definuje podmíněné konstanty kompilátoru. Páry symbol/hodnota jsou odděleny středníky a jsou určeny pomocí následující syntaxe:<br /><br /> *symbol1 = hodnota1; symbol2 = hodnota2*<br /><br /> Vlastnost je ekvivalentní `/define` přepínači kompilátoru. |
| DefineDebug | Vše |  Logická hodnota, která určuje, zda má být definována konstanta ladění. |
| DefineTrace | Vše | Logická hodnota, která určuje, zda má být definována konstanta TRACE. |
| DelaySign | .NET | Logická hodnota, která označuje, zda chcete sestavení zpozdit podpisem, nikoli úplným podepsáním. |
| Deterministická | .NET | Logická hodnota, která určuje, zda má kompilátor vytvořit identická sestavení pro stejné vstupy. Tento parametr odpovídá `/deterministic` přepínači kompilátoru. |
| DisableFastUpToDateCheck | Vše | Logická hodnota, která se vztahuje pouze na Visual Studio. Správce sestavení sady Visual Studio používá proces nazvaný FastUpToDateCheck k určení, zda projekt musí být znovu sestaven, aby byl aktuální. Tento proces je rychlejší než použití nástroje MSBuild k tomu, aby ji bylo možné určit. Nastavení vlastnosti DisableFastUpToDateCheck na `true` umožňuje obejít správce sestavení sady Visual Studio a vynutit použití nástroje MSBuild k určení, zda je projekt aktuální. |
| DocumentationFile | .NET | Název souboru, který je generován jako soubor dokumentace XML. Tento název obsahuje pouze název souboru a neobsahuje informace o cestě. |
| ErrorReport | .NET | Určuje, jak má úloha kompilátoru nahlásit interní chyby kompilátoru. Platné hodnoty jsou "prompt", "Odeslat" nebo "none". Tato vlastnost je ekvivalentní `/errorreport` přepínači kompilátoru. |
| ExcludeDeploymentUrl | .NET | [Úloha GenerateDeploymentManifest –](../msbuild/generatedeploymentmanifest-task.md) Přidá značku deploymentProvider do manifestu nasazení, pokud soubor projektu obsahuje některý z následujících prvků:<br /><br /> - UpdateUrl<br />– InstallUrl<br />- PublishUrl<br /><br /> Pomocí ExcludeDeploymentUrl však můžete zabránit přidání značky deploymentProvider do manifestu nasazení, i když je zadána kterákoli z výše uvedených adres URL. Chcete-li to provést, přidejte do souboru projektu následující vlastnost:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Poznámka:**  ExcludeDeploymentUrl se nezveřejňuje v integrovaném vývojovém prostředí sady Visual Studio a dá se nastavit jenom ruční úpravou souboru projektu. Nastavení této vlastnosti neovlivní publikování v rámci sady Visual Studio; To znamená, že značka deploymentProvider bude stále přidána na adresu URL určenou parametrem PublishUrl. |
| Zarovnání. | .NET | Určuje, kam se v bajtech mají zarovnat oddíly výstupního souboru. Platné hodnoty jsou 512, 1024, 2048, 4096, 8192. Tato vlastnost je ekvivalentní `/filealignment` přepínači kompilátoru. |
| FrameworkPathOverride | Visual Basic | Určuje umístění *mscorlib.dll* a *microsoft.visualbasic.dll*. Tento parametr je ekvivalentní `/sdkpath` přepínači *vbc.exe* kompilátoru. |
| GenerateDocumentation | .NET | Logický parametr, který označuje, zda je dokumentace generována sestavením. Pokud `true` , sestavení generuje informace o dokumentaci a umístí je do souboru *. XML* spolu s názvem spustitelného souboru nebo knihovny, kterou vytvořil úkol sestavení. |
| GenerateFullPaths | C# | Vygenerujte úplné cesty pro názvy souborů ve výstupu pomocí možnosti kompilátoru [-fullpaths –](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) . |
| GenerateSerializationAssemblies | .NET | Určuje, zda by měla být sestavení serializace XML generována *SGen.exe*, která může být nastavena na hodnotu on, auto nebo off. Tato vlastnost se používá pouze pro sestavení, která cílí pouze na .NET Framework. Chcete-li generovat sestavení serializace XML pro .NET Standard nebo sestavení .NET Core, odkazujte na balíček NuGet *Microsoft.Xmlserializátor. Generator* . |
| IntermediateOutputPath | Vše | Úplná zprostředkující výstupní cesta odvozená od `BaseIntermediateOutputPath` , pokud není zadána žádná cesta. Například *\obj\debug \\ *. |
| ContainerName | Vše | Název kontejneru klíčů se silným názvem. |
| KeyOriginatorFile | Vše | Název souboru klíče se silným názvem. |
| Moduleassemblyname – | .NET | Název sestavení, do kterého má být kompilovaný modul začleněn. Vlastnost je ekvivalentní `/moduleassemblyname` přepínači kompilátoru. |
| MSBuildProjectExtensionsPath | Vše | Určuje cestu, kde se nachází rozšíření projektu. Ve výchozím nastavení má tato hodnota stejnou hodnotu jako `BaseIntermediateOutputPath` . |
| NoLogo | Vše | Logická hodnota, která označuje, zda má být vypnuto logo kompilátoru. Tato vlastnost je ekvivalentní `/nologo` přepínači kompilátoru. |
| NoStdLib | .NET | Logická hodnota, která označuje, zda se má vyhýbat odkazování na standardní knihovnu (*mscorlib.dll*). Výchozí hodnota je `false`. |
| NoVBRuntimeReference | Visual Basic | Logická hodnota, která označuje, zda by měl být modul runtime Visual Basic (*Microsoft.VisualBasic.dll*) zahrnut jako odkaz v projektu. |
| NoWarn | .NET | Potlačí zadaná upozornění. Je třeba zadat pouze číselnou část identifikátoru upozornění. Několik upozornění je odděleno středníky. Tento parametr odpovídá `/nowarn` přepínači kompilátoru. |
| NoWin32Manifest | .NET | Logická hodnota, která označuje, zda informace o manifestu nástroje řízení uživatelských účtů (UAC) budou vloženy do spustitelného souboru aplikace. Platí pouze pro projekty aplikace Visual Studio cílené na systém Windows Vista. V projektech nasazených pomocí technologie ClickOnce a modelu COM bez registrace je tento prvek ignorován. `False`(výchozí hodnota) určuje, že informace o manifestu nástroje řízení uživatelských účtů (UAC) budou vloženy do spustitelného souboru aplikace. `True`Určuje, že informace o manifestu nástroje řízení uživatelských účtů nebudou vloženy.<br /><br /> Tato vlastnost se vztahuje pouze na projekty sady Visual Studio cílené na systém Windows Vista. V projektech nasazených pomocí technologie ClickOnce a modelu COM bez registrace je tato vlastnost ignorována.<br /><br /> NoWin32Manifest byste měli přidat pouze v případě, že nechcete, aby aplikace Visual Studio vložila do spustitelného souboru aplikace žádné informace o manifestu. Tento proces se nazývá *virtualizace*. Chcete-li použít virtualizaci, nastavte `<ApplicationManifest>` ve spojení s `<NoWin32Manifest>` následujícím způsobem:<br /><br /> – Pro Visual Basic projekty odeberte `<ApplicationManifest>` uzel. (V Visual Basic projekty `<NoWin32Manifest>` se ignoruje, když `<ApplicationManifest>` uzel existuje.)<br />– Pro projekty v jazyce C# nastavte `<ApplicationManifest>` na `False` a `<NoWin32Manifest>` na `True` . (V projektech C#, `<ApplicationManifest>` Overrides `<NoWin32Manifest>` .)<br /> Tato vlastnost je ekvivalentní `/nowin32manifest` přepínači kompilátoru *vbc.exe*. |
| Optimalizace | .NET | Logická hodnota, která Pokud je nastavena na `true` , umožňuje optimalizace kompilátoru. Tato vlastnost je ekvivalentní `/optimize` přepínači kompilátoru. |
| OptionCompare – | VisualBasic | Určuje, jak se provádí porovnávání řetězců. Platné hodnoty jsou "Binary" nebo "text". Tato vlastnost je ekvivalentní `/optioncompare` přepínači kompilátoru *vbc.exe*. |
| OptionExplicit – | Visual Basic | Logická hodnota, která Pokud je nastavena na `true` , vyžaduje explicitní deklaraci proměnných ve zdrojovém kódu. Tato vlastnost je ekvivalentní `/optionexplicit` přepínači kompilátoru. |
| Optioninfer – | Visual Basic | Logická hodnota, která Pokud je nastavena na `true` , umožňuje odvozování typů proměnných. Tato vlastnost je ekvivalentní `/optioninfer` přepínači kompilátoru. |
| OptionStrict – | Visual Basic | Logická hodnota, která Pokud je nastavena na `true` , způsobí, že úloha sestavení vynutí striktní sémantiku typu pro omezení implicitních převodů typu. Tato vlastnost je ekvivalentní `/optionstrict` přepínači *vbc.exe* kompilátoru. |
| OutDir | Vše | Označuje konečné výstupní umístění projektu nebo řešení. Při sestavování řešení lze OutDir použít ke shromáždění více výstupů projektu na jednom místě. Kromě toho je OutDir zahrnut v AssemblySearchPaths, který se používá pro překládání odkazů. Například *bin\Debug*. |
| OutputPath | Vše | Určuje cestu k výstupnímu adresáři vzhledem k adresáři projektu, například *bin\Debug*. |
| OutputType | Vše |  Určuje formát výstupního souboru. Tento parametr může mít jednu z následujících hodnot:<br /><br /> Knihovna. Vytvoří knihovnu kódu. (Výchozí hodnota.)<br />Programu. Vytvoří konzolovou aplikaci.<br />Čipu. Vytvoří modul.<br />Winexe. Vytvoří program založený na systému Windows.<br /><br /> V jazyce C# a Visual Basic je tato vlastnost ekvivalentní `/target` přepínači. |
| OverwriteReadOnlyFiles | Vše | Logická hodnota, která označuje, zda chcete povolit sestavení pro přepsání souborů jen pro čtení nebo spuštění chyby. |
| PathMap | .NET | Určuje, jak namapovat fyzické cesty na výstup názvů zdrojových cest kompilátorem. Tato vlastnost je ekvivalentní `/pathmap` přepínači kompilátoru. |
| PdbFile | .NET | Název souboru *. pdb* , který vysíláte. Tato vlastnost je ekvivalentní `/pdb` přepínači *csc.exe* kompilátoru. |
| Platforma | Vše | Operační systém, pro který sestavíte. Příklady pro .NET Framework buildy jsou "any CPU", "x86" a "x64". |
| ProcessorArchitecture | .NET | Architektura procesoru, která se používá, když jsou přeloženy odkazy na sestavení. Platné hodnoty jsou "MSIL", "x86", "amd64" nebo "ia64". |
| ProduceOnlyReferenceAssembly | .NET | Logická hodnota, která instruuje kompilátor, aby vygenerovala pouze referenční sestavení namísto zkompilovaného kódu. Nelze použít ve spojení s `ProduceReferenceAssembly` .  Tato vlastnost odpovídá `/refonly` přepínači *vbc.exe* a *csc.exe* kompilátorů. |
| ProduceReferenceAssembly | .NET | Logická hodnota, která Pokud je nastavena na `true` povolenou výrobu [referenčních sestavení](/dotnet/standard/assembly/reference-assemblies) pro aktuální sestavení. `Deterministic`by měla být `true` při použití této funkce. Tato vlastnost odpovídá `/refout` přepínači *vbc.exe* a *csc.exe* kompilátorů. |
| RemoveIntegerChecks | Visual Basic | Logická hodnota, která označuje, zda se mají zakázat kontroly chyb přetečení celých čísel. Výchozí hodnota je `false`. Tato vlastnost je ekvivalentní `/removeintchecks` přepínači *vbc.exe* kompilátoru. |
| RootNamespace | Vše | Kořenový obor názvů, který se má použít při pojmenování vloženého prostředku. Tento obor názvů je součástí názvu vloženého manifestu prostředku. |
| Satellite_AlgorithmId | .NET | ID algoritmu hash *AL.exe* , který se má použít při vytváření satelitních sestavení. |
| Satellite_BaseAddress | .NET | Základní adresa, která se použije v případě satelitních sestavení specifických pro jazykovou verzi, se vytváří pomocí `CreateSatelliteAssemblies` cíle. |
| Satellite_CompanyName | .NET | Název společnosti, který se má předat *AL.exe* během generování satelitního sestavení. |
| Satellite_Configuration | .NET | Název konfigurace, který se má předat *AL.exe* během generování satelitního sestavení. |
| Satellite_Description | .NET | Text popisu, který se má předat *AL.exe* během generování satelitního sestavení. |
| Satellite_EvidenceFile | .NET | Vloží zadaný soubor do satelitního sestavení, které má název prostředku "Security. evidence". |
| Satellite_FileVersion | .NET | Určuje řetězec pro pole verze souboru v satelitním sestavení. |
| Satellite_Flags | .NET | Určuje hodnotu pro pole flags v satelitním sestavení. |
| Satellite_GenerateFullPaths | .NET | Způsobí, že úloha sestavení použije absolutní cesty pro všechny soubory hlášené v chybové zprávě. |
| Satellite_LinkResource | .NET | Propojí zadané soubory prostředků se satelitním sestavením. |
| Satellite_MainEntryPoint | .NET | Určuje plně kvalifikovaný název (tj. Class. Method) metody pro použití jako vstupní bod při převodu modulu na spustitelný soubor během generování satelitního sestavení. |
| Satellite_ProductName | .NET | Určuje řetězec pro pole produktu v satelitním sestavení. |
| Satellite_ProductVersion | .NET | Určuje řetězec pro pole ProductVersion v satelitním sestavení. |
| Satellite_TargetType | .NET | Určuje formát výstupního souboru satelitního sestavení jako "Library", "exe" nebo "Win". Výchozí hodnota je "Library". |
| Satellite_Title | .NET | Určuje řetězec pro pole title v satelitním sestavení. |
| Satellite_Trademark | .NET | Určuje řetězec pro pole ochranné známky v satelitním sestavení. |
| Satellite_Version | .NET | Určuje informace o verzi satelitního sestavení. |
| Satellite_Win32Icon | .NET | Vloží soubor ikony *. ico* do satelitního sestavení. |
| Satellite_Win32Resource | .NET | Vloží prostředek systému Win32 (soubor *. res* ) do satelitního sestavení. |
| SGenToolPath | .NET | Volitelná cesta nástroje, která označuje, kde získat *SGen.exe* , když je aktuální verze *SGen.exe* přepsána. |
| SGenUseProxyTypes | .NET | Logická hodnota, která určuje, zda mají být generovány typy proxy pomocí *SGen.exe*. To platí jenom v případě, že je *GenerateSerializationAssemblies* nastavené na zapnuto.<br /><br /> Cíl SGen používá tuto vlastnost k nastavení příznaku UseProxyTypes. Tato vlastnost je nastavena na hodnotu true a neexistuje žádné uživatelské rozhraní, které by bylo možné změnit. Chcete-li generovat sestavení serializace pro typy non-WebService, přidejte tuto vlastnost do souboru projektu a nastavte ji na false před importem *Microsoft. Common. targets* nebo *C#/VB.targets*. |
| SkipInvalidConfigurations | Vše | Když `true` , vygeneruje upozornění na neplatnou platformu a kombinace konfigurací, ale sestavení neselže, pokud není `false` definováno (výchozí), vygeneruje chybu. |
| StartupObject | .NET | Určuje třídu nebo modul, který obsahuje metodu Main nebo Sub Main Procedure. Tato vlastnost je ekvivalentní `/main` přepínači kompilátoru. |
| SubsystemVersion | .NET | Určuje minimální verzi subsystému, kterou může vygenerovaný spustitelný soubor použít. Tato vlastnost je ekvivalentní `/subsystemversion` přepínači kompilátoru. Informace o výchozí hodnotě této vlastnosti naleznete v tématu [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) nebo [/subsystemversion (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Verze prostředí .NET Compact Framework potřebná ke spuštění aplikace, kterou vytváříte. Zadáním této možnosti můžete odkazovat na konkrétní sestavení rozhraní, která pravděpodobně nebudete moci odkazovat jinak. |
| TargetFrameworkVersion | .NET | Verze .NET Framework potřebná ke spuštění aplikace, kterou vytváříte. Zadáním této možnosti můžete odkazovat na konkrétní sestavení rozhraní, která pravděpodobně nebudete moci odkazovat jinak. |
| TreatWarningsAsErrors | .NET | Logický parametr, který v případě `true` , že způsobí, že všechna upozornění budou považována za chyby. Tento parametr je ekvivalentní `/nowarn` přepínači kompilátoru. |
| UseHostCompilerIfAvailable | .NET | Logický parametr, který v případě `true` způsobí, že úloha sestavení použije vnitroprocesové objekt kompilátoru, pokud je k dispozici. Tento parametr je používán pouze v aplikaci Visual Studio. |
| Utf8output – | .NET | Logický parametr, který v případě `true` , protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr je ekvivalentní `/utf8Output` přepínači kompilátoru. |
| VbcToolPath | Visual Basic | Volitelná cesta, která označuje jiné umístění pro *vbc.exe* , pokud je aktuální verze *vbc.exe* přepsána. |
| VbcVerbosity | Visual Basic | Určuje podrobnost výstupu kompilátoru Visual Basic. Platné hodnoty jsou "quiet", "normální" (výchozí hodnota) nebo "Verbose". |
| VisualStudioVersion | Vše | Určuje verzi sady Visual Studio, ve které se má tento projekt považovat za spuštěný. Pokud tato vlastnost není zadána, MSBuild ji nastaví na rozumnou výchozí hodnotu.<br /><br /> Tato vlastnost se používá v několika typech projektů k určení sady cílů, které se používají pro sestavení. Pokud `ToolsVersion` je nastaven na 4,0 nebo vyšší pro projekt, `VisualStudioVersion` slouží k určení, kterou dílčí sadu nástrojů použít. Další informace najdete v tématu [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Určuje seznam upozornění, která mají být považována za chyby. Tento parametr je ekvivalentní `/warnaserror` přepínači kompilátoru. |
| WarningsNotAsErrors | .NET | Určuje seznam upozornění, která nejsou považována za chyby. Tento parametr je ekvivalentní `/warnaserror` přepínači kompilátoru. |
| Win32Manifest | .NET | Název souboru manifestu, který má být vložen do konečného sestavení. Tento parametr je ekvivalentní `/win32Manifest` přepínači kompilátoru. |
| Win32Resource | .NET | Název souboru prostředku Win32, který se má vložit do konečného sestavení Tento parametr je ekvivalentní `/win32resource` přepínači kompilátoru. |

## <a name="see-also"></a>Viz také:

- [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
- [Společná metadata položky MSBuild](common-msbuild-item-metadata.md)
- [Rezervované a dobře známé vlastnosti nástroje MSBuild](msbuild-reserved-and-well-known-properties.md)
