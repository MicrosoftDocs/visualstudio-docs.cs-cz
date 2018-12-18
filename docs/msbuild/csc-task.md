---
title: CSC – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd360a34c70d3208211b861dae064bd4c5a01595
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832357"
---
# <a name="csc-task"></a>Csc – úloha
Zabalí *csc.exe*a vytváří spustitelné soubory (*.exe* soubory), dynamické knihovny (*.dll* soubory), nebo moduly kódu (*.netmodule* soubory). Další informace o *csc.exe*, naleznete v tématu [možnosti kompilátoru C#](/dotnet/csharp/language-reference/compiler-options/index).  

## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Csc` úloh.  


| Parametr | Popis |
|------------------------------| - |
| `AdditionalLibPaths` | Volitelné `String[]` parametru.<br /><br /> Určuje další adresáře souborů pro hledání odkazů. Další informace najdete v tématu [-lib (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Volitelné `String` parametru.<br /><br /> Určuje jeden nebo více modulů jako součást sestavení. Další informace najdete v tématu [- addmodule (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zkompiluje kód, který používá [nebezpečné](/dotnet/csharp/language-reference/keywords/unsafe) – klíčové slovo. Další informace najdete v tématu [-unsafe (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Volitelné `String` parametru.<br /><br /> Určuje konfigurační soubor aplikace obsahující nastavení vazeb sestavení. |
| `BaseAddress` | Volitelné `String` parametru.<br /><br /> Určuje upřednostňovaná základní adresa, ve kterém se má načíst knihovnu DLL. Výchozí základní adresa pro knihovnu DLL se nastavuje [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] společného jazykového modulu runtime. Další informace najdete v tématu [- baseaddress (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Volitelné `Boolean` parametru.<br /><br /> Určuje, zda aritmetika, která přesahuje hranice datový typ celé číslo dojde k výjimce za běhu. Další informace najdete v tématu [-checked (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Volitelné `Int32` parametru.<br /><br /> Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace. Další informace najdete v tématu [- codepage (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Volitelné `String` parametru.<br /><br /> Určuje typ ladění. `DebugType` může být `full` nebo `pdbonly`. Výchozí hodnota je `full`, což umožňuje připojit ke spuštěnému programu ladicí program. Určení `pdbonly` umožňuje zdrojového kódu ladění, když program je spuštěn v ladicím programu, ale assembler se zobrazí pouze v případě spuštěnému programu k ladicímu programu.<br /><br /> Přepíše tento parametr `EmitDebugInformation` parametru.<br /><br /> Další informace najdete v tématu [-debug (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Volitelné `String` parametru.<br /><br /> Definuje symboly preprocesoru. Další informace najdete v tématu [-definovat (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, určuje, že chcete li plně podepsané sestavení. Pokud `false`, určuje, že chcete pouze umístit veřejný klíč v sestavení.<br /><br /> Tento parametr nemá žádný vliv, pokud nejsou použity s buď `KeyFile` nebo `KeyContainer` parametru.<br /><br /> Další informace najdete v tématu [- delaysign (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Volitelné `Boolean` parametru.<br/><br/> Pokud `true`, způsobí, že kompilátor do výstupního sestavení, jejichž binární obsah je identické napříč kompilace Pokud vstupů jsou stejné.<br/><br/>Další informace najdete v tématu [-deterministické (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Volitelné `String` parametru.<br /><br /> Určuje seznam upozornění se deaktivuje. Další informace najdete v tématu [- nowarn (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Volitelné `String` parametru.<br /><br /> Zpracuje komentáře dokumentace do souboru XML. Další informace najdete v tématu [-doc (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha generuje ladicí informace a umístí jej do souboru databáze (PDB) programu. Pokud `false`, úloha vysílá žádné informace o ladění. Výchozí hodnota je `false`. Další informace najdete v tématu [-debug (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Volitelné `String` parametru.<br /><br /> Poskytuje pohodlný způsob, jak C# interní chybu nahlásit společnosti Microsoft. Tento parametr může mít hodnotu `prompt`, `send`, nebo `none`. Pokud parametr je nastaven na `prompt`, zobrazí se výzva při výskytu vnitřní chyby kompilátoru. Na řádku vám umožní odeslat hlášení o chybě programu společnosti Microsoft. Pokud parametr je nastaven na `send`, je automaticky odeslána hlášení o chybě. Pokud parametr je nastaven na `none`, pouze v textový výstup kompilátoru hlásí chybu. Výchozí hodnota je `none`. Další informace najdete v tématu [- errorreport (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Volitelné `Int32` parametru.<br /><br /> Určuje velikost oddíly výstupního souboru. Další informace najdete v tématu [- filealign (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, určuje absolutní cestu k souboru ve výstupu kompilátoru. Pokud `false`, určuje název souboru. Výchozí hodnota je `false`. Další informace najdete v tématu [- fullpaths (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Volitelné `String` parametru.<br /><br /> Určuje název kontejneru kryptografických klíčů. Další informace najdete v tématu [- keycontainer (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Volitelné `String` parametru.<br /><br /> Určuje název souboru obsahujícího kryptografický klíč. Další informace najdete v tématu [- keyfile (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Volitelné `String` parametru.<br /><br /> Určuje verzi modulu jazyka. Další informace najdete v tématu [- langversion (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Vytvoří odkaz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] prostředků do výstupního souboru; soubor prostředku není umístěn do výstupního souboru.<br /><br /> Položek předaných do tento parametr může mít volitelná metadata položky s názvem `LogicalName` a `Access`. `LogicalName` odpovídá `identifier` parametr `/linkresource` přepnout, a `Access` odpovídá `accessibility-modifier` parametru. Další informace najdete v tématu [- linkresource (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Volitelné `String` parametru.<br /><br /> Určuje umístění `Main` metody. Další informace najdete v tématu [-main (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Volitelné `String` parametru.<br /><br /> Určuje název sestavení, které bude tento modul součástí. |
| `NoConfig` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, sděluje kompilátoru, aby proveďte kompilaci s *csc.rsp* souboru. Další informace najdete v tématu [- noconfig (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, potlačí zobrazení informací nápisu kompilátoru. Další informace najdete v tématu [- nologo (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, brání import *mscorlib.dll*, která definuje obor názvů celého systému. Tento parametr použijte, pokud chcete definovat nebo vytvořit vlastní System – obor názvů a objekty. Další informace najdete v tématu [- nostdlib (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, neobsahují výchozí manifest Win32. |
| `Optimize` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, povolí optimalizace. Pokud `false`, zakáže optimalizace. Další informace najdete v tématu [-optimalizovat (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Volitelné `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Další informace najdete v tématu [-out (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Volitelné `String` parametru.<br /><br /> Určuje název výstupního souboru referenční sestavení. Další informace najdete v tématu [- refout (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Volitelné `String` parametru.<br /><br /> Určuje název souboru ladicích informací. Výchozí název je název výstupního souboru s *PDB* rozšíření. |
| `Platform` | Volitelné `String` parametru.<br /><br /> Určuje platformu procesor, který bude cílen výstupním souborem. Tento parametr může mít hodnotu `x86`, `x64`, nebo `anycpu`. Výchozí hodnota je `anycpu`. Další informace najdete v tématu [-platform (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Způsobí, že úloha pro import informací o veřejný typ ze zadaných položek do aktuálního projektu. Další informace najdete v tématu [– referenční dokumentace (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Můžete zadat [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] alias v odkazu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] souboru tak, že přidáte metadata `Aliases` k původní položce "Odkaz". Chcete-li například nastavit alias "LS1" v příkazovém řádku následující Csc:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> měli byste použít:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Vloží [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] prostředků do výstupního souboru.<br /><br /> Položek předaných do tento parametr může mít volitelná metadata položky s názvem `LogicalName` a `Access`. `LogicalName` odpovídá `identifier` parametr `/resource` přepnout, a `Access` odpovídá `accessibility-modifier` parametru. Další informace najdete v tématu [-resource (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Volitelné `String` parametru.<br /><br /> Určuje soubor odpovědí, který obsahuje příkazy pro tuto úlohu. Další informace najdete v tématu [@ (zadat soubor odezvy)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje jeden nebo více [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] zdrojové soubory. |
| `TargetType` | Volitelné `String` parametru.<br /><br /> Určuje formát výstupního souboru. Tento parametr může mít hodnotu `library`, která vytvoří knihovnu kódu `exe`, vytváří aplikace konzoly `module`, která vytvoří modul, nebo `winexe`, vytváří Windows program. Výchozí hodnota je `library`. Další informace najdete v tématu [-target (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zpracuje všechna upozornění jako chyby. Další informace najdete v tématu [- warnaserror (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Volitelné `Boolean` parametru.<br /><br /> Úkol použije objekt vnitroprocesového kompilátoru přikáže, pokud je k dispozici. Používání pouze systémem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| `Utf8Output` | Volitelné `Boolean` parametru.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Další informace najdete v tématu [-utf8output (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Volitelné `Int32` parametru.<br /><br /> Určuje úroveň upozornění kompilátoru k zobrazení. Další informace najdete v tématu [-warn (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Volitelné `String` parametru.<br /><br /> Označí seznam upozornění pro nakládání s chybami. Další informace najdete v tématu [- warnaserror (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Přepíše tento parametr `TreatWarningsAsErrors` parametru. |
| `WarningsNotAsErrors` | Volitelné `String` parametru.<br /><br /> Označí seznam upozornění, která nemají být považována za chyby. Další informace najdete v tématu [- warnaserror (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Tento parametr je užitečná pouze pokud `TreatWarningsAsErrors` parametr je nastaven na `true`. |
| `Win32Icon` | Volitelné `String` parametru.<br /><br /> Vloží *.ico* souboru v sestavení, které dává výstupnímu souboru požadovaný vzhled v **Průzkumníka souborů**. Další informace najdete v tématu [-win32icon (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Volitelné `String` parametru.<br /><br /> Určuje manifest Win32 mají být zahrnuty. |
| `Win32Resource` | Volitelné `String` parametru.<br /><br /> Vloží prostředek systému Win32 (*.res*) soubor do výstupního souboru. Další informace najdete v tématu [-win32res (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze `Microsoft.Build.Tasks.ManagedCompiler` třída, která dědí z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md).  

## <a name="example"></a>Příklad  
 V následujícím příkladu `Csc` úloha kompilace spustitelný soubor ze zdrojových souborů v `Compile` kolekci položek.  

```xml  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  

## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)
