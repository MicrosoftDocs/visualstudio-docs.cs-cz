---
title: Úkol ČSC | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c88e5aaef9262d320cdf61564078246dee46b10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634263"
---
# <a name="csc-task"></a>Csc – úloha

Zabalí *csc.exe*a vytvoří spustitelné soubory (*soubory EXE),* knihovny s dynamickými spoji (*soubory DLL)* nebo moduly kódu ( soubory *.netmodule).* Další informace o *programu csc.exe*naleznete v tématu [C# možnosti kompilátoru](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `Csc` úkolu.

| Parametr | Popis |
|------------------------------| - |
| `AdditionalLibPaths` | Volitelný `String[]` parametr.<br /><br /> Určuje další adresáře pro vyhledávání odkazů. Další informace naleznete v tématu [-lib (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Volitelný `String` parametr.<br /><br /> Určuje jeden nebo více modulů, které mají být součástí sestavy. Další informace naleznete v tématu [-addmodule (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`zkompiluje kód, který používá klíčové slovo [nebezpečné.](/dotnet/csharp/language-reference/keywords/unsafe) Další informace naleznete [v tématu -unsafe (Možnosti kompilátoru Jazyka C).](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option) |
| `ApplicationConfiguration` | Volitelný `String` parametr.<br /><br /> Určuje konfigurační soubor aplikace obsahující nastavení vazby sestavení. |
| `BaseAddress` | Volitelný `String` parametr.<br /><br /> Určuje upřednostňovanou základní adresu, na kterou má být načíst dll. Výchozí základní adresa pro dll je nastavena za běhu mll .NET Framework common language. Další informace naleznete v tématu [-baseaddress (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Volitelný `Boolean` parametr.<br /><br /> Určuje, zda integer aritmetika, která přeteče hranice datového typu způsobí výjimku za běhu. Další informace naleznete v [tématu -checked (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Volitelný `Int32` parametr.<br /><br /> Určuje znakovou stránku, která má být v kompilaci používána pro všechny soubory zdrojového kódu. Další informace naleznete [v tématu -codepage (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Volitelný `String` parametr.<br /><br /> Určuje typ ladění. `DebugType`může `full` být `pdbonly`nebo . Výchozí hodnota `full`je , která umožňuje připojení ladicího programu ke spuštěnému programu. Zadání `pdbonly` umožňuje ladění zdrojového kódu při spuštění programu v ladicím programu, ale zobrazí assembler pouze v případě, že je spuštěný program připojen k ladicímu programu.<br /><br /> Tento parametr přepíše `EmitDebugInformation` parametr.<br /><br /> Další informace naleznete v tématu [-debug (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Volitelný `String` parametr.<br /><br /> Definuje symboly preprocesoru. Další informace naleznete v tématu [-define (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, určuje, že chcete umístit pouze veřejný klíč do sestavení. Pokud `false`, určuje, že chcete plně podepsané sestavení<br /><br /> Tento parametr nemá žádný vliv, `KeyFile` `KeyContainer` pokud není použit s parametrem nebo.<br /><br /> Další informace naleznete v tématu [-delaysign (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Volitelný `Boolean` parametr.<br/><br/> If `true`, způsobí, že kompilátor výstup sestavení, jehož binární obsah je shodný napříč kompilacemi, pokud vstupy jsou identické.<br/><br/>Další informace naleznete [v tématu -deterministic (C# Compiler možnosti)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která mají být zakázána. Další informace naleznete v tématu [-nowarn (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Volitelný `String` parametr.<br /><br /> Zpracuje komentáře k dokumentaci do souboru XML. Další informace naleznete v tématu [-doc (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úloha generuje ladicí informace a umístí je do souboru databáze programu (.pdb). Pokud `false`úloha nevydává žádné informace o ladění. Výchozí je `false`. Další informace naleznete v tématu [-debug (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Volitelný `String` parametr.<br /><br /> Poskytuje pohodlný způsob, jak nahlásit vnitřní chybu jazyka C# společnosti Microsoft. Tento parametr může mít `prompt` `send`hodnotu `none`, , nebo . Pokud je parametr `prompt`nastaven na , zobrazí se výzva, když dojde k chybě interního kompilátoru. Výzva umožňuje odeslat hlášení o chybě elektronicky společnosti Microsoft. Pokud je parametr `send`nastaven na , je automaticky odeslána zpráva o chybě. Pokud je parametr `none`nastaven na , chyba je hlášena pouze v textovém výstupu kompilátoru. Výchozí je `none`. Další informace naleznete v tématu [-errorreport (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Volitelný `Int32` parametr.<br /><br /> Určuje velikost oddílů ve výstupním souboru. Další informace naleznete v tématu [-filealign (Možnosti kompilátoru Jazyka C).](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option) |
| `GenerateFullPaths` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`určuje absolutní cestu k souboru ve výstupu kompilátoru. Pokud `false`určuje název souboru. Výchozí je `false`. Další informace naleznete [v tématu -fullpaths (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Volitelný `String` parametr.<br /><br /> Určuje název kontejneru kryptografického klíče. Další informace naleznete [v tématu -keycontainer (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Volitelný `String` parametr.<br /><br /> Určuje název souboru obsahující ho kryptografický klíč. Další informace naleznete v tématu [-keyfile (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Volitelný `String` parametr.<br /><br /> Určuje verzi jazyka, který se má použít. Další informace naleznete v tématu [-langversion (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vytvoří odkaz na prostředek rozhraní .NET Framework ve výstupním souboru. soubor prostředků není umístěn do výstupního souboru.<br /><br /> Položky předané do tohoto parametru `LogicalName` `Access`mohou mít volitelné položky metadat s názvem a . `LogicalName`odpovídá parametru `identifier` přepínače `/linkresource` a `Access` odpovídá parametru. `accessibility-modifier` Další informace naleznete v tématu [-linkresource (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Volitelný `String` parametr.<br /><br /> Určuje umístění `Main` metody. Další informace naleznete [v tématu -main (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Volitelný `String` parametr.<br /><br /> Určuje název sestavení, jehož součástí bude tento modul. |
| `NoConfig` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`aplikace , řekne kompilátoru, aby nekompiloval se souborem *csc.rsp.* Další informace naleznete v tématu [-noconfig (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`potlačí zobrazení informací o banneru kompilátoru. Další informace naleznete v tématu [-nologo (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`zabrání importu *souboru mscorlib.dll*, který definuje celý obor názvů Systém. Tento parametr použijte, pokud chcete definovat nebo vytvořit vlastní systémový obor názvů a objekty. Další informace naleznete v tématu [-nostdlib (Možnosti kompilátoru Jazyka C# ).](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option) |
| `NoWin32Manifest` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`nezahrnovat výchozí Win32 manifest. |
| `Optimize` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, umožňuje optimalizace. Pokud `false`zakáže optimalizace. Další informace naleznete v tématu [-optimize (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Volitelný `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Další informace naleznete v tématu [-out (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Volitelný `String` parametr.<br /><br /> Určuje název souboru sestavení výstupního odkazu. Další informace naleznete [v tématu -refout (Možnosti kompilátoru Jazyka C# ).](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option) |
| `PdbFile` | Volitelný `String` parametr.<br /><br /> Určuje název souboru informací o ladění. Výchozí název je název výstupního souboru s příponou *PDB.* |
| `Platform` | Volitelný `String` parametr.<br /><br /> Určuje platformu procesoru, na kterou má výstupní soubor cílit. Tento parametr může mít `x86` `x64`hodnotu `anycpu`, , nebo . Výchozí je `anycpu`. Další informace naleznete v tématu [-platform (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Způsobí, že úkol importuje informace veřejného typu ze zadaných položek do aktuálního projektu. Další informace naleznete [v tématu -reference (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> V souboru MSBuild můžete zadat alias odkazu jazyka `Aliases` C# přidáním metadat do původní položky "Reference". Chcete-li například nastavit alias "LS1" v následujícím příkazovém řádku Csc:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> byste použili:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vloží do výstupního souboru prostředek rozhraní .NET Framework.<br /><br /> Položky předané do tohoto parametru `LogicalName` `Access`mohou mít volitelné položky metadat s názvem a . `LogicalName`odpovídá parametru `identifier` přepínače `/resource` a `Access` odpovídá parametru. `accessibility-modifier` Další informace naleznete v tématu [-resource (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Volitelný `String` parametr.<br /><br /> Určuje soubor odpovědí, který obsahuje příkazy pro tuto úlohu. Další informace naleznete v tématu [@ (Specify response file).](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option) |
| `Sources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje jeden nebo více zdrojových souborů jazyka C#. |
| `TargetType` | Volitelný `String` parametr.<br /><br /> Určuje formát souboru výstupního souboru. Tento parametr může mít `library`hodnotu , která `exe`vytvoří knihovnu kódu `module`, která vytvoří `winexe`konzolovou aplikaci , která vytvoří modul nebo , která vytvoří program systému Windows. Výchozí hodnota je `library`. Další informace naleznete [v tématu -target (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, považuje všechna upozornění za chyby. Další informace naleznete v tématu [-warnaserror (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Volitelný `Boolean` parametr.<br /><br /> Dá pokyn úkolu použít objekt kompilátoru v procesu, pokud je k dispozici. Používá pouze visual studio. |
| `Utf8Output` | Volitelný `Boolean` parametr.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Další informace naleznete [v tématu -utf8output (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Volitelný `Int32` parametr.<br /><br /> Určuje úroveň upozornění, aby se kompilátor zobrazil. Další informace naleznete v tématu [-warn (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která mají být považována za chyby. Další informace naleznete v tématu [-warnaserror (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Tento parametr přepíše `TreatWarningsAsErrors` parametr. |
| `WarningsNotAsErrors` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která nejsou považována za chyby. Další informace naleznete v tématu [-warnaserror (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Tento parametr je užitečný `TreatWarningsAsErrors` pouze v `true`případě, že je parametr nastaven na . |
| `Win32Icon` | Volitelný `String` parametr.<br /><br /> Vloží soubor *.ico* do sestavy, který poskytuje výstupnímu souboru požadovaný vzhled v **Průzkumníkovi souborů**. Další informace naleznete v tématu [-win32icon (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Volitelný `String` parametr.<br /><br /> Určuje manifest win32, který má být zahrnut. |
| `Win32Resource` | Volitelný `String` parametr.<br /><br /> Vloží do výstupního souboru soubor prostředku Win32 (*res).* Další informace naleznete v tématu [-win32res (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí `Microsoft.Build.Tasks.ManagedCompiler` parametry z třídy, která dědí <xref:Microsoft.Build.Tasks.ToolTaskExtension> z <xref:Microsoft.Build.Utilities.ToolTask> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [ToolTaskExtension base class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `Csc` úlohu ke kompilaci spustitelného `Compile` souboru ze zdrojových souborů v kolekci položek.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
