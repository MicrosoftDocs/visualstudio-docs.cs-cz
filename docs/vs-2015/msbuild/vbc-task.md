---
title: Úloha Vbc | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6edc8b246055dcd8efdb32f4118f81a535635d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683813"
---
# <a name="vbc-task"></a>Vbc – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zalomí vbc.exe, které vytváří spustitelné soubory (. exe), dynamické knihovny (. dll) nebo kódové moduly (. netmodule). Další informace o vbc.exe najdete v tématu [Visual Basic kompilátoru příkazového řádku](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Vbc` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Volitelný `String[]` parametr.<br /><br /> Určuje další složky, ve kterých budou hledána sestavení zadaná v atributu References.|  
|`AddModules`|Volitelný `String[]` parametr.<br /><br /> Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete. Tento parametr odpovídá přepínači [/addmodule](https://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) vbc.exe kompilátoru.|  
|`BaseAddress`|Volitelný `String` parametr.<br /><br /> Určuje základní adresu knihovny DLL. Tento parametr odpovídá přepínači [/BaseAddress](https://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) kompilátoru vbc.exe.|  
|`CodePage`|Volitelný `Int32` parametr.<br /><br /> Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci. Tento parametr odpovídá přepínači [/codepage](https://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) kompilátoru vbc.exe.|  
|`DebugType`|Volitelný `String[]` parametr.<br /><br /> Způsobí, že kompilátor generuje ladicí informace. Tento parametr může mít následující hodnoty:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Výchozí hodnota je `full` , která umožňuje připojit k běžícímu programu ladicí program. Hodnota `pdbonly` umožňuje ladění zdrojového kódu při spuštění programu v ladicím programu, ale zobrazuje kód jazyka sestavení pouze v případě, že je spuštěný program připojen k ladicímu programu. Další informace najdete v tématu [/Debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|Volitelný `String[]` parametr.<br /><br /> Definuje podmíněné konstanty kompilátoru. Páry symbol/hodnota jsou odděleny středníky a jsou zadány s následující syntaxí:<br /><br /> *symbol1* `=` *hodnota1* `;` *symbol2* `=` *hodnota2*<br /><br /> Tento parametr odpovídá přepínači [/define](https://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) kompilátoru vbc.exe.|  
|`DelaySign`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` se úloha umístí do sestavení veřejný klíč. `false`V případě, úloha plně podepíše sestavení. Výchozí hodnota je `false` . Tento parametr nemá žádný vliv, pokud se nepoužívá s `KeyFile` parametrem nebo `KeyContainer` parametrem. Tento parametr odpovídá přepínači [/delaysign](https://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) kompilátoru vbc.exe.|  
|`DisabledWarnings`|Volitelný `String` parametr.<br /><br /> Potlačí zadaná upozornění. Stačí zadat jenom číselnou část identifikátoru upozornění. Několik upozornění je odděleno středníky. Tento parametr odpovídá přepínači [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) kompilátoru vbc.exe.|  
|`DocumentationFile`|Volitelný `String` parametr.<br /><br /> Zpracuje komentáře dokumentace do zadaného souboru XML. Tento parametr Přepisuje `GenerateDocumentation` atribut. Další informace najdete v tématu [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` úloha vygeneruje informace o ladění a umístí je do souboru. pdb. Další informace najdete v tématu [/Debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|Volitelný `String` parametr.<br /><br /> Určuje, jak by měl úkol hlásit vnitřní chyby kompilátoru. Tento parametr může mít následující hodnoty:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Pokud `prompt` je zadána a dojde k vnitřní chybě kompilátoru, uživateli se zobrazí výzva s možností wheter k odeslání dat chyby společnosti Microsoft.<br /><br /> Pokud `send` je zadána a dojde k vnitřní chybě kompilátoru, úloha odešle údaje o chybě společnosti Microsoft.<br /><br /> Výchozí hodnota je `none` , což hlásí pouze chyby ve výstupu textu.<br /><br /> Tento parametr odpovídá přepínači [/errorreport](https://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) vbc.exe kompilátoru.|  
|`FileAlignment`|Volitelný `Int32` parametr.<br /><br /> Určuje, kam se v bajtech mají zarovnat oddíly výstupního souboru. Tento parametr může mít následující hodnoty:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Tento parametr odpovídá přepínači [/filealign](https://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) kompilátoru vbc.exe.|  
|`GenerateDocumentation`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , vygeneruje informace o dokumentaci a umístí je do souboru XML s názvem spustitelného souboru nebo knihovny, kterou vytváří úkol. Další informace najdete v tématu [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Importuje obory názvů z určených kolekcí položek. Tento parametr odpovídá přepínači [/Imports](https://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) kompilátoru vbc.exe.|  
|`KeyContainer`|Volitelný `String` parametr.<br /><br /> Určuje název kontejneru kryptografických klíčů. Tento parametr se corresonds na přepínač [/keycontainer](https://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) kompilátoru vbc.exe.|  
|`KeyFile`|Volitelný `String` parametr.<br /><br /> Určuje název souboru, který obsahuje kryptografický klíč. Další informace najdete v tématu [/keyfile](https://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|Volitelné [řetězec] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->ukazatele.<br /><br /> Určuje jazykovou verzi, buď "9" nebo "10".|  
|`LinkResources`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru; zdrojový soubor není umístěný do výstupního souboru. Tento parametr odpovídá přepínači [/linkresource](https://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) kompilátoru vbc.exe.|  
|`MainEntryPoint`|Volitelný `String` parametr.<br /><br /> Určuje třídu nebo modul, který obsahuje `Sub Main` proceduru. Tento parametr se corresonds na přepínač [/Main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) kompilátoru vbc.exe.|  
|`ModuleAssemblyName`|Volitelný `String` parametr.<br /><br /> Určuje sestavení, jehož součástí je tento modul.|  
|`NoConfig`|Volitelný `Boolean` parametr.<br /><br /> Určuje, že by kompilátor neměl používat soubor Vbc. rsp. Tento parametr odpovídá parametru [/noconfig](https://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) kompilátoru vbc.exe.|  
|`NoLogo`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` se potlačí zobrazení informací o banneru kompilátoru. Tento parametr odpovídá přepínači [/nologo](https://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) vbc.exe kompilátoru.|  
|`NoStandardLib`|Volitelný `Boolean` parametr.<br /><br /> Způsobí, že kompilátor neodkazuje na standardní knihovny. Tento parametr odpovídá přepínači [/nostdlib](https://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) kompilátoru vbc.exe.|  
|`NoVBRuntimeReference`|Volitelný `Boolean` parametr.<br /><br /> Pouze interní použití. Je-li nastavena hodnota true, zakáže automatické odkaz Microsoft.VisualBasic.dll..|  
|`NoWarnings`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je úloha potlačuje všechna upozornění. Další informace najdete v tématu [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` povolíte optimalizace kompilátoru. Tento parametr odpovídá přepínači [/optimize](https://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) kompilátoru vbc.exe.|  
|`OptionCompare`|Volitelný `String` parametr.<br /><br /> Určuje, jak se provádí porovnávání řetězců. Tento parametr může mít následující hodnoty:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Hodnota `binary` Určuje, že úloha používá porovnávání binárních řetězců. Hodnota `text` Určuje, že úloha používá porovnávání textových řetězců. Výchozí hodnota tohoto parametru je `binary` . Tento parametr odpovídá přepínači [/OptionCompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) kompilátoru vbc.exe.|  
|`OptionExplicit`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je požadována explicitní deklarace proměnných. Tento parametr odpovídá přepínači [/OptionExplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) kompilátoru vbc.exe.|  
|`OptionInfer`|Volitelný `Boolean` parametr.<br /><br /> `true`V případě, umožňuje odvozování typů proměnných.|  
|`OptionStrict`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je úloha vynutila striktní sémantiku typu pro omezení implicitních převodů typu. Tento parametr odpovídá přepínači [/OptionStrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) kompilátoru vbc.exe.|  
|`OptionStrictType`|Volitelný `String` parametr.<br /><br /> Určuje, která sémantika striktního typu vygeneruje upozornění. V současné době je podporována pouze možnost vlastní. Tento parametr odpovídá přepínači [/OptionStrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) kompilátoru vbc.exe.|  
|`OutputAssembly`|Volitelný `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Tento parametr odpovídá přepínači [/out](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) vbc.exe kompilátoru.|  
|`Platform`|Volitelný `String` parametr.<br /><br /> Určuje platformu procesoru, na kterou má výstupní soubor cílit. Tento parametr může mít hodnotu `x86` , `x64` , `Itanium` nebo `anycpu` . Výchozí je `anycpu`. Tento parametr odpovídá přepínači [/Platform](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) kompilátoru vbc.exe.|  
|`References`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Způsobí, že úloha importuje informace o veřejném typu ze zadaných položek do aktuálního projektu. Tento parametr odpovídá přepínači [/reference](https://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) vbc.exe kompilátoru.|  
|`RemoveIntegerChecks`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , zakáže kontroly chyb přetečení celých čísel. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači [/removeintchecks](https://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) kompilátoru vbc.exe.|  
|`Resources`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vloží prostředek .NET Framework do výstupního souboru. Tento parametr odpovídá přepínači [/Resource](https://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) kompilátoru vbc.exe.|  
|`ResponseFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje soubor odpovědí obsahující příkazy pro tento úkol. Tento parametr odpovídá možnosti [@ (určení souboru odezvy)](https://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) kompilátoru vbc.exe.|  
|`RootNamespace`|Volitelný `String` parametr.<br /><br /> Určuje kořenový obor názvů pro všechny deklarace typů. Tento parametr odpovídá přepínači [/RootNamespace](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) kompilátoru vbc.exe.|  
|`SdkPath`|Volitelný `String` parametr.<br /><br /> Určuje umístění mscorlib.dll a microsoft.visualbasic.dll. Tento parametr odpovídá přepínači [přepínač/SdkPath](https://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) kompilátoru vbc.exe.|  
|`Sources`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje jeden nebo více [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] zdrojových souborů.|  
|`TargetCompactFramework`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true` úloha cílena na [!INCLUDE[Compact](../includes/compact-md.md)] . Tento přepínač odpovídá přepínači [/netcf](https://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) kompilátoru vbc.exe.|  
|`TargetType`|Volitelný `String` parametr.<br /><br /> Určuje formát výstupního souboru. Tento parametr může mít hodnotu `library` , která vytvoří knihovnu kódu, `exe` , která vytvoří konzolovou aplikaci, `module` , která vytvoří modul, nebo `winexe` , který vytvoří program systému Windows. Výchozí je `library`. Tento parametr odpovídá přepínači [/target](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) kompilátoru vbc.exe.|  
|`Timeout`|Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue` , což značí, že není k dispozici žádný časový interval.|  
|`ToolPath`|Volitelný `String` parametr.<br /><br /> Určuje umístění, ze kterého bude úloha načítat základní spustitelný soubor (vbc.exe). Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK odpovídající verzi rozhraní, na které běží [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|`TreatWarningsAsErrors`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` jsou všechna upozornění považována za chyby. Další informace najdete v tématu [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|Volitelný `Boolean` parametr.<br /><br /> Dá pokyn k tomu, aby úkol použil objekt vnitroprocesového kompilátoru, pokud je k dispozici. Používáno pouze nástrojem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|`Utf8Output`|Volitelný `Boolean` parametr.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr odpovídá přepínači [/utf8output](https://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) kompilátoru vbc.exe.|  
|`Verbosity`|Volitelný `String` parametr.<br /><br /> Určuje podrobnost výstupu kompilátoru. Podrobnosti mohou být `Quiet` , `Normal` (výchozí), nebo `Verbose` .|  
|`WarningsAsErrors`|Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která mají být považována za chyby. Další informace najdete v tématu [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Tento parametr Přepisuje `TreatWarningsAsErrors` parametr.|  
|`WarningsNotAsErrors`|Volitelný `String` parametr.<br /><br /> Určuje seznam upozornění, která nejsou považována za chyby. Další informace najdete v tématu [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Tento parametr je užitečný pouze v případě, že `TreatWarningsAsErrors` je parametr nastaven na hodnotu `true` .|  
|`Win32Icon`|Volitelný `String` parametr.<br /><br /> Vloží soubor. ico do sestavení, které poskytne výstupnímu souboru požadovaný vzhled v Průzkumníkovi souborů. Tento parametr odpovídá přepínači [/win32icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) kompilátoru vbc.exe.|  
|`Win32Resources`|Volitelný `String` parametr.<br /><br /> Vloží soubor prostředků Win32 (. res) do výstupního souboru. Tento parametr odpovídá přepínači [/Win32Resource.](https://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) kompilátoru vbc.exe.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekt.  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Kompilátor příkazového řádku](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
