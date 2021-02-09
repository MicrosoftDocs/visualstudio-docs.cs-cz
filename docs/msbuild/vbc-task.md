---
title: Úloha Vbc | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu Vbc k zabalení vbc.exe, který vytváří spustitelné soubory, knihovny DLL nebo moduly kódu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6596dd0893d0ab302a738cb12856fc6758df039
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908859"
---
# <a name="vbc-task"></a>Vbc – úloha

Zalomí *vbc.exe*, které vytváří spustitelné soubory (*. exe*), dynamické knihovny (*. dll*) nebo kódové moduly (*. netmodule*). Další informace o *vbc.exe* najdete v tématu [Visual Basic kompilátoru příkazového řádku](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `Vbc` úkolu.

| Parametr | Popis |
|------------------------------| - |
| `AdditionalLibPaths` | Volitelný `String[]` parametr.<br /><br /> Určuje další složky, ve kterých budou hledána sestavení zadaná v atributu References. |
| `AddModules` | Volitelný `String[]` parametr.<br /><br /> Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete. Tento parametr odpovídá přepínači [-addmodule –](/dotnet/visual-basic/reference/command-line-compiler/addmodule) kompilátoru *vbc.exe* . |
| `BaseAddress` | Volitelný `String` parametr.<br /><br /> Určuje základní adresu knihovny DLL. Tento parametr odpovídá přepínači [-baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) *vbc.exe* kompilátoru. |
| `CodePage` | Volitelný `Int32` parametr.<br /><br /> Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci. Tento parametr odpovídá přepínači [-codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) kompilátoru *vbc.exe* . |
| `DebugType` | Volitelný `String[]` parametr.<br /><br /> Způsobí, že kompilátor generuje ladicí informace. Tento parametr může mít následující hodnoty:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Výchozí hodnota je `full` , která umožňuje připojit k běžícímu programu ladicí program. Hodnota `pdbonly` umožňuje ladění zdrojového kódu při spuštění programu v ladicím programu, ale zobrazuje kód jazyka sestavení pouze v případě, že je spuštěný program připojen k ladicímu programu. Další informace naleznete v tématu [-Debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Volitelný `String[]` parametr.<br /><br /> Definuje podmíněné konstanty kompilátoru. Páry symbol/hodnota jsou odděleny středníky a jsou zadány s následující syntaxí:<br /><br /> *symbol1* `=` *hodnota1* `;` *symbol2* `=` *hodnota2*<br /><br /> Tento parametr odpovídá přepínači [-define](/dotnet/visual-basic/reference/command-line-compiler/define) *vbc.exe* kompilátoru. |
| `DelaySign` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` se úloha umístí do sestavení veřejný klíč. `false`V případě, úloha plně podepíše sestavení. Výchozí hodnota je `false` . Tento parametr nemá žádný vliv, pokud se nepoužívá s `KeyFile` parametrem nebo `KeyContainer` parametrem. Tento parametr odpovídá přepínači [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) kompilátoru *vbc.exe* . |
| `Deterministic` | Volitelný `Boolean` parametr.<br/><br/> Pokud je `true` , vyvolá kompilátor výstup sestavení, jehož binární obsah je identický v rámci kompilací, pokud jsou vstupy identické.<br/><br/>Další informace naleznete v tématu [-deterministické](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Volitelný `String` parametr.<br /><br /> Potlačí zadaná upozornění. Stačí zadat jenom číselnou část identifikátoru upozornění. Několik upozornění je odděleno středníky. Tento parametr odpovídá přepínači [-bez upozornění](/dotnet/visual-basic/reference/command-line-compiler/nowarn) kompilátoru *vbc.exe* . |
| `DocumentationFile` | Volitelný `String` parametr.<br /><br /> Zpracuje komentáře dokumentace do zadaného souboru XML. Tento parametr Přepisuje `GenerateDocumentation` atribut. Další informace najdete v [dokumentu-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` úloha vygeneruje informace o ladění a umístí je do souboru *. pdb* . Další informace naleznete v tématu [-Debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Volitelný `String` parametr.<br /><br /> Určuje, jak by měl úkol hlásit vnitřní chyby kompilátoru. Tento parametr může mít následující hodnoty:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Pokud `prompt` je zadána a dojde k vnitřní chybě kompilátoru, zobrazí se uživateli výzva s možností, zda chcete odeslat údaje o chybách společnosti Microsoft.<br /><br /> Pokud `send` je zadána a dojde k vnitřní chybě kompilátoru, úloha odešle údaje o chybě společnosti Microsoft.<br /><br /> Výchozí hodnota je `none` , což hlásí pouze chyby ve výstupu textu.<br /><br /> Tento parametr odpovídá přepínači [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) kompilátoru *vbc.exe* . |
| `FileAlignment` | Volitelný `Int32` parametr.<br /><br /> Určuje, kam se v bajtech mají zarovnat oddíly výstupního souboru. Tento parametr může mít následující hodnoty:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Tento parametr odpovídá přepínači [-align](/dotnet/visual-basic/reference/command-line-compiler/filealign) *vbc.exe* kompilátoru. |
| `GenerateDocumentation` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , vygeneruje informace o dokumentaci a umístí je do souboru XML s názvem spustitelného souboru nebo knihovny, kterou vytváří úkol. Další informace najdete v [dokumentu-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Importuje obory názvů z určených kolekcí položek. Tento parametr odpovídá přepínači [-Imports](/dotnet/visual-basic/reference/command-line-compiler/imports) kompilátoru *vbc.exe* . |
| `KeyContainer` | Volitelný `String` parametr.<br /><br /> Určuje název kontejneru kryptografických klíčů. Tento parametr odpovídá přepínači-s, který [obsahuje](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) *vbc.exe* kompilátoru. |
| `KeyFile` | Volitelný `String` parametr.<br /><br /> Určuje název souboru, který obsahuje kryptografický klíč. Další informace najdete v tématu [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Volitelný <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Určuje [jazykovou verzi](/dotnet/visual-basic/language-reference/configure-language-version), například "15,5". |
| `LinkResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru; zdrojový soubor není umístěný do výstupního souboru. Tento parametr odpovídá přepínači [-linkresource –](/dotnet/visual-basic/reference/command-line-compiler/linkresource) kompilátoru *vbc.exe* . |
| `MainEntryPoint` | Volitelný `String` parametr.<br /><br /> Určuje třídu nebo modul, který obsahuje `Sub Main` proceduru. Tento parametr odpovídá [hlavnímu](/dotnet/visual-basic/reference/command-line-compiler/main) přepínači *vbc.exe* kompilátoru. |
| `ModuleAssemblyName` | Volitelný `String` parametr.<br /><br /> Určuje sestavení, jehož součástí je tento modul. |
| `NoConfig` | Volitelný `Boolean` parametr.<br /><br /> Určuje, že by kompilátor neměl používat soubor *Vbc. rsp* . Tento parametr odpovídá parametru [--config](/dotnet/visual-basic/reference/command-line-compiler/noconfig) kompilátoru *vbc.exe* . |
| `NoLogo` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` se potlačí zobrazení informací o banneru kompilátoru. Tento parametr odpovídá přepínači [-bez loga](/dotnet/visual-basic/reference/command-line-compiler/nologo) *vbc.exe* kompilátoru. |
| `NoStandardLib` | Volitelný `Boolean` parametr.<br /><br /> Způsobí, že kompilátor neodkazuje na standardní knihovny. Tento parametr odpovídá přepínači [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) kompilátoru *vbc.exe* . |
| `NoVBRuntimeReference` | Volitelný `Boolean` parametr.<br /><br /> Pouze interní použití. Je-li nastavena hodnota true, zakáže automatické odkaz na *Microsoft.VisualBasic.dll*. |
| `NoWarnings` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je úloha potlačuje všechna upozornění. Další informace najdete v tématu [– Upozornění](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` povolíte optimalizace kompilátoru. Tento parametr odpovídá přepínači [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) *vbc.exe* kompilátoru. |
| `OptionCompare` | Volitelný `String` parametr.<br /><br /> Určuje, jak se provádí porovnávání řetězců. Tento parametr může mít následující hodnoty:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Hodnota `binary` Určuje, že úloha používá porovnávání binárních řetězců. Hodnota `text` Určuje, že úloha používá porovnávání textových řetězců. Výchozí hodnota tohoto parametru je `binary` . Tento parametr odpovídá přepínači [-OptionCompare –](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) kompilátoru *vbc.exe* . |
| `OptionExplicit` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je požadována explicitní deklarace proměnných. Tento parametr odpovídá přepínači [-OptionExplicit –](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) kompilátoru *vbc.exe* . |
| `OptionInfer` | Volitelný `Boolean` parametr.<br /><br /> `true`V případě, umožňuje odvozování typů proměnných. |
| `OptionStrict` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je úloha vynutila striktní sémantiku typu pro omezení implicitních převodů typu. Tento parametr odpovídá přepínači [-OptionStrict –](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilátoru *vbc.exe* . |
| `OptionStrictType` | Volitelný `String` parametr.<br /><br /> Určuje, která sémantika striktního typu vygeneruje upozornění. V současné době je podporována pouze možnost vlastní. Tento parametr odpovídá přepínači [-OptionStrict –](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilátoru *vbc.exe* . |
| `OutputAssembly` | Volitelný `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Tento parametr [odpovídá přepínači](/dotnet/visual-basic/reference/command-line-compiler/out) *vbc.exe* kompilátoru. |
| `Platform` | Volitelný `String` parametr.<br /><br /> Určuje platformu procesoru, na kterou má výstupní soubor cílit. Tento parametr může mít hodnotu `x86` , `x64` , `Itanium` nebo `anycpu` . Výchozí je `anycpu`. Tento parametr odpovídá přepínači [-Platform](/dotnet/visual-basic/reference/command-line-compiler/platform) kompilátoru *vbc.exe* . |
| `References` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Způsobí, že úloha importuje informace o veřejném typu ze zadaných položek do aktuálního projektu. Tento parametr odpovídá přepínači [-reference](/dotnet/visual-basic/reference/command-line-compiler/reference) kompilátoru *vbc.exe* . |
| `RemoveIntegerChecks` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , zakáže kontroly chyb přetečení celých čísel. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači [-removeintchecks –](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) kompilátoru *vbc.exe* . |
| `Resources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vloží prostředek .NET Framework do výstupního souboru. Tento parametr odpovídá přepínači [-Resource](/dotnet/visual-basic/reference/command-line-compiler/resource) kompilátoru *vbc.exe* . |
| `ResponseFiles` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje soubor odpovědí obsahující příkazy pro tento úkol. Tento parametr odpovídá možnosti [@ (určení souboru odezvy)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) kompilátoru *vbc.exe* . |
| `RootNamespace` | Volitelný `String` parametr.<br /><br /> Určuje kořenový obor názvů pro všechny deklarace typů. Tento parametr odpovídá přepínači [-RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) kompilátoru *vbc.exe* . |
| `SdkPath` | Volitelný `String` parametr.<br /><br /> Určuje umístění *mscorlib.dll* a *microsoft.visualbasic.dll*. Tento parametr odpovídá přepínači [-SdkPath –](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) kompilátoru *vbc.exe* . |
| `Sources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje jeden nebo více Visual Basic zdrojových souborů. |
| `TargetCompactFramework` | Volitelný `Boolean` parametr.<br /><br /> Pokud je `true` úloha cílena na prostředí .NET Compact Framework. Tento přepínač odpovídá přepínači [-netcf –](/dotnet/visual-basic/reference/command-line-compiler/netcf) kompilátoru *vbc.exe* . |
| `TargetType` | Volitelný `String` parametr.<br /><br /> Určuje formát výstupního souboru. Tento parametr může mít hodnotu `library` , která vytvoří knihovnu kódu, `exe` , která vytvoří konzolovou aplikaci, `module` , která vytvoří modul, nebo `winexe` , který vytvoří program systému Windows. Výchozí je `library`. Tento parametr odpovídá přepínači [-target](/dotnet/visual-basic/reference/command-line-compiler/target) *vbc.exe* kompilátoru. |
| `Timeout` | Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue` , což značí, že není k dispozici žádný časový interval. |
| `ToolPath` | Volitelný `String` parametr.<br /><br /> Určuje umístění, ze kterého bude úloha načítat základní spustitelný soubor (*vbc.exe*). Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK odpovídající verzi rozhraní .NET Framework, která spouští nástroj MSBuild. |
| `TreatWarningsAsErrors` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` jsou všechna upozornění považována za chyby. Další informace najdete v tématu [-warnaserror – (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Volitelný `Boolean` parametr.<br /><br /> Dá pokyn k tomu, aby úkol použil objekt vnitroprocesového kompilátoru, pokud je k dispozici. Používáno pouze v aplikaci Visual Studio. |
| `Utf8Output` | Volitelný `Boolean` parametr.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr odpovídá přepínači [-utf8output –](/dotnet/visual-basic/reference/command-line-compiler/utf8output) kompilátoru *vbc.exe* . |
| `Verbosity` | Volitelný `String` parametr.<br /><br /> Určuje podrobnost výstupu kompilátoru. Podrobnosti mohou být `Quiet` , `Normal` (výchozí), nebo `Verbose` . |
| `WarningsAsErrors` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která mají být považována za chyby. Další informace najdete v tématu [-warnaserror – (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Tento parametr Přepisuje `TreatWarningsAsErrors` parametr. |
| `WarningsNotAsErrors` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která nejsou považována za chyby. Další informace najdete v tématu [-warnaserror – (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Tento parametr je užitečný pouze v případě, že `TreatWarningsAsErrors` je parametr nastaven na hodnotu `true` . |
| `Win32Icon` | Volitelný `String` parametr.<br /><br /> Vloží soubor *. ico* do sestavení, které poskytne výstupnímu souboru požadovaný vzhled v **Průzkumníkovi souborů**. Tento parametr odpovídá přepínači [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) kompilátoru *vbc.exe* . |
| `Win32Resources` | Volitelný `String` parametr.<br /><br /> Vloží soubor prostředků Win32 (*. res*) do výstupního souboru. Tento parametr odpovídá přepínači [-Win32Resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) kompilátoru *vbc.exe* . |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Příklad

 Následující příklad zkompiluje Visual Basic projekt.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
