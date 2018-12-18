---
title: Vbc – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/12/2018
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf2ab82b16d3cdaf493afc15f506dc237e6a91d4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937873"
---
# <a name="vbc-task"></a>Vbc – úloha
Zabalí *vbc.exe*, která vytváří spustitelné soubory (*.exe*), dynamické knihovny (*.dll*), nebo moduly kódu (*.netmodule*). Další informace o *vbc.exe*, naleznete v tématu [příkazového řádku kompilátoru jazyka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index).  

## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Vbc` úloh.  


| Parametr | Popis |
|------------------------------| - |
| `AdditionalLibPaths` | Volitelné `String[]` parametru.<br /><br /> Určuje další složky, ve kterých se mají hledat sestavení zadaná v atributu odkazy. |
| `AddModules` | Volitelné `String[]` parametru.<br /><br /> Způsobí, že kompilátor, aby všechny informace ze zadané soubory, které jsou k dispozici do projektu je aktuálně kompilován typu. Tento parametr [- addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) přepnout z *vbc.exe* kompilátoru. |
| `BaseAddress` | Volitelné `String` parametru.<br /><br /> Určuje základní adresu knihovny DLL. Tento parametr [- baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) přepnout z *vbc.exe* kompilátoru. |
| `CodePage` | Volitelné `Int32` parametru.<br /><br /> Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace. Tento parametr [- znaková stránka](/dotnet/visual-basic/reference/command-line-compiler/codepage) přepnout z *vbc.exe* kompilátoru. |
| `DebugType` | Volitelné `String[]` parametru.<br /><br /> Způsobí, že kompilátor generovat ladicí informace. Tento parametr může mít následující hodnoty:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Výchozí hodnota je `full`, což umožňuje připojení ladicího programu ke spuštěnému programu. Hodnota `pdbonly` umožňuje ladění kódu zdroj, když program je spuštěn v ladicím programu, ale jenom v případě, že je spuštěný program je připojen k ladicímu programu se zobrazí kód jazyka sestavení. Další informace najdete v tématu [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Volitelné `String[]` parametru.<br /><br /> Definuje podmíněné konstanty kompilátoru. Dvojice symbol/hodnota jsou odděleny středníkem a jsou zadány pomocí následující syntaxe:<br /><br /> *symbol1* `=` *hodnota1* `;` *symbol2* `=` *hodnota2*<br /><br /> Tento parametr [-definovat](/dotnet/visual-basic/reference/command-line-compiler/define) přepnout z *vbc.exe* kompilátoru. |
| `DelaySign` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha umístí veřejný klíč v sestavení. Pokud `false`, úloha plně podepíše sestavení. Výchozí hodnota je `false`. Tento parametr nemá žádný vliv, pokud nejsou použity s `KeyFile` parametr nebo `KeyContainer` parametru. Tento parametr [- delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) přepnout z *vbc.exe* kompilátoru. |
| `Deterministic` | Volitelné `Boolean` parametru.<br/><br/> Pokud `true`, způsobí, že kompilátor do výstupního sestavení, jejichž binární obsah je identické napříč kompilace Pokud vstupů jsou stejné.<br/><br/>Další informace najdete v tématu [-deterministické](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Volitelné `String` parametru.<br /><br /> Potlačí zadaná upozornění. Stačí zadat číselnou část identifikátoru upozornění. Více varování je odděleno středníky. Tento parametr [- nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) přepnout z *vbc.exe* kompilátoru. |
| `DocumentationFile` | Volitelné `String` parametru.<br /><br /> Zpracuje komentáře dokumentace do zadaného souboru XML. Přepíše tento parametr `GenerateDocumentation` atribut. Další informace najdete v tématu [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha generuje ladicí informace a umístí jej do *PDB* souboru. Další informace najdete v tématu [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Volitelné `String` parametru.<br /><br /> Určuje, jak by měl úkol ohlásit interní chyby kompilátoru. Tento parametr může mít následující hodnoty:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Pokud `prompt` určena a dojde k chybě vnitřní kompilátor, bude uživatel vyzván s možností, zda chcete odesílat data chyby do Microsoftu.<br /><br /> Pokud `send` určena a dojde k chybě vnitřní kompilátor, úloha odesílá data chyby společnosti Microsoft.<br /><br /> Výchozí hodnota je `none`, která hlásí chyby v textu pouze výstup.<br /><br /> Tento parametr [- errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) přepnout z *vbc.exe* kompilátoru. |
| `FileAlignment` | Volitelné `Int32` parametru.<br /><br /> Určuje, v bajtech, kam chcete zarovnat oddíly výstupního souboru. Tento parametr může mít následující hodnoty:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Tento parametr [- filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) přepnout z *vbc.exe* kompilátoru. |
| `GenerateDocumentation` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, generuje informace o dokumentaci a umístí jej do souboru XML s názvem spustitelného souboru nebo knihovny, která vytváří úlohy. Další informace najdete v tématu [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Obory názvů se importuje z zadanou položku kolekce. Tento parametr [– importuje](/dotnet/visual-basic/reference/command-line-compiler/imports) přepnout z *vbc.exe* kompilátoru. |
| `KeyContainer` | Volitelné `String` parametru.<br /><br /> Určuje název kontejneru kryptografických klíčů. Tento parametr [- keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) přepnout z *vbc.exe* kompilátoru. |
| `KeyFile` | Volitelné `String` parametru.<br /><br /> Určuje název souboru obsahujícího kryptografický klíč. Další informace najdete v tématu [- keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Volitelné <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Určuje jazykovou verzi, "9" nebo "10". |
| `LinkResources` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Vytvoří odkaz na prostředek rozhraní .NET Framework do výstupního souboru; soubor prostředků není umístěn do výstupního souboru. Tento parametr [- linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) přepnout z *vbc.exe* kompilátoru. |
| `MainEntryPoint` | Volitelné `String` parametru.<br /><br /> Určuje třídu nebo modul, který obsahuje `Sub Main` postup. Tento parametr [– hlavní](/dotnet/visual-basic/reference/command-line-compiler/main) přepnout z *vbc.exe* kompilátoru. |
| `ModuleAssemblyName` | Volitelné `String` parametru.<br /><br /> Určuje sestavení, které tento modul je součástí. |
| `NoConfig` | Volitelné `Boolean` parametru.<br /><br /> Určuje, zda kompilátor by neměl používat *vbc.rsp* souboru. Tento parametr [- noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) parametr *vbc.exe* kompilátoru. |
| `NoLogo` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, potlačí zobrazení informací nápisu kompilátoru. Tento parametr [- nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) přepnout z *vbc.exe* kompilátoru. |
| `NoStandardLib` | Volitelné `Boolean` parametru.<br /><br /> Způsobí, že kompilátor nelze odkazovat na standardní knihovny. Tento parametr [- nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) přepnout z *vbc.exe* kompilátoru. |
| `NoVBRuntimeReference` | Volitelné `Boolean` parametru.<br /><br /> Pouze pro interní použití. Při hodnotě true se brání automatické odkaz na *Microsoft.VisualBasic.dll*. |
| `NoWarnings` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha potlačí všechna upozornění. Další informace najdete v tématu [- nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, povolí optimalizace kompilátoru. Tento parametr [– optimalizace](/dotnet/visual-basic/reference/command-line-compiler/optimize) přepnout z *vbc.exe* kompilátoru. |
| `OptionCompare` | Volitelné `String` parametru.<br /><br /> Určuje způsob porovnávání řetězců. Tento parametr může mít následující hodnoty:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Hodnota `binary` Určuje, že úkol používá binární porovnání řetězců. Hodnota `text` Určuje, že úkol používá textové porovnávání řetězců. Výchozí hodnota tohoto parametru je `binary`. Tento parametr [- optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) přepnout z *vbc.exe* kompilátoru. |
| `OptionExplicit` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, se vyžaduje explicitní deklaraci proměnných. Tento parametr [- optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) přepnout z *vbc.exe* kompilátoru. |
| `OptionInfer` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, povolí odvozování typů proměnných. |
| `OptionStrict` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha vynutí sémantiku přísného typu pro omezení převodů implicitních typů. Tento parametr [- optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) přepnout z *vbc.exe* kompilátoru. |
| `OptionStrictType` | Volitelné `String` parametru.<br /><br /> Určuje, které sémantiku přísného typu generovat upozornění. V současné době se podporuje jenom "vlastní". Tento parametr [- optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) přepnout z *vbc.exe* kompilátoru. |
| `OutputAssembly` | Volitelné `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Tento parametr [-out](/dotnet/visual-basic/reference/command-line-compiler/out) přepnout z *vbc.exe* kompilátoru. |
| `Platform` | Volitelné `String` parametru.<br /><br /> Určuje platformu procesor, který bude cílen výstupním souborem. Tento parametr může mít hodnotu `x86`, `x64`, `Itanium`, nebo `anycpu`. Výchozí hodnota je `anycpu`. Tento parametr [– platforma](/dotnet/visual-basic/reference/command-line-compiler/platform) přepnout z *vbc.exe* kompilátoru. |
| `References` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Způsobí, že úloha pro import informací o veřejný typ ze zadaných položek do aktuálního projektu. Tento parametr [– referenční dokumentace](/dotnet/visual-basic/reference/command-line-compiler/reference) přepnout z *vbc.exe* kompilátoru. |
| `RemoveIntegerChecks` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zakáže chyby kontroly přetečení celých čísel. Výchozí hodnota je `false`. Tento parametr [- removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) přepnout z *vbc.exe* kompilátoru. |
| `Resources` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Vloží prostředek rozhraní .NET Framework do výstupního souboru. Tento parametr [-prostředků](/dotnet/visual-basic/reference/command-line-compiler/resource) přepnout z *vbc.exe* kompilátoru. |
| `ResponseFiles` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje soubor odpovědí, který obsahuje příkazy pro tuto úlohu. Tento parametr [@ (určení souboru odezvy)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) možnost *vbc.exe* kompilátoru. |
| `RootNamespace` | Volitelné `String` parametru.<br /><br /> Určuje kořenový obor názvů pro všechny deklarace typů. Tento parametr [- rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) přepnout z *vbc.exe* kompilátoru. |
| `SdkPath` | Volitelné `String` parametru.<br /><br /> Určuje umístění *mscorlib.dll* a *microsoft.visualbasic.dll*. Tento parametr [- sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) přepnout z *vbc.exe* kompilátoru. |
| `Sources` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje jeden nebo více souborů zdrojového jazyka Visual Basic. |
| `TargetCompactFramework` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, cíle úlohy [!INCLUDE[Compact](../extensibility/includes/compact_md.md)]. Tento přepínač odpovídá [- netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) přepnout z *vbc.exe* kompilátoru. |
| `TargetType` | Volitelné `String` parametru.<br /><br /> Určuje formát výstupního souboru. Tento parametr může mít hodnotu `library`, která vytvoří knihovnu kódu `exe`, vytváří aplikace konzoly `module`, která vytvoří modul, nebo `winexe`, vytváří Windows program. Výchozí hodnota je `library`. Tento parametr [– cíl](/dotnet/visual-basic/reference/command-line-compiler/target) přepnout z *vbc.exe* kompilátoru. |
| `Timeout` | Volitelné `Int32` parametru.<br /><br /> Určuje množství času, v milisekundách, po jejichž uplynutí je spustitelný soubor s úkolem ukončen. Výchozí hodnota je `Int.MaxValue`, která udává, že neexistuje žádný časový limit. |
| `ToolPath` | Volitelné `String` parametru.<br /><br /> Určuje umístění, kde bude úloha načtení základní spustitelného souboru (*vbc.exe*). Pokud není tento parametr zadán, použije úloha instalační cestu sady SDK odpovídající verzi rozhraní framework, na kterém běží [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `TreatWarningsAsErrors` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, všechna upozornění jsou považována za chyby. Další informace najdete v tématu [- warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Volitelné `Boolean` parametru.<br /><br /> Úkol použije objekt vnitroprocesového kompilátoru přikáže, pokud je k dispozici. Používání pouze systémem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| `Utf8Output` | Volitelné `Boolean` parametru.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) přepnout z *vbc.exe* kompilátoru. |
| `Verbosity` | Volitelné `String` parametru.<br /><br /> Určuje podrobnost výstupu kompilátoru. Úroveň podrobností může být `Quiet`, `Normal` (výchozí), nebo `Verbose`. |
| `WarningsAsErrors` | Volitelné `String` parametru.<br /><br /> Označí seznam upozornění pro nakládání s chybami. Další informace najdete v tématu [- warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Přepíše tento parametr `TreatWarningsAsErrors` parametru. |
| `WarningsNotAsErrors` | Volitelné `String` parametru.<br /><br /> Označí seznam upozornění, která nemají být považována za chyby. Další informace najdete v tématu [- warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Tento parametr je užitečná pouze pokud `TreatWarningsAsErrors` parametr je nastaven na `true`. |
| `Win32Icon` | Volitelné `String` parametru.<br /><br /> Vloží *.ico* souboru v sestavení, které dává výstupnímu souboru požadovaný vzhled v **Průzkumníka souborů**. Tento parametr [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) přepnout z *vbc.exe* kompilátoru. |
| `Win32Resources` | Volitelné `String` parametru.<br /><br /> Vloží prostředek systému Win32 (*.res*) soubor do výstupního souboru. Tento parametr [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) přepnout z *vbc.exe* kompilátoru. |

## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md).  

## <a name="example"></a>Příklad  
 Následující příklad se zkompiluje projekt jazyka Visual Basic.  

```xml  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  

## <a name="see-also"></a>Viz také:  
 [Kompilátor příkazového řádku jazyka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
