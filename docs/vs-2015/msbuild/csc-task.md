---
title: Úloha CSc | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0dd27fe64982e77872e37ec01dbdb71a0a141ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694103"
---
# <a name="csc-task"></a>Csc – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zalomí CSC.exe a vytváří spustitelné soubory (soubory. exe), dynamické knihovny (soubory. dll) nebo kódové moduly (soubory. netmodule). Další informace o CSC.exe najdete v tématu [Možnosti kompilátoru C#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Csc` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Volitelný `String[]` parametr.<br /><br /> Určuje další adresáře, ve kterých budou hledány odkazy. Další informace naleznete v tématu [/lib (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|Volitelný `String` parametr.<br /><br /> Určuje jeden nebo více modulů, které mají být součástí sestavení. Další informace naleznete v tématu [/addmodule (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` zkompiluje kód, který používá klíčové slovo [unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) . Další informace naleznete v tématu [/unsafe (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|Volitelný `String` parametr.<br /><br /> Určuje konfigurační soubor aplikace obsahující nastavení vazby sestavení.|  
|`BaseAddress`|Volitelný `String` parametr.<br /><br /> Určuje upřednostňovanou základní adresu, na které se má načíst knihovna DLL. Výchozí základní adresa pro knihovnu DLL je nastavena modulem [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] CLR (Common Language Runtime). Další informace naleznete v tématu [/BaseAddress (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|Volitelný `Boolean` parametr.<br /><br /> Určuje, zda celočíselná aritmetická operace, která přetéká hranice datového typu, způsobuje výjimku v době běhu. Další informace naleznete v tématu [/checked (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|Volitelný `Int32` parametr.<br /><br /> Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci. Další informace naleznete v tématu [/codepage (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|Volitelný `String` parametr.<br /><br /> Určuje typ ladění. `DebugType` může být `full` nebo `pdbonly` . Výchozí hodnota je `full` , což umožňuje připojit ladicí program ke spuštěnému programu. Určení `pdbonly` umožňuje ladění zdrojového kódu při spuštění programu v ladicím programu, ale zobrazí pouze Assembler, pokud je spuštěný program připojen k ladicímu programu.<br /><br /> Tento parametr Přepisuje `EmitDebugInformation` parametr.<br /><br /> Další informace naleznete v tématu [/Debug (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|Volitelný `String` parametr.<br /><br /> Definuje symboly preprocesoru. Další informace naleznete v tématu [/define (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , určuje, že chcete sestavení plně podepsané. Pokud `false` , určuje, že chcete umístit pouze veřejný klíč do sestavení.<br /><br /> Tento parametr nemá žádný vliv, pokud se nepoužívá buď s `KeyFile` `KeyContainer` parametrem nebo.<br /><br /> Další informace naleznete v tématu [/delaysign (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která mají být zakázána. Další informace naleznete v tématu [/nowarn (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|Volitelný `String` parametr.<br /><br /> Zpracuje komentáře dokumentace do souboru XML. Další informace naleznete v tématu [/doc (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` úloha vygeneruje informace o ladění a umístí je do souboru databáze programu (PDB). Pokud `false` Úloha negeneruje žádné ladicí informace. Výchozí je `false`. Další informace naleznete v tématu [/Debug (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|Volitelný `String` parametr.<br /><br /> Nabízí pohodlný způsob, jak ohlásit interní chybu v jazyce C# společnosti Microsoft. Tento parametr může mít hodnotu `prompt` , `send` nebo `none` . Pokud je parametr nastaven na hodnotu `prompt` , zobrazí se výzva, když dojde k vnitřní chybě kompilátoru. Na příkazovém řádku můžete poslat zprávu o chybě elektronicky společnosti Microsoft. Pokud je parametr nastaven na hodnotu `send` , je automaticky odeslána zpráva o chybě. Pokud je parametr nastaven na hodnotu `none` , chyba je uvedena pouze v textovém výstupu kompilátoru. Výchozí je `none`. Další informace naleznete v tématu [/errorreport (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|Volitelný `Int32` parametr.<br /><br /> Určuje velikost oddílů ve výstupním souboru. Další informace naleznete v tématu [/filealign (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` určuje absolutní cestu k souboru ve výstupu kompilátoru. Pokud `false` Určuje název souboru. Výchozí je `false`. Další informace naleznete v tématu [/fullpaths (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|Volitelný `String` parametr.<br /><br /> Určuje název kontejneru kryptografických klíčů. Další informace naleznete v tématu [/keycontainer (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|Volitelný `String` parametr.<br /><br /> Určuje název souboru, který obsahuje kryptografický klíč. Další informace naleznete v tématu [/keyfile (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|Volitelný `String` parametr.<br /><br /> Určuje verzi jazyka, který se má použít. Další informace naleznete v tématu [/langversion (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vytvoří odkaz na [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] prostředek ve výstupním souboru; soubor prostředků není umístěný do výstupního souboru.<br /><br /> Položky předané do tohoto parametru mohou mít volitelné položky metadat s názvem `LogicalName` a `Access` . `LogicalName` odpovídá `identifier` parametru `/linkresource` přepínače a `Access` odpovídá `accessibility-modifier` parametru. Další informace naleznete v tématu [/linkresource (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|Volitelný `String` parametr.<br /><br /> Určuje umístění `Main` metody. Další informace naleznete v tématu [/Main (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|Volitelný `String` parametr.<br /><br /> Určuje název sestavení, jehož součástí bude tento modul.|  
|`NoConfig`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , instruuje kompilátor, aby nekompiluje se souborem CSc. rsp. Další informace naleznete v tématu [/noconfig (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` se potlačí zobrazení informací o banneru kompilátoru. Další informace naleznete v tématu [/nologo (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , zabraňuje importu mscorlib.dll, který definuje celý obor názvů System. Tento parametr použijte, pokud chcete definovat nebo vytvořit vlastní obor názvů a objekty systému. Další informace naleznete v tématu [/nostdlib (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` nezahrnete výchozí manifest Win32.|  
|`Optimize`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , povolí optimalizace. Pokud `false` zakážete optimalizace. Další informace naleznete v tématu [/optimize (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|Volitelný `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Další informace naleznete v tématu [/out (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|Volitelný `String` parametr.<br /><br /> Určuje název souboru ladicích informací. Výchozí název je název výstupního souboru s příponou. pdb.|  
|`Platform`|Volitelný `String` parametr.<br /><br /> Určuje platformu procesoru, na kterou má výstupní soubor cílit. Tento parametr může mít hodnotu `x86` , `x64` nebo `anycpu` . Výchozí je `anycpu`. Další informace naleznete v tématu [/Platform (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Způsobí, že úloha importuje informace o veřejném typu ze zadaných položek do aktuálního projektu. Další informace naleznete v tématu [/Reference (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> V souboru můžete zadat [!INCLUDE[csprcs](../includes/csprcs-md.md)] alias odkazu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] přidáním metadat `Aliases` do původní položky "odkaz". Chcete-li například nastavit alias "LS1" v následujícím příkazovém řádku CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> použijete:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vloží [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] prostředek do výstupního souboru.<br /><br /> Položky předané do tohoto parametru mohou mít volitelné položky metadat s názvem `LogicalName` a `Access` . `LogicalName` odpovídá `identifier` parametru `/resource` přepínače a `Access` odpovídá `accessibility-modifier` parametru. Další informace naleznete v tématu [/Resource (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|Volitelný `String` parametr.<br /><br /> Určuje soubor odpovědí obsahující příkazy pro tento úkol. Další informace naleznete v tématu [@ (určení souboru odezvy)](https://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje jeden nebo více [!INCLUDE[csprcs](../includes/csprcs-md.md)] zdrojových souborů.|  
|`TargetType`|Volitelný `String` parametr.<br /><br /> Určuje formát výstupního souboru. Tento parametr může mít hodnotu `library` , která vytvoří knihovnu kódu, `exe` , která vytvoří konzolovou aplikaci, `module` , která vytvoří modul, nebo `winexe` , který vytvoří program systému Windows. Výchozí hodnota je `library`. Další informace naleznete v tématu [/target (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` aplikace považuje všechna upozornění za chyby. Další informace naleznete v tématu [/warnaserror (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|Volitelný `Boolean` parametr.<br /><br /> Dá pokyn k tomu, aby úkol použil objekt vnitroprocesového kompilátoru, pokud je k dispozici. Používáno pouze nástrojem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|`Utf8Output`|Volitelný `Boolean` parametr.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Další informace naleznete v tématu [/utf8output (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|Volitelný `Int32` parametr.<br /><br /> Určuje úroveň upozornění pro zobrazení kompilátoru. Další informace naleznete v tématu [/warn (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která mají být považována za chyby. Další informace naleznete v tématu [/warnaserror (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Tento parametr Přepisuje `TreatWarningsAsErrors` parametr.|  
|`WarningsNotAsErrors`|Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která nejsou považována za chyby. Další informace naleznete v tématu [/warnaserror (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Tento parametr je užitečný pouze v případě, že `TreatWarningsAsErrors` je parametr nastaven na hodnotu `true` .|  
|`Win32Icon`|Volitelný `String` parametr.<br /><br /> Vloží soubor. ico do sestavení, které poskytne výstupnímu souboru požadovaný vzhled v Průzkumníkovi souborů. Další informace naleznete v tématu [/win32icon (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|Volitelný `String` parametr.<br /><br /> Určuje manifest Win32, který se má zahrnout.|  
|`Win32Resource`|Volitelný `String` parametr.<br /><br /> Vloží soubor prostředků Win32 (. res) do výstupního souboru. Další informace naleznete v tématu [parametr/win32res (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Poznámky  
 Kromě parametrů uvedených výše Tato úloha dědí parametry z `Microsoft.Build.Tasks.ManagedCompiler` třídy, která dědí z třídy <xref:Microsoft.Build.Tasks.ToolTaskExtension> , která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Csc` úlohu pro zkompilování spustitelného souboru ze zdrojových souborů v `Compile` kolekci položek.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)
