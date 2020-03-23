---
title: Vbc Úkol | Dokumenty společnosti Microsoft
ms.date: 04/12/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a1710336ebc73be707e962733e37376b5689e10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631234"
---
# <a name="vbc-task"></a>Vbc – úloha

Zalomení *vbc.exe*, který vytváří spustitelné soubory (*.exe*), dynamické knihovny (*.dll*) nebo moduly kódu (*.netmodule*). Další informace o *vbc.exe*naleznete v [tématu Kompilátor příkazového řádku jazyka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `Vbc` úkolu.

| Parametr | Popis |
|------------------------------| - |
| `AdditionalLibPaths` | Volitelný `String[]` parametr.<br /><br /> Určuje další složky, ve kterých mají být vyhledány sestavení určené v atributu Reference. |
| `AddModules` | Volitelný `String[]` parametr.<br /><br /> Způsobí, že kompilátor zpřístupní všechny informace o typu ze zadaného souboru (souborů) projektu, který právě kompilujete. Tento parametr odpovídá přepínači [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) kompilátoru *vbc.exe.* |
| `BaseAddress` | Volitelný `String` parametr.<br /><br /> Určuje základní adresu dll. Tento parametr odpovídá přepínači [-baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) kompilátoru *vbc.exe.* |
| `CodePage` | Volitelný `Int32` parametr.<br /><br /> Určuje znakovou stránku, která má být v kompilaci používána pro všechny soubory zdrojového kódu. Tento parametr odpovídá přepínači [-codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) kompilátoru *vbc.exe.* |
| `DebugType` | Volitelný `String[]` parametr.<br /><br /> Způsobí, že kompilátor generovat informace o ladění. Tento parametr může mít následující hodnoty:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Výchozí hodnota `full`je , která umožňuje připojení ladicího programu ke spuštěnému programu. Hodnota umožňuje `pdbonly` ladění zdrojového kódu při spuštění programu v ladicím programu, ale zobrazí kód jazyka sestavení pouze v případě, že je spuštěný program připojen k ladicímu programu. Další informace naleznete v tématu [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Volitelný `String[]` parametr.<br /><br /> Definuje konstanty podmíněného kompilátoru. Dvojice symbolů a hodnot jsou odděleny středníky a jsou určeny následující syntaxí:<br /><br /> *symbol1* `=` *symbol1* `;` *symbol2* `=` *hodnota2*<br /><br /> Tento parametr odpovídá [přepínači -define](/dotnet/visual-basic/reference/command-line-compiler/define) kompilátoru *vbc.exe.* |
| `DelaySign` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úkol umístí veřejný klíč do sestavení. Pokud `false`úkol plně podepíše sestavení. Výchozí hodnota `false`je . Tento parametr nemá žádný vliv, pokud není použit s parametrem `KeyFile` nebo parametrem. `KeyContainer` Tento parametr odpovídá přepínači [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) kompilátoru *vbc.exe.* |
| `Deterministic` | Volitelný `Boolean` parametr.<br/><br/> If `true`, způsobí, že kompilátor výstup sestavení, jehož binární obsah je shodný napříč kompilacemi, pokud vstupy jsou identické.<br/><br/>Další informace naleznete [v tématu -deterministický](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Volitelný `String` parametr.<br /><br /> Potlačí zadaná upozornění. Stačí zadat číselnou část identifikátoru upozornění. Více upozornění jsou odděleny středníky. Tento parametr odpovídá přepínači [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) kompilátoru *vbc.exe.* |
| `DocumentationFile` | Volitelný `String` parametr.<br /><br /> Zpracuje komentáře k dokumentaci k zadanému souboru XML. Tento parametr přepíše `GenerateDocumentation` atribut. Další informace naleznete v tématu [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úloha generuje informace o ladění a umístí je do souboru *PDB.* Další informace naleznete v tématu [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Volitelný `String` parametr.<br /><br /> Určuje, jak má úloha vykazovat interní chyby kompilátoru. Tento parametr může mít následující hodnoty:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Pokud `prompt` je zadán a dojde k chybě interníkompilátoru, uživatel je vyzván s možností, zda chcete odeslat data o chybě společnosti Microsoft.<br /><br /> Pokud `send` je zadán a dojde k chybě interníkompilátoru, úloha odešle data o chybě společnosti Microsoft.<br /><br /> Výchozí hodnota `none`je , která hlásí chyby pouze v textovém výstupu.<br /><br /> Tento parametr odpovídá přepínači [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) kompilátoru *vbc.exe.* |
| `FileAlignment` | Volitelný `Int32` parametr.<br /><br /> Určuje, kde mají být v bajtech zarovnány části výstupního souboru. Tento parametr může mít následující hodnoty:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Tento parametr odpovídá přepínači [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) kompilátoru *vbc.exe.* |
| `GenerateDocumentation` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`aplikace vygeneruje informace o dokumentaci a umístí je do souboru XML s názvem spustitelného souboru nebo knihovny, kterou úloha vytváří. Další informace naleznete v tématu [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Importuje obory názvů z zadaných kolekcí položek. Tento parametr odpovídá přepínači [-imports](/dotnet/visual-basic/reference/command-line-compiler/imports) kompilátoru *vbc.exe.* |
| `KeyContainer` | Volitelný `String` parametr.<br /><br /> Určuje název kontejneru kryptografického klíče. Tento parametr odpovídá [přepínači -keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) kompilátoru *vbc.exe.* |
| `KeyFile` | Volitelný `String` parametr.<br /><br /> Určuje název souboru obsahující ho kryptografický klíč. Další informace naleznete v tématu [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Volitelný <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Určuje [jazykovou verzi](/dotnet/visual-basic/language-reference/configure-language-version), například "15.5". |
| `LinkResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vytvoří odkaz na prostředek rozhraní .NET Framework ve výstupním souboru. soubor prostředků není umístěn do výstupního souboru. Tento parametr odpovídá přepínači [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) kompilátoru *vbc.exe.* |
| `MainEntryPoint` | Volitelný `String` parametr.<br /><br /> Určuje třídu nebo modul, `Sub Main` který obsahuje postup. Tento parametr odpovídá [přepínači -main](/dotnet/visual-basic/reference/command-line-compiler/main) kompilátoru *vbc.exe.* |
| `ModuleAssemblyName` | Volitelný `String` parametr.<br /><br /> Určuje sestavení, jehož je tento modul součástí. |
| `NoConfig` | Volitelný `Boolean` parametr.<br /><br /> Určuje, že kompilátor by neměl používat soubor *vbc.rsp.* Tento parametr odpovídá parametru [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) kompilátoru *vbc.exe.* |
| `NoLogo` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`potlačí zobrazení informací o banneru kompilátoru. Tento parametr odpovídá přepínači [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) kompilátoru *vbc.exe.* |
| `NoStandardLib` | Volitelný `Boolean` parametr.<br /><br /> Způsobí, že kompilátor nebude odkazovat na standardní knihovny. Tento parametr odpovídá přepínači [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) kompilátoru *vbc.exe.* |
| `NoVBRuntimeReference` | Volitelný `Boolean` parametr.<br /><br /> Pouze interní použití. Pokud true, zabrání automatický odkaz na *Microsoft.VisualBasic.dll*. |
| `NoWarnings` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úloha potlačí všechna upozornění. Další informace naleznete v tématu [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, umožňuje optimalizace kompilátoru. Tento parametr odpovídá přepínači [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) kompilátoru *vbc.exe.* |
| `OptionCompare` | Volitelný `String` parametr.<br /><br /> Určuje způsob porovnání řetězců. Tento parametr může mít následující hodnoty:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Hodnota `binary` určuje, že úloha používá binární porovnání řetězců. Hodnota `text` určuje, že úloha používá porovnání textových řetězců. Výchozí hodnota tohoto parametru je `binary`. Tento parametr odpovídá přepínači [-optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) kompilátoru *vbc.exe.* |
| `OptionExplicit` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`je vyžadováno explicitní prohlášení proměnných. Tento parametr odpovídá přepínači [-optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) kompilátoru *vbc.exe.* |
| `OptionInfer` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, umožňuje odvození typu proměnných. |
| `OptionStrict` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úkol vynucuje striktní typ sémantiku omezit implicitní typ převody. Tento parametr odpovídá přepínači [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilátoru *vbc.exe.* |
| `OptionStrictType` | Volitelný `String` parametr.<br /><br /> Určuje, která sémantika typu strict generuje upozornění. V současné době je podporovánpouze "vlastní". Tento parametr odpovídá přepínači [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilátoru *vbc.exe.* |
| `OutputAssembly` | Volitelný `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Tento parametr odpovídá přepínači [-out](/dotnet/visual-basic/reference/command-line-compiler/out) kompilátoru *vbc.exe.* |
| `Platform` | Volitelný `String` parametr.<br /><br /> Určuje platformu procesoru, na kterou má výstupní soubor cílit. Tento parametr může mít `x86` `x64`hodnotu , , `Itanium`nebo `anycpu`. Výchozí je `anycpu`. Tento parametr odpovídá [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform) přepínači -platformkompilátoru *vbc.exe.* |
| `References` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Způsobí, že úkol importuje informace veřejného typu ze zadaných položek do aktuálního projektu. Tento parametr odpovídá přepínači [-reference](/dotnet/visual-basic/reference/command-line-compiler/reference) kompilátoru *vbc.exe.* |
| `RemoveIntegerChecks` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`zakáže kontroly chyb přetečení celého čísla. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači [-removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) kompilátoru *vbc.exe.* |
| `Resources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vloží do výstupního souboru prostředek rozhraní .NET Framework. Tento parametr odpovídá přepínači [-resource](/dotnet/visual-basic/reference/command-line-compiler/resource) kompilátoru *vbc.exe.* |
| `ResponseFiles` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje soubor odpovědí, který obsahuje příkazy pro tuto úlohu. Tento parametr odpovídá volbě [@ (Specify Response File)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) kompilátoru *vbc.exe.* |
| `RootNamespace` | Volitelný `String` parametr.<br /><br /> Určuje kořenový obor názvů pro všechny deklarace typu. Tento parametr odpovídá přepínači [-rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) kompilátoru *vbc.exe.* |
| `SdkPath` | Volitelný `String` parametr.<br /><br /> Určuje umístění souborů *mscorlib.dll* a *microsoft.visualbasic.dll*. Tento parametr odpovídá přepínači [-sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) kompilátoru *vbc.exe.* |
| `Sources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje jeden nebo více zdrojových souborů jazyka Visual Basic. |
| `TargetCompactFramework` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úkol cílí na rozhraní .NET Compact Framework. Tento přepínač odpovídá přepínači [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) kompilátoru *vbc.exe.* |
| `TargetType` | Volitelný `String` parametr.<br /><br /> Určuje formát souboru výstupního souboru. Tento parametr může mít `library`hodnotu , která `exe`vytvoří knihovnu kódu `module`, která vytvoří `winexe`konzolovou aplikaci , která vytvoří modul nebo , která vytvoří program systému Windows. Výchozí je `library`. Tento parametr odpovídá přepínači [-target](/dotnet/visual-basic/reference/command-line-compiler/target) kompilátoru *vbc.exe.* |
| `Timeout` | Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je spustitelný soubor úlohy ukončen. Výchozí hodnota `Int.MaxValue`je , označující, že neexistuje žádné časové období. |
| `ToolPath` | Volitelný `String` parametr.<br /><br /> Určuje umístění, ze kterého bude úloha načítat základní spustitelný soubor (*vbc.exe*). Pokud tento parametr není zadán, úloha používá instalační cestu sady SDK odpovídající verzi rozhraní, ve které je spuštěno službu MSBuild. |
| `TreatWarningsAsErrors` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`jsou všechna upozornění považována za chyby. Další informace naleznete v tématu [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Volitelný `Boolean` parametr.<br /><br /> Dá pokyn úkolu použít objekt kompilátoru v procesu, pokud je k dispozici. Používá pouze visual studio. |
| `Utf8Output` | Volitelný `Boolean` parametr.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr odpovídá přepínači [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) kompilátoru *vbc.exe.* |
| `Verbosity` | Volitelný `String` parametr.<br /><br /> Určuje podrobnost výstupu kompilátoru. Podrobnostmůže být `Quiet`, `Normal` (výchozí) nebo `Verbose`. |
| `WarningsAsErrors` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která mají být považována za chyby. Další informace naleznete v tématu [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Tento parametr přepíše `TreatWarningsAsErrors` parametr. |
| `WarningsNotAsErrors` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která nejsou považována za chyby. Další informace naleznete v tématu [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Tento parametr je užitečný `TreatWarningsAsErrors` pouze v `true`případě, že je parametr nastaven na . |
| `Win32Icon` | Volitelný `String` parametr.<br /><br /> Vloží soubor *.ico* do sestavy, který poskytuje výstupnímu souboru požadovaný vzhled v **Průzkumníkovi souborů**. Tento parametr odpovídá přepínači [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) kompilátoru *vbc.exe.* |
| `Win32Resources` | Volitelný `String` parametr.<br /><br /> Vloží do výstupního souboru soubor prostředku Win32 (*res).* Tento parametr odpovídá přepínači [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) kompilátoru *vbc.exe.* |

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.ToolTaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.ToolTask> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [ToolTaskExtension base class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad zkompiluje projekt jazyka.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>Viz také

- [Kompilátor příkazového řádku jazyka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
