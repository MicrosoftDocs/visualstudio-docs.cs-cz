---
title: CSC – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 657535e73294508ac59330cd379c1c6bd192a0b2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237377"
---
# <a name="csc-task"></a>Csc – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zabalí CSC.exe a vytváří spustitelné soubory (soubory .exe), dynamické knihovny (soubory .dll) nebo moduly kódu (.netmodule soubory). Další informace o CSC.exe, naleznete v tématu [možnosti kompilátoru C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Csc` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Volitelné `String[]` parametru.<br /><br /> Určuje další adresáře souborů pro hledání odkazů. Další informace najdete v tématu [/lib (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|Volitelné `String` parametru.<br /><br /> Určuje jeden nebo více modulů jako součást sestavení. Další informace najdete v tématu [/addmodule (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zkompiluje kód, který používá [nebezpečné](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) – klíčové slovo. Další informace najdete v tématu [/ unsafe (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|Volitelné `String` parametru.<br /><br /> Určuje konfigurační soubor aplikace obsahující nastavení vazeb sestavení.|  
|`BaseAddress`|Volitelné `String` parametru.<br /><br /> Určuje upřednostňovaná základní adresa, ve kterém se má načíst knihovnu DLL. Výchozí základní adresa pro knihovnu DLL se nastavuje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] společného jazykového modulu runtime. Další informace najdete v tématu [/BaseAddress (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|Volitelné `Boolean` parametru.<br /><br /> Určuje, zda aritmetika, která přesahuje hranice datový typ celé číslo dojde k výjimce za běhu. Další informace najdete v tématu [/ checked (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|Volitelné `Int32` parametru.<br /><br /> Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace. Další informace najdete v tématu [/codepage (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|Volitelné `String` parametru.<br /><br /> Určuje typ ladění. `DebugType` může být `full` nebo `pdbonly`. Výchozí hodnota je `full`, což umožňuje připojit ke spuštěnému programu ladicí program. Určení `pdbonly` umožňuje zdrojového kódu ladění, když program je spuštěn v ladicím programu, ale assembler se zobrazí pouze v případě spuštěnému programu k ladicímu programu.<br /><br /> Přepíše tento parametr `EmitDebugInformation` parametru.<br /><br /> Další informace najdete v tématu [/Debug (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|Volitelné `String` parametru.<br /><br /> Definuje symboly preprocesoru. Další informace najdete v tématu [/ define (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, určuje, že chcete li plně podepsané sestavení. Pokud `false`, určuje, že chcete pouze umístit veřejný klíč v sestavení.<br /><br /> Tento parametr nemá žádný vliv, pokud nejsou použity s buď `KeyFile` nebo `KeyContainer` parametru.<br /><br /> Další informace najdete v tématu [/delaysign (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|Volitelné `String` parametru.<br /><br /> Určuje seznam upozornění se deaktivuje. Další informace najdete v tématu [/nowarn (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|Volitelné `String` parametru.<br /><br /> Zpracuje komentáře dokumentace do souboru XML. Další informace najdete v tématu [/DOC (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha generuje ladicí informace a umístí jej do souboru databáze (PDB) programu. Pokud `false`, úloha vysílá žádné informace o ladění. Výchozí hodnota je `false`. Další informace najdete v tématu [/Debug (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|Volitelné `String` parametru.<br /><br /> Poskytuje pohodlný způsob, jak C# interní chybu nahlásit společnosti Microsoft. Tento parametr může mít hodnotu `prompt`, `send`, nebo `none`. Pokud parametr je nastaven na `prompt`, zobrazí se výzva při výskytu vnitřní chyby kompilátoru. Na řádku vám umožní odeslat hlášení o chybě programu společnosti Microsoft. Pokud parametr je nastaven na `send`, je automaticky odeslána hlášení o chybě. Pokud parametr je nastaven na `none`, pouze v textový výstup kompilátoru hlásí chybu. Výchozí hodnota je `none`. Další informace najdete v tématu [/errorreport (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|Volitelné `Int32` parametru.<br /><br /> Určuje velikost oddíly výstupního souboru. Další informace najdete v tématu [/filealign (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, určuje absolutní cestu k souboru ve výstupu kompilátoru. Pokud `false`, určuje název souboru. Výchozí hodnota je `false`. Další informace najdete v tématu [/fullpaths (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|Volitelné `String` parametru.<br /><br /> Určuje název kontejneru kryptografických klíčů. Další informace najdete v tématu [/keycontainer (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|Volitelné `String` parametru.<br /><br /> Určuje název souboru obsahujícího kryptografický klíč. Další informace najdete v tématu [/keyfile (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|Volitelné `String` parametru.<br /><br /> Určuje verzi modulu jazyka. Další informace najdete v tématu [/langversion (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Vytvoří odkaz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] prostředků do výstupního souboru; soubor prostředku není umístěn do výstupního souboru.<br /><br /> Položek předaných do tento parametr může mít volitelná metadata položky s názvem `LogicalName` a `Access`. `LogicalName` odpovídá `identifier` parametr `/linkresource` přepnout, a `Access` odpovídá `accessibility-modifier` parametru. Další informace najdete v tématu [/linkresource (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|Volitelné `String` parametru.<br /><br /> Určuje umístění `Main` metody. Další informace najdete v tématu [/Main (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|Volitelné `String` parametru.<br /><br /> Určuje název sestavení, které bude tento modul součástí.|  
|`NoConfig`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, instruuje kompilátor, ne pro kompilaci pomocí souboru csc.rsp. Další informace najdete v tématu [/noconfig (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, potlačí zobrazení informací nápisu kompilátoru. Další informace najdete v tématu [/nologo (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, brání import mscorlib.dll, která definuje obor názvů celého systému. Tento parametr použijte, pokud chcete definovat nebo vytvořit vlastní System – obor názvů a objekty. Další informace najdete v tématu [/nostdlib (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, neobsahují výchozí manifest Win32.|  
|`Optimize`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, povolí optimalizace. Pokud `false`, zakáže optimalizace. Další informace najdete v tématu [/ optimize (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|Volitelné `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Další informace najdete v tématu [/out (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|Volitelné `String` parametru.<br /><br /> Určuje název souboru ladicích informací. Výchozí název je název výstupního souboru s příponou .pdb.|  
|`Platform`|Volitelné `String` parametru.<br /><br /> Určuje platformu procesor, který bude cílen výstupním souborem. Tento parametr může mít hodnotu `x86`, `x64`, nebo `anycpu`. Výchozí hodnota je `anycpu`. Další informace najdete v tématu [/Platform (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Způsobí, že úloha pro import informací o veřejný typ ze zadaných položek do aktuálního projektu. Další informace najdete v tématu [/Reference (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> Můžete zadat [!INCLUDE[csprcs](../includes/csprcs-md.md)] alias v odkazu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru tak, že přidáte metadata `Aliases` k původní položce "Odkaz". Chcete-li například nastavit alias "LS1" v příkazovém řádku následující CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> měli byste použít:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Vloží [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] prostředků do výstupního souboru.<br /><br /> Položek předaných do tento parametr může mít volitelná metadata položky s názvem `LogicalName` a `Access`. `LogicalName` odpovídá `identifier` parametr `/resource` přepnout, a `Access` odpovídá `accessibility-modifier` parametru. Další informace najdete v tématu [/Resource (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|Volitelné `String` parametru.<br /><br /> Určuje soubor odpovědí, který obsahuje příkazy pro tuto úlohu. Další informace najdete v tématu [@ (určení souboru odezvy)](http://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje jeden nebo více [!INCLUDE[csprcs](../includes/csprcs-md.md)] zdrojové soubory.|  
|`TargetType`|Volitelné `String` parametru.<br /><br /> Určuje formát výstupního souboru. Tento parametr může mít hodnotu `library`, která vytvoří knihovnu kódu `exe`, vytváří aplikace konzoly `module`, která vytvoří modul, nebo `winexe`, vytváří Windows program. Výchozí hodnota je `library`. Další informace najdete v tématu [/Target (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zpracuje všechna upozornění jako chyby. Další informace najdete v tématu [/warnaserror (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|Volitelné `Boolean` parametru.<br /><br /> Úkol použije objekt vnitroprocesového kompilátoru přikáže, pokud je k dispozici. Používání pouze systémem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Volitelné `Boolean` parametru.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Další informace najdete v tématu [/utf8output (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|Volitelné `Int32` parametru.<br /><br /> Určuje úroveň upozornění kompilátoru k zobrazení. Další informace najdete v tématu [/ warn (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|Volitelné `String` parametru.<br /><br /> Označí seznam upozornění pro nakládání s chybami. Další informace najdete v tématu [/warnaserror (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Přepíše tento parametr `TreatWarningsAsErrors` parametru.|  
|`WarningsNotAsErrors`|Volitelné `String` parametru.<br /><br /> Označí seznam upozornění, která nemají být považována za chyby. Další informace najdete v tématu [/warnaserror (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Tento parametr je užitečná pouze pokud `TreatWarningsAsErrors` parametr je nastaven na `true`.|  
|`Win32Icon`|Volitelné `String` parametru.<br /><br /> Vloží soubor .ico do sestavení, které dává výstupnímu souboru požadovaný vzhled v Průzkumníku souborů. Další informace najdete v tématu [/win32icon (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|Volitelné `String` parametru.<br /><br /> Určuje manifest Win32 mají být zahrnuty.|  
|`Win32Resource`|Volitelné `String` parametru.<br /><br /> Do výstupního souboru vloží soubor prostředků (.res) Win32. Další informace najdete v tématu [/win32res (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze `Microsoft.Build.Tasks.ManagedCompiler` třída, která dědí z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Csc` úloha kompilace spustitelný soubor ze zdrojových souborů v `Compile` kolekci položek.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)



