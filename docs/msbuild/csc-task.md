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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7443ba29a743f4936ae104d9d0bb556fae3c4e2d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595381"
---
# <a name="csc-task"></a>Csc – úloha
Zabalí *CSc. exe*a vytvoří spustitelné soubory (soubory *. exe* ), dynamické knihovny (soubory *. dll* ) nebo kódové moduly (soubory *. netmodule* ). Další informace o souboru *CSc. exe*naleznete v tématu [ C# možnosti kompilátoru](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametry
Následující tabulka popisuje parametry úlohy `Csc`.

| Parametr | Popis |
|------------------------------| - |
| `AdditionalLibPaths` | Volitelný parametr `String[]`.<br /><br /> Určuje další adresáře, ve kterých budou hledány odkazy. Další informace naleznete v tématu [-lib (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Volitelný parametr `String`.<br /><br /> Určuje jeden nebo více modulů, které mají být součástí sestavení. Další informace naleznete v tématu [-addmodule – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, zkompiluje kód, který používá klíčové slovo [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) . Další informace naleznete v tématu [-unsafeC# (možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Volitelný parametr `String`.<br /><br /> Určuje konfigurační soubor aplikace obsahující nastavení vazby sestavení. |
| `BaseAddress` | Volitelný parametr `String`.<br /><br /> Určuje upřednostňovanou základní adresu, na které se má načíst knihovna DLL. Výchozí základní adresa pro knihovnu DLL je nastavena .NET Framework modul CLR (Common Language Runtime). Další informace naleznete v tématu [-BaseAddress (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Volitelný parametr `Boolean`.<br /><br /> Určuje, zda celočíselná aritmetická operace, která přetéká hranice datového typu, způsobuje výjimku v době běhu. Další informace naleznete v tématu [-checked (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Volitelný parametr `Int32`.<br /><br /> Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci. Další informace naleznete v části [-codepage (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Volitelný parametr `String`.<br /><br /> Určuje typ ladění. `DebugType` lze `full` nebo `pdbonly`. Výchozí hodnota je `full`, což umožňuje připojit ladicí program ke spuštěnému programu. Určení `pdbonly` umožňuje ladění zdrojového kódu při spuštění programu v ladicím programu, ale zobrazuje pouze Assembler, pokud je spuštěný program připojen k ladicímu programu.<br /><br /> Tento parametr Přepisuje parametr `EmitDebugInformation`.<br /><br /> Další informace naleznete v tématu [-Debug (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Volitelný parametr `String`.<br /><br /> Definuje symboly preprocesoru. Další informace naleznete v tématu [-defineC# (možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, určuje, že chcete umístit pouze veřejný klíč do sestavení. Pokud `false`, určuje, že chcete plně podepsané sestavení<br /><br /> Tento parametr nemá žádný vliv, pokud se nepoužívá buď s parametrem `KeyFile` nebo `KeyContainer`.<br /><br /> Další informace naleznete v tématu [-delaysign (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Volitelný parametr `Boolean`.<br/><br/> Pokud je `true`, způsobí kompilátor výstup sestavení, jehož binární obsah je identický v rámci kompilací, pokud jsou vstupy identické.<br/><br/>Další informace naleznete v tématu [-deterministické (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Volitelný parametr `String`.<br /><br /> Určuje seznam upozornění, která mají být zakázána. Další informace naleznete v tématu [-bez upozornění (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Volitelný parametr `String`.<br /><br /> Zpracuje komentáře dokumentace do souboru XML. Další informace naleznete v tématu [-doc (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, úloha vygeneruje ladicí informace a umístí ji do souboru databáze programu (PDB). Pokud `false`, úloha negeneruje žádné ladicí informace. Výchozí hodnota je `false`. Další informace naleznete v tématu [-Debug (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Volitelný parametr `String`.<br /><br /> Nabízí pohodlný způsob, jak ohlásit C# interní chybu společnosti Microsoft. Tento parametr může mít hodnotu `prompt`, `send`nebo `none`. Pokud je parametr nastaven na `prompt`, zobrazí se výzva, když dojde k vnitřní chybě kompilátoru. Na příkazovém řádku můžete poslat zprávu o chybě elektronicky společnosti Microsoft. Pokud je parametr nastavený na `send`, pošle se automaticky zpráva o chybě. Pokud je parametr nastaven na `none`, je chyba hlášena pouze v textovém výstupu kompilátoru. Výchozí hodnota je `none`. Další informace naleznete v tématu [-errorreport (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Volitelný parametr `Int32`.<br /><br /> Určuje velikost oddílů ve výstupním souboru. Další informace naleznete v tématu [-zarovnáváníC# (možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, určuje absolutní cestu k souboru ve výstupu kompilátoru. Pokud `false`, určuje název souboru. Výchozí hodnota je `false`. Další informace naleznete v tématu [-fullpaths – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Volitelný parametr `String`.<br /><br /> Určuje název kontejneru kryptografických klíčů. Další informace naleznete v tématu [-Form-obsahoval (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Volitelný parametr `String`.<br /><br /> Určuje název souboru, který obsahuje kryptografický klíč. Další informace najdete v tématu [-keyfile (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Volitelný parametr `String`.<br /><br /> Určuje verzi jazyka, který se má použít. Další informace naleznete v tématu [-langversion – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru; zdrojový soubor není umístěný do výstupního souboru.<br /><br /> Položky předané do tohoto parametru mohou mít volitelné položky metadat s názvem `LogicalName` a `Access`. `LogicalName` odpovídá parametru `identifier` `/linkresource` přepínači a `Access` odpovídá parametru `accessibility-modifier`. Další informace naleznete v tématu [-linkresource – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Volitelný parametr `String`.<br /><br /> Určuje umístění metody `Main`. Další informace naleznete v tématu [-Main (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Volitelný parametr `String`.<br /><br /> Určuje název sestavení, jehož součástí bude tento modul. |
| `NoConfig` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, instruuje kompilátor, aby nekompiluje se souborem *CSc. rsp* . Další informace naleznete v tématu [-bez konfigurace (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, potlačí zobrazování informací banneru kompilátoru. Další informace najdete v tématu [– bez loga (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, zabrání import *knihovny mscorlib. dll*, která definuje celý obor názvů System. Tento parametr použijte, pokud chcete definovat nebo vytvořit vlastní obor názvů a objekty systému. Další informace naleznete v tématu [-nostdlib (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, Nezahrnovat výchozí manifest Win32. |
| `Optimize` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, povolí optimalizace. Pokud `false`zakážete optimalizace. Další informace naleznete v tématu [-optimizeC# (možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Volitelný výstupní parametr `String`.<br /><br /> Určuje název výstupního souboru. Další informace naleznete v tématu [-out (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Volitelný parametr `String`.<br /><br /> Určuje název výstupního souboru referenčního sestavení. Další informace naleznete v tématu [-refout (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Volitelný parametr `String`.<br /><br /> Určuje název souboru ladicích informací. Výchozí název je název výstupního souboru s příponou *. pdb* . |
| `Platform` | Volitelný parametr `String`.<br /><br /> Určuje platformu procesoru, na kterou má výstupní soubor cílit. Tento parametr může mít hodnotu `x86`, `x64`nebo `anycpu`. Výchozí hodnota je `anycpu`. Další informace naleznete v tématu [-Platform (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Způsobí, že úloha importuje informace o veřejném typu ze zadaných položek do aktuálního projektu. Další informace naleznete v tématu [-Reference (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Můžete zadat alias odkazu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] v souboru [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] přidáním `Aliases` metadat do původní položky "odkaz". Chcete-li například nastavit alias "LS1" v následujícím příkazovém řádku csc:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> použijete:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Vloží prostředek .NET Framework do výstupního souboru.<br /><br /> Položky předané do tohoto parametru mohou mít volitelné položky metadat s názvem `LogicalName` a `Access`. `LogicalName` odpovídá parametru `identifier` `/resource` přepínači a `Access` odpovídá parametru `accessibility-modifier`. Další informace naleznete v tématu [-Resource (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Volitelný parametr `String`.<br /><br /> Určuje soubor odpovědí obsahující příkazy pro tento úkol. Další informace naleznete v tématu [@ (určení souboru odezvy)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje jeden nebo více [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] zdrojových souborů. |
| `TargetType` | Volitelný parametr `String`.<br /><br /> Určuje formát výstupního souboru. Tento parametr může mít hodnotu `library`, která vytvoří knihovnu kódu, `exe`, která vytvoří konzolovou aplikaci, `module`, která vytvoří modul nebo `winexe`, který vytvoří program systému Windows. Výchozí hodnota je `library`. Další informace naleznete v tématu [-target (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, zpracovává všechna upozornění jako chyby. Další informace naleznete v tématu [-warnaserror – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Volitelný parametr `Boolean`.<br /><br /> Dá pokyn k tomu, aby úkol použil objekt vnitroprocesového kompilátoru, pokud je k dispozici. Používáno pouze pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| `Utf8Output` | Volitelný parametr `Boolean`.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Další informace naleznete v tématu [-utf8output – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Volitelný parametr `Int32`.<br /><br /> Určuje úroveň upozornění pro zobrazení kompilátoru. Další informace naleznete v tématu [-warn (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Volitelný parametr `String`.<br /><br /> Určuje seznam upozornění, která mají být považována za chyby. Další informace naleznete v tématu [-warnaserror – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Tento parametr Přepisuje parametr `TreatWarningsAsErrors`. |
| `WarningsNotAsErrors` | Volitelný parametr `String`.<br /><br /> Určuje seznam upozornění, která nejsou považována za chyby. Další informace naleznete v tématu [-warnaserror – (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Tento parametr je užitečný pouze v případě, že parametr `TreatWarningsAsErrors` je nastaven na hodnotu `true`. |
| `Win32Icon` | Volitelný parametr `String`.<br /><br /> Vloží soubor *. ico* do sestavení, které poskytne výstupnímu souboru požadovaný vzhled v **Průzkumníkovi souborů**. Další informace naleznete v tématu [-win32icon (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Volitelný parametr `String`.<br /><br /> Určuje manifest Win32, který se má zahrnout. |
| `Win32Resource` | Volitelný parametr `String`.<br /><br /> Vloží soubor prostředků Win32 ( *. res*) do výstupního souboru. Další informace naleznete v tématu [-win32res (C# možnosti kompilátoru)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Poznámky
Kromě výše uvedených parametrů Tato úloha dědí parametry z třídy `Microsoft.Build.Tasks.ManagedCompiler`, která dědí z třídy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, která sama dědí z třídy <xref:Microsoft.Build.Utilities.ToolTask>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad
Následující příklad používá úlohu `Csc` ke kompilaci spustitelného souboru ze zdrojových souborů v kolekci `Compile`ch položek.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
