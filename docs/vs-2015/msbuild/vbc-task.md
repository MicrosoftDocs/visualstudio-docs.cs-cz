---
title: Vbc – úloha | Dokumentace Microsoftu
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
manager: ghogen
ms.openlocfilehash: 4ed9563f4149b550e123cf74a09f19245514fe97
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281859"
---
# <a name="vbc-task"></a>Vbc – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zabalí vbc.exe, která vytváří spustitelné soubory (.exe), dynamické knihovny (DLL) nebo moduly kódu (.netmodule). Další informace o vbc.exe, naleznete v tématu [příkazového řádku kompilátoru jazyka Visual Basic](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Vbc` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Volitelné `String[]` parametru.<br /><br /> Určuje další složky, ve kterých se mají hledat sestavení zadaná v atributu odkazy.|  
|`AddModules`|Volitelné `String[]` parametru.<br /><br /> Způsobí, že kompilátor, aby všechny informace ze zadané soubory, které jsou k dispozici do projektu je aktuálně kompilován typu. Tento parametr [/addmodule](http://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) přepínače kompilátoru vbc.exe.|  
|`BaseAddress`|Volitelné `String` parametru.<br /><br /> Určuje základní adresu knihovny DLL. Tento parametr [/BaseAddress](http://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) přepínače kompilátoru vbc.exe.|  
|`CodePage`|Volitelné `Int32` parametru.<br /><br /> Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace. Tento parametr [/CODEPAGE](http://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) přepínače kompilátoru vbc.exe.|  
|`DebugType`|Volitelné `String[]` parametru.<br /><br /> Způsobí, že kompilátor generovat ladicí informace. Tento parametr může mít následující hodnoty:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Výchozí hodnota je `full`, což umožňuje připojení ladicího programu ke spuštěnému programu. Hodnota `pdbonly` umožňuje ladění kódu zdroj, když program je spuštěn v ladicím programu, ale jenom v případě, že je spuštěný program je připojen k ladicímu programu se zobrazí kód jazyka sestavení. Další informace najdete v tématu [/Debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|Volitelné `String[]` parametru.<br /><br /> Definuje podmíněné konstanty kompilátoru. Dvojice symbol/hodnota jsou odděleny středníkem a jsou zadány pomocí následující syntaxe:<br /><br /> *symbol1* `=` *hodnota1* `;` *symbol2* `=` *hodnota2*<br /><br /> Tento parametr [/ define](http://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) přepínače kompilátoru vbc.exe.|  
|`DelaySign`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha umístí veřejný klíč v sestavení. Pokud `false`, úloha plně podepíše sestavení. Výchozí hodnota je `false`. Tento parametr nemá žádný vliv, pokud nejsou použity s `KeyFile` parametr nebo `KeyContainer` parametru. Tento parametr [/delaysign](http://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) přepínače kompilátoru vbc.exe.|  
|`DisabledWarnings`|Volitelné `String` parametru.<br /><br /> Potlačí zadaná upozornění. Stačí zadat číselnou část identifikátoru upozornění. Více varování je odděleno středníky. Tento parametr [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) přepínače kompilátoru vbc.exe.|  
|`DocumentationFile`|Volitelné `String` parametru.<br /><br /> Zpracuje komentáře dokumentace do zadaného souboru XML. Přepíše tento parametr `GenerateDocumentation` atribut. Další informace najdete v tématu [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha generuje ladicí informace a umístí jej do souboru pdb. Další informace najdete v tématu [/Debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|Volitelné `String` parametru.<br /><br /> Určuje, jak by měl úkol ohlásit interní chyby kompilátoru. Tento parametr může mít následující hodnoty:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Pokud `prompt` určena a dojde k chybě vnitřní kompilátor, uživatel je vyzván, existuje možnost němuž údaje o chybám poslat Microsoftu.<br /><br /> Pokud `send` určena a dojde k chybě vnitřní kompilátor, úloha odesílá data chyby společnosti Microsoft.<br /><br /> Výchozí hodnota je `none`, která hlásí chyby v textu pouze výstup.<br /><br /> Tento parametr [/errorreport](http://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) přepínače kompilátoru vbc.exe.|  
|`FileAlignment`|Volitelné `Int32` parametru.<br /><br /> Určuje, v bajtech, kam chcete zarovnat oddíly výstupního souboru. Tento parametr může mít následující hodnoty:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Tento parametr [/filealign](http://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) přepínače kompilátoru vbc.exe.|  
|`GenerateDocumentation`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, generuje informace o dokumentaci a umístí jej do souboru XML s názvem spustitelného souboru nebo knihovny, která vytváří úlohy. Další informace najdete v tématu [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Obory názvů se importuje z zadanou položku kolekce. Tento parametr [/importuje](http://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) přepínače kompilátoru vbc.exe.|  
|`KeyContainer`|Volitelné `String` parametru.<br /><br /> Určuje název kontejneru kryptografických klíčů. Tento parametr corresonds k [/keycontainer](http://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) přepínače kompilátoru vbc.exe.|  
|`KeyFile`|Volitelné `String` parametru.<br /><br /> Určuje název souboru obsahujícího kryptografický klíč. Další informace najdete v tématu [/keyfile](http://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|Volitelné [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametru.<br /><br /> Určuje jazykovou verzi, "9" nebo "10".|  
|`LinkResources`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Vytvoří odkaz na prostředek rozhraní .NET Framework do výstupního souboru; soubor prostředků není umístěn do výstupního souboru. Tento parametr [/linkresource](http://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) přepínače kompilátoru vbc.exe.|  
|`MainEntryPoint`|Volitelné `String` parametru.<br /><br /> Určuje třídu nebo modul, který obsahuje `Sub Main` postup. Tento parametr corresonds k [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) přepínače kompilátoru vbc.exe.|  
|`ModuleAssemblyName`|Volitelné `String` parametru.<br /><br /> Určuje sestavení, které tento modul je součástí.|  
|`NoConfig`|Volitelné `Boolean` parametru.<br /><br /> Určuje, zda kompilátor by neměl používat soubor vbc.rsp. Tento parametr [/noconfig](http://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) parametr kompilátoru vbc.exe.|  
|`NoLogo`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, potlačí zobrazení informací nápisu kompilátoru. Tento parametr [/nologo](http://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) přepínače kompilátoru vbc.exe.|  
|`NoStandardLib`|Volitelné `Boolean` parametru.<br /><br /> Způsobí, že kompilátor nelze odkazovat na standardní knihovny. Tento parametr [/nostdlib](http://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) přepínače kompilátoru vbc.exe.|  
|`NoVBRuntimeReference`|Volitelné `Boolean` parametru.<br /><br /> Pouze pro interní použití. Při hodnotě true se brání automatické odkaz na knihovny Microsoft.VisualBasic.dll...|  
|`NoWarnings`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha potlačí všechna upozornění. Další informace najdete v tématu [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, povolí optimalizace kompilátoru. Tento parametr [/ optimize](http://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) přepínače kompilátoru vbc.exe.|  
|`OptionCompare`|Volitelné `String` parametru.<br /><br /> Určuje způsob porovnávání řetězců. Tento parametr může mít následující hodnoty:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Hodnota `binary` Určuje, že úkol používá binární porovnání řetězců. Hodnota `text` Určuje, že úkol používá textové porovnávání řetězců. Výchozí hodnota tohoto parametru je `binary`. Tento parametr [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) přepínače kompilátoru vbc.exe.|  
|`OptionExplicit`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, se vyžaduje explicitní deklaraci proměnných. Tento parametr [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) přepínače kompilátoru vbc.exe.|  
|`OptionInfer`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, povolí odvozování typů proměnných.|  
|`OptionStrict`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha vynutí sémantiku přísného typu pro omezení převodů implicitních typů. Tento parametr [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) přepínače kompilátoru vbc.exe.|  
|`OptionStrictType`|Volitelné `String` parametru.<br /><br /> Určuje, které sémantiku přísného typu generovat upozornění. V současné době se podporuje jenom "vlastní". Tento parametr [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) přepínače kompilátoru vbc.exe.|  
|`OutputAssembly`|Volitelné `String` výstupní parametr.<br /><br /> Určuje název výstupního souboru. Tento parametr [/out](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) přepínače kompilátoru vbc.exe.|  
|`Platform`|Volitelné `String` parametru.<br /><br /> Určuje platformu procesor, který bude cílen výstupním souborem. Tento parametr může mít hodnotu `x86`, `x64`, `Itanium`, nebo `anycpu`. Výchozí hodnota je `anycpu`. Tento parametr [/Platform](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) přepínače kompilátoru vbc.exe.|  
|`References`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Způsobí, že úloha pro import informací o veřejný typ ze zadaných položek do aktuálního projektu. Tento parametr [/reference](http://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) přepínače kompilátoru vbc.exe.|  
|`RemoveIntegerChecks`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zakáže chyby kontroly přetečení celých čísel. Výchozí hodnota je `false`. Tento parametr [/removeintchecks](http://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) přepínače kompilátoru vbc.exe.|  
|`Resources`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Vloží prostředek rozhraní .NET Framework do výstupního souboru. Tento parametr [/Resource](http://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) přepínače kompilátoru vbc.exe.|  
|`ResponseFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje soubor odpovědí, který obsahuje příkazy pro tuto úlohu. Tento parametr [@ (určení souboru odezvy)](http://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) – možnost kompilátoru vbc.exe.|  
|`RootNamespace`|Volitelné `String` parametru.<br /><br /> Určuje kořenový obor názvů pro všechny deklarace typů. Tento parametr [/RootNamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) přepínače kompilátoru vbc.exe.|  
|`SdkPath`|Volitelné `String` parametru.<br /><br /> Určuje umístění knihovny mscorlib.dll a microsoft.visualbasic.dll. Tento parametr [/sdkpath](http://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) přepínače kompilátoru vbc.exe.|  
|`Sources`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje jeden nebo více [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] zdrojové soubory.|  
|`TargetCompactFramework`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, cíle úlohy [!INCLUDE[Compact](../includes/compact-md.md)]. Tento přepínač odpovídá [/netcf](http://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) přepínače kompilátoru vbc.exe.|  
|`TargetType`|Volitelné `String` parametru.<br /><br /> Určuje formát výstupního souboru. Tento parametr může mít hodnotu `library`, která vytvoří knihovnu kódu `exe`, vytváří aplikace konzoly `module`, která vytvoří modul, nebo `winexe`, vytváří Windows program. Výchozí hodnota je `library`. Tento parametr [/target](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) přepínače kompilátoru vbc.exe.|  
|`Timeout`|Volitelné `Int32` parametru.<br /><br /> Určuje množství času, v milisekundách, po jejichž uplynutí je spustitelný soubor s úkolem ukončen. Výchozí hodnota je `Int.MaxValue`, která udává, že neexistuje žádný časový limit.|  
|`ToolPath`|Volitelné `String` parametru.<br /><br /> Určuje umístění, kde bude úloha načtení základní spustitelného souboru (vbc.exe). Pokud není tento parametr zadán, použije úloha instalační cestu sady SDK odpovídající verzi rozhraní framework, na kterém běží [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`TreatWarningsAsErrors`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, všechna upozornění jsou považována za chyby. Další informace najdete v tématu [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|Volitelné `Boolean` parametru.<br /><br /> Úkol použije objekt vnitroprocesového kompilátoru přikáže, pokud je k dispozici. Používání pouze systémem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Volitelné `Boolean` parametru.<br /><br /> Protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr [/utf8output](http://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) přepínače kompilátoru vbc.exe.|  
|`Verbosity`|Volitelné `String` parametru.<br /><br /> Určuje podrobnost výstupu kompilátoru. Úroveň podrobností může být `Quiet`, `Normal` (výchozí), nebo `Verbose`.|  
|`WarningsAsErrors`|Volitelné `String` parametru.<br /><br /> Označí seznam upozornění pro nakládání s chybami. Další informace najdete v tématu [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Přepíše tento parametr `TreatWarningsAsErrors` parametru.|  
|`WarningsNotAsErrors`|Volitelné `String` parametru.<br /><br /> Označí seznam upozornění, která nemají být považována za chyby. Další informace najdete v tématu [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Tento parametr je užitečná pouze pokud `TreatWarningsAsErrors` parametr je nastaven na `true`.|  
|`Win32Icon`|Volitelné `String` parametru.<br /><br /> Vloží soubor .ico do sestavení, které dává výstupnímu souboru požadovaný vzhled v Průzkumníku souborů. Tento parametr [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) přepínače kompilátoru vbc.exe.|  
|`Win32Resources`|Volitelné `String` parametru.<br /><br /> Do výstupního souboru vloží soubor prostředků (.res) Win32. Tento parametr [/win32resource](http://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) přepínače kompilátoru vbc.exe.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad se zkompiluje [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektu.  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



