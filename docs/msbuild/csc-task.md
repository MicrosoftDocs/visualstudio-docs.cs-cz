---
title: Úloha CSc | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9df54befff79b82703cb363fea92536285c68232
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70888026"
---
# <a name="csc-task"></a>Csc – úloha
Zabalí *CSc. exe*a vytvoří spustitelné soubory (soubory *. exe* ), dynamické knihovny (soubory *. dll* ) nebo kódové moduly (soubory *. netmodule* ). Další informace o souboru *CSc. exe*naleznete v tématu [ C# možnosti kompilátoru](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametry
Následující tabulka popisuje parametry `Csc` úkolu.

| Parametr | Popis |
|------------------------------| - |
| `AdditionalLibPaths` | Volitelný `String[]` parametr.<br /><br /> Určuje další adresáře, ve kterých budou hledány odkazy. Další informace naleznete v tématu [-lib (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Volitelný `String` parametr.<br /><br /> Určuje jeden nebo více modulů, které mají být součástí sestavení. Další informace naleznete v tématu [-addmodule – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`zkompiluje kód, který používá klíčové slovo [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) . Další informace naleznete v tématu [-unsafeC# (možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Volitelný `String` parametr.<br /><br /> Určuje konfigurační soubor aplikace obsahující nastavení vazby sestavení. |
| `BaseAddress` | Volitelný `String` parametr.<br /><br /> Určuje upřednostňovanou základní adresu, na které se má načíst knihovna DLL. Výchozí základní adresa pro knihovnu DLL je nastavena .NET Framework modul CLR (Common Language Runtime). Další informace naleznete v tématu [-BaseAddress (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Volitelný `Boolean` parametr.<br /><br /> Určuje, zda celočíselná aritmetická operace, která přetéká hranice datového typu, způsobuje výjimku v době běhu. Další informace naleznete v tématu [-checked (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Volitelný `Int32` parametr.<br /><br /> Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci. Další informace naleznete v části [-codepage (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Volitelný `String` parametr.<br /><br /> Určuje typ ladění. `DebugType`může být `full` nebo `pdbonly`. Výchozí hodnota je `full`, což umožňuje připojit ladicí program ke spuštěnému programu. Určení `pdbonly` umožňuje ladění zdrojového kódu při spuštění programu v ladicím programu, ale zobrazí pouze Assembler, pokud je spuštěný program připojen k ladicímu programu.<br /><br /> Tento parametr Přepisuje `EmitDebugInformation` parametr.<br /><br /> Další informace naleznete v tématu [-Debug (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Volitelný `String` parametr.<br /><br /> Definuje symboly preprocesoru. Další informace naleznete v tématu [-defineC# (možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, určuje, že chcete umístit pouze veřejný klíč do sestavení. Pokud `false`, určuje, že chcete sestavení plně podepsané<br /><br /> Tento parametr nemá žádný vliv, pokud se nepoužívá `KeyFile` buď `KeyContainer` s parametrem nebo.<br /><br /> Další informace naleznete v tématu [-delaysign (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Volitelný `Boolean` parametr.<br/><br/> Pokud `true`je, vyvolá kompilátor výstup sestavení, jehož binární obsah je identický v rámci kompilací, pokud jsou vstupy identické.<br/><br/>Další informace naleznete v tématu [-deterministické (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která mají být zakázána. Další informace naleznete v tématu [-bez upozornění (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Volitelný `String` parametr.<br /><br /> Zpracuje komentáře dokumentace do souboru XML. Další informace naleznete v tématu [-doc (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úloha vygeneruje informace o ladění a umístí je do souboru databáze programu (PDB). Pokud `false`Úloha negeneruje žádné ladicí informace. Výchozí hodnota je `false`. Další informace naleznete v tématu [-Debug (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Volitelný `String` parametr.<br /><br /> Nabízí pohodlný způsob, jak ohlásit C# interní chybu společnosti Microsoft. Tento parametr může mít hodnotu `prompt`, `send`nebo `none`. Pokud je parametr nastaven na `prompt`hodnotu, zobrazí se výzva, když dojde k vnitřní chybě kompilátoru. Na příkazovém řádku můžete poslat zprávu o chybě elektronicky společnosti Microsoft. Pokud je parametr nastaven na `send`hodnotu, je automaticky odeslána zpráva o chybě. Pokud je parametr nastaven na `none`hodnotu, chyba je uvedena pouze v textovém výstupu kompilátoru. Výchozí hodnota je `none`. Další informace naleznete v tématu [-errorreport (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Volitelný `Int32` parametr.<br /><br /> Určuje velikost oddílů ve výstupním souboru. Další informace naleznete v tématu [-zarovnáváníC# (možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`určuje absolutní cestu k souboru ve výstupu kompilátoru. Pokud `false`Určuje název souboru. Výchozí hodnota je `false`. Další informace naleznete v tématu [-fullpaths – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Volitelný `String` parametr.<br /><br /> Určuje název kontejneru kryptografických klíčů. Další informace naleznete v tématu [-Form-obsahoval (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Volitelný `String` parametr.<br /><br /> Určuje název souboru, který obsahuje kryptografický klíč. Další informace najdete v tématu [-keyfile (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Volitelný `String` parametr.<br /><br /> Určuje verzi jazyka, který se má použít. Další informace naleznete v tématu [-langversion – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | <xref:Microsoft.Build.Framework.ITaskItem> Volitelný`[]` parametr.<br /><br /> Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru; zdrojový soubor není umístěný do výstupního souboru.<br /><br /> Položky předané do tohoto parametru mohou mít volitelné položky metadat `LogicalName` s `Access`názvem a. `LogicalName``identifier` odpovídá parametru `/linkresource` přepínače a `Access` odpovídá parametru.`accessibility-modifier` Další informace naleznete v tématu [-linkresource – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Volitelný `String` parametr.<br /><br /> Určuje umístění `Main` metody. Další informace naleznete v tématu [-Main (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Volitelný `String` parametr.<br /><br /> Určuje název sestavení, jehož součástí bude tento modul. |
| `NoConfig` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, instruuje kompilátor, aby nekompiluje se souborem *CSc. rsp* . Další informace naleznete v tématu [-bez konfigurace (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`se potlačí zobrazení informací o banneru kompilátoru. Další informace najdete v tématu [– bez loga (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, zabrání import *knihovny mscorlib. dll*, která definuje celý obor názvů System. Tento parametr použijte, pokud chcete definovat nebo vytvořit vlastní obor názvů a objekty systému. Další informace naleznete v tématu [-nostdlib (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`nezahrnete výchozí manifest Win32. |
| `Optimize` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, povolí optimalizace. Pokud `false`zakážete optimalizace. Další informace naleznete v tématu [-optimizeC# (možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Volitelný `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Další informace naleznete v tématu [-out (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Volitelný `String` parametr.<br /><br /> Určuje název výstupního souboru referenčního sestavení. Další informace naleznete v tématu [-refout (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Volitelný `String` parametr.<br /><br /> Určuje název souboru ladicích informací. Výchozí název je název výstupního souboru s příponou *. pdb* . |
| `Platform` | Volitelný `String` parametr.<br /><br /> Určuje platformu procesoru, na kterou má výstupní soubor cílit. Tento parametr může mít hodnotu `x86`, `x64`nebo `anycpu`. Výchozí hodnota je `anycpu`. Další informace naleznete v tématu [-Platform (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | <xref:Microsoft.Build.Framework.ITaskItem> Volitelný`[]` parametr.<br /><br /> Způsobí, že úloha importuje informace o veřejném typu ze zadaných položek do aktuálního projektu. Další informace naleznete v tématu [-Reference (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> V souboru můžete zadat [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] alias odkazu přidáním metadat `Aliases` do původní položky "odkaz". [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Chcete-li například nastavit alias "LS1" v následujícím příkazovém řádku csc:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> použijete:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | <xref:Microsoft.Build.Framework.ITaskItem> Volitelný`[]` parametr.<br /><br /> Vloží prostředek .NET Framework do výstupního souboru.<br /><br /> Položky předané do tohoto parametru mohou mít volitelné položky metadat `LogicalName` s `Access`názvem a. `LogicalName``identifier` odpovídá parametru `/resource` přepínače a `Access` odpovídá parametru.`accessibility-modifier` Další informace naleznete v tématu [-Resource (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Volitelný `String` parametr.<br /><br /> Určuje soubor odpovědí obsahující příkazy pro tento úkol. Další informace naleznete v tématu [@ (určení souboru odezvy)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | <xref:Microsoft.Build.Framework.ITaskItem> Volitelný`[]` parametr.<br /><br /> Určuje jeden nebo více [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] zdrojových souborů. |
| `TargetType` | Volitelný `String` parametr.<br /><br /> Určuje formát výstupního souboru. Tento `library`parametr může mít hodnotu, která vytvoří knihovnu kódu, `exe`, která vytvoří konzolovou aplikaci, `module`, která vytvoří modul, nebo `winexe`, který vytvoří program systému Windows. Výchozí hodnota je `library`. Další informace naleznete v tématu [-target (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`aplikace považuje všechna upozornění za chyby. Další informace naleznete v tématu [-warnaserror – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Volitelný `Boolean` parametr.<br /><br /> Dá pokyn k tomu, aby úkol použil objekt vnitroprocesového kompilátoru, pokud je k dispozici. Používáno pouze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nástrojem. |
| `Utf8Output` | Volitelný `Boolean` parametr.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Další informace naleznete v tématu [-utf8output – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Volitelný `Int32` parametr.<br /><br /> Určuje úroveň upozornění pro zobrazení kompilátoru. Další informace naleznete v tématu [-warn (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která mají být považována za chyby. Další informace naleznete v tématu [-warnaserror – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Tento parametr Přepisuje `TreatWarningsAsErrors` parametr. |
| `WarningsNotAsErrors` | Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která nejsou považována za chyby. Další informace naleznete v tématu [-warnaserror – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Tento parametr je užitečný pouze v případě `TreatWarningsAsErrors` , že je parametr `true`nastaven na hodnotu. |
| `Win32Icon` | Volitelný `String` parametr.<br /><br /> Vloží soubor *. ico* do sestavení, které poskytne výstupnímu souboru požadovaný vzhled v **Průzkumníkovi souborů**. Další informace naleznete v tématu [-win32icon (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Volitelný `String` parametr.<br /><br /> Určuje manifest Win32, který se má zahrnout. |
| `Win32Resource` | Volitelný `String` parametr.<br /><br /> Vloží soubor prostředků Win32 ( *. res*) do výstupního souboru. Další informace naleznete v tématu [-win32res (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Poznámky
Kromě parametrů uvedených výše Tato úloha dědí parametry z `Microsoft.Build.Tasks.ManagedCompiler` třídy, která dědí <xref:Microsoft.Build.Tasks.ToolTaskExtension> z třídy, <xref:Microsoft.Build.Utilities.ToolTask> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad
Následující příklad používá `Csc` úlohu pro zkompilování spustitelného souboru ze zdrojových souborů `Compile` v kolekci položek.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
