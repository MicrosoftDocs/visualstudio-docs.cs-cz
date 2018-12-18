---
title: Propojení úkolů | Dokumentace Microsoftu
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
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2ca9c721567d89bddad4a9ee61639bd3a82f10d
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143447"
---
# <a name="link-task"></a>Úloha odkazu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zabalí nástroj linker Visual C++, link.exe. Nástroj linker k propojení objektových souborů Common Object File Format (COFF) a knihovny, které chcete vytvořit spustitelný soubor (.exe) nebo dynamická knihovna (DLL). Další informace najdete v tématu [možnosti Linkeru](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry **odkaz** úloh. Většinu úkolů parametrů a několik sad parametrů, odpovídají možnost příkazového řádku.  
  
- **AdditionalDependencies**  
  
   Volitelné **String []** parametru.  
  
   Určuje seznam vstupních souborů přidejte do příkazu.  
  
   Další informace najdete v tématu [vstupní soubory LINK](http://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
- **AdditionalLibraryDirectories**  
  
   Volitelné **String []** parametru.  
  
   Přepíše cestu ke knihovně prostředí. Zadejte název adresáře.  
  
   Další informace najdete v tématu [/Libpath (další proměnná Libpath)](http://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
- **AdditionalManifestDependencies**  
  
   Volitelné **String []** parametru.  
  
   Určuje atributy, které budou umístěny do `dependency` části souboru manifestu.  
  
   Další informace najdete v tématu [/MANIFESTDEPENDENCY (určení závislostí manifestu)](http://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Také, naleznete v tématu "Konfiguračních souborů vydavatele" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.  
  
- **AdditionalOptions**  
  
   Volitelné **řetězec** parametru.  
  
   Seznam možností linkeru uvedená na příkazovém řádku. Například **"**_/option1 /option2 /option#_". Tento parametr použijte k určení možnosti linkeru, které nejsou reprezentovány jakýkoli jiný **odkaz** parametr úlohy.  
  
   Další informace najdete v tématu [možnosti Linkeru](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
- **AddModuleNamesToAssembly**  
  
   Volitelné **String []** parametru.  
  
   Přidá odkaz modulu na sestavení.  
  
   Další informace najdete v tématu [/ASSEMBLYMODULE (Přidání modulu MSIL do sestavení)](http://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
- **AllowIsolation**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, způsobí, že operační systém do manifestu vyhledávání a načte. Pokud `false`, označuje, zda jsou načteny knihovny DLL, jako kdyby byl žádný manifest.  
  
   Další informace najdete v tématu [/ALLOWISOLATION (vyhledání manifestu)](http://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
- **AssemblyDebug**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, generuje **DebuggableAttribute** atribut spolu s ladicí informace o sledování a zakazuje optimalizace JIT. Pokud `false`, generuje **DebuggableAttribute** atribut ale zakáže sledování informací o ladění a povolí optimalizace JIT.  
  
   Další informace najdete v tématu [/assemblydebug (přidání atributu DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
- **AssemblyLinkResource**  
  
   Volitelné **String []** parametru.  
  
   Vytvoří odkaz na prostředek rozhraní .NET Framework do výstupního souboru; soubor prostředků není umístěn do výstupního souboru. Zadejte název prostředku.  
  
   Další informace najdete v tématu [/ASSEMBLYLINKRESOURCE (odkaz na prostředek rozhraní .NET Framework)](http://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
- **AttributeFileTracking**  
  
   Implicitní **logická** parametru.  
  
   Povolí podrobnější souborů sledování k zachycení odkazu přírůstkové od chování. Vždy vrátí `true`.  
  
- **Vlastnost BaseAddress**  
  
   Volitelné **řetězec** parametru.  
  
   Nastaví základní adresu pro program nebo knihovnu DLL při sestavování. Zadejte `{address[,size] | @filename,key}`.  
  
   Další informace najdete v tématu [propojovacího (základní adresa)](http://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
- **BuildingInIDE**  
  
   Volitelné **logická** parametru.  
  
   Hodnota true určuje to, že nástroj MSBuild je vyvolána z rozhraní IDE. V opačném případě označuje, zda nástroj MSBuild je vyvolána z příkazového řádku.  
  
   Tento parametr nemá žádný ekvivalent linkeru.  
  
- **CLRImageType**  
  
   Volitelné **řetězec** parametru.  
  
   Nastaví typ bitovou kopii common language runtime (CLR).  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možností propojovacího programu.  
  
  - **Výchozí** - *\<žádné >*  
  
  - **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
  - **ForcePureILImage** -   **/CLRIMAGETYPE: PURE**  
  
  - **ForceSafeILImage** - **Safe**  
  
    Další informace najdete v tématu [/CLRIMAGETYPE (zadat typ z bitové kopie modulu CLR)](http://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
- **CLRSupportLastError**  
  
   Volitelné **řetězec** parametru.  
  
   Zachová poslední kód chyby funkcí volaných mechanismem P/Invoke.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možností propojovacího programu.  
  
  - **Povolené** - **/CLRSupportLastError**  
  
  - **Zakázané** - **/CLRSupportLastError:NO**  
  
  - **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
    Další informace najdete v tématu [/CLRSUPPORTLASTERROR (zachování kódu poslední chyby pro volání PInvoke)](http://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
- **CLRThreadAttribute**  
  
   Volitelné **řetězec** parametru.  
  
   Explicitně určuje atribut dělení na vlákna pro vstupní bod programu CLR.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možností propojovacího programu.  
  
  - **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE: žádné**  
  
  - **MTAThreadingAttribute** - **: MTA**  
  
  - **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
    Další informace najdete v tématu [/CLRTHREADATTRIBUTE (nastavit atribut modulu CLR vlákno)](http://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
- **CLRUnmanagedCodeCheck**  
  
   Volitelné **logická** parametru.  
  
   Určuje, zda linker použije **SuppressUnmanagedCodeSecurityAttribute** linkerem generovaná volání nespravovaného volání ze spravovaného kódu do nativních knihoven DLL.  
  
   Další informace najdete v tématu [/CLRUNMANAGEDCODECHECK (přidat atribut SuppressUnmanagedCodeSecurityAttribute)](http://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
- **CreateHotPatchableImage**  
  
   Volitelné **řetězec** parametru.  
  
   Připravuje obrázek na horké záplatování.  
  
   Zadejte jednu z následujících hodnot, které odpovídá možností propojovacího programu.  
  
  - **Povolené** - **/FUNCTIONPADMIN**  
  
  - **X86Image** - **/FUNCTIONPADMIN:5**  
  
  - **X64Image** - **/FUNCTIONPADMIN:6**  
  
  - **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
    Další informace najdete v tématu [/FUNCTIONPADMIN (vytvoření Image vyměnitelné za provozu)](http://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
- **DataExecutionPrevention**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, označuje, že spustitelný soubor byl testován jako kompatibilní s funkcí Zabránění spuštění dat Windows.  
  
   Další informace najdete v tématu [/NXCOMPAT (kompatibilní s předcházením spuštění dat)](http://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
- **DelayLoadDLLs**  
  
   Volitelné **String []** parametru.  
  
   Způsobí, že tento parametr *s odloženým načtením* knihoven DLL. Zadejte název knihovny DLL pro odložené načtení.  
  
   Další informace najdete v tématu [/delayload (Import odloženého načtení)](http://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
- **DelaySign**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, částečně podepíše sestavení. Výchozí hodnota je `false`.  
  
   Další informace najdete v tématu [/delaysign (částečně podepsání sestavení)](http://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
- **Ovladač**  
  
   Volitelné **řetězec** parametru.  
  
   Zadejte tento parametr k vytvoření ovladač režimu jádra Windows NT.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možností propojovacího programu.  
  
  - **NotSet** - *\<none>*  
  
  - **Ovladač** - **Driver/Driver**  
  
  - **UpOnly** - **/DRIVER:UPONLY**  
  
  - **WDM** - **/DRIVER:WDM**  
  
    Další informace najdete v tématu [Driver/Driver (ovladač režimu jádra Windows NT)](http://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
- **EmbedManagedResourceFile**  
  
   Volitelné **String []** parametru.  
  
   Vloží soubor prostředků v sestavení. Zadejte název souboru požadovaný prostředek. Volitelně zadejte logický název, který slouží k načtení prostředku, a **PRIVÁTNÍ** možnost, která označuje v manifestu sestavení, že soubor prostředků je privátní.  
  
   Další informace najdete v tématu [narozdíl od (vložení spravovaného prostředku)](http://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
- **EnableCOMDATFolding**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, povoluje skládání identických sekvencí COMDAT.  
  
   Další informace najdete v tématu `ICF[= iterations]` argument [/OPT (optimalizace)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **EnableUAC**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, určuje, že informace o řízení uživatelských účtů (UAC) je vloženy do manifestu.  
  
   Další informace najdete v tématu [/MANIFESTUAC (vložené informace UAC v manifestu)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **EntryPointSymbol**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje funkci vstupního bodu jako počáteční adresu souboru .exe nebo knihovny DLL. Zadejte název funkce jako hodnotu parametru.  
  
   Další informace najdete v tématu [/Entry (Symbol vstupního bodu)](http://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
- **FixedBaseAddress**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, vytvoří program nebo knihovnu DLL, který lze načíst pouze na jeho upřednostňované základní adrese.  
  
   Další informace najdete v tématu [/fixed (pevná základní adresa)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
- **ForceFileOutput**  
  
   Volitelné **řetězec** parametru.  
  
   Říká linkeru, aby vytvořil soubor platný .exe nebo knihovny DLL i v případě, že symbol se odkazuje ale není definované nebo je vynásobit definované.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Povolené** -   **/FORCE**  
  
  - **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
  - **UndefinedSymbolOnly** -   **/FORCE: NEROZPOZNANÝ**  
  
    Další informace najdete v tématu [/Force (vynucení výstupu souboru)](http://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
- **ForceSymbolReferences**  
  
   Volitelné **String []** parametru.  
  
   Tento parametr přikazuje linkeru, aby přidal zadaný symbol do tabulky symbolů.  
  
   Další informace najdete v tématu [parametr/include (vynucení odkazů na symboly)](http://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
- **FunctionOrder**  
  
   Volitelné **řetězec** parametru.  
  
   Tento parametr optimalizuje program tak, že zadaný zabalených funkcí (sekvence Comdat) do bitové kopie v předurčeném pořadí.  
  
   Další informace najdete v tématu [/Order (Put funkcí v pořadí)](http://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
- **GenerateDebugInformation**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, vytvoří ladicí informace pro soubor .exe nebo knihovny DLL.  
  
   Další informace najdete v tématu [/Debug (Generovat ladicí informace)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
- **GenerateManifest**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, vytvoří soubor manifestu vedle sebe.  
  
   Další informace najdete v tématu [volbu/manifest (vytvoření Side-by-Side manifestu sestavení)](http://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
- **GenerateMapFile**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, vytvoří *souboru s mapováním*. Přípona názvu souboru souboru s mapováním je .map.  
  
   Další informace najdete v tématu [parametr/map (generování souboru mapování)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
- **HeapCommitSize**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje množství fyzické paměti v haldě přidělit najednou.  
  
   Další informace najdete v tématu `commit` argument v [/HEAP (nastavení velikosti haldy)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Další informace naleznete **HeapReserveSize** parametru.  
  
- **HeapReserveSize**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje celkový počet haldy ve virtuální paměti.  
  
   Další informace najdete v tématu `reserve` argument v [/HEAP (nastavení velikosti haldy)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Další informace naleznete **HeapCommitSize** parametr v této tabulce.  
  
- **IgnoreAllDefaultLibraries**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, říká linkeru, aby odebral jednu nebo více výchozích knihoven ze seznamu knihoven prohledává při překladu externích odkazů.  
  
   Další informace najdete v tématu [: / NODEFAULTLIB (ignorování knihoven)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **IgnoreEmbeddedIDL**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, určuje, že atributy IDL ve zdrojovém kódu nemají být zpracovány do souboru IDL.  
  
   Další informace najdete v tématu [/IGNOREIDL (není procesu atributy do MIDL)](http://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
- **IgnoreImportLibrary**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, určuje, že knihovna importů generovaná touto konfigurací by neměla být importována do závislých projektů.  
  
   Tento parametr neodpovídá možností propojovacího programu.  
  
- **IgnoreSpecificDefaultLibraries**  
  
   Volitelné **String []** parametru.  
  
   Určuje jeden nebo více názvů výchozích knihoven k ignorování. Více knihoven oddělte středníkem.  
  
   Další informace najdete v tématu [: / NODEFAULTLIB (ignorování knihoven)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **ImageHasSafeExceptionHandlers**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, linker vytvoří bitovou kopii pouze v případě, že můžete také vytvořit tabulku na obrázku bezpečných obslužných rutin výjimek.  
  
   Další informace najdete v tématu [/SAFESEH (bitová kopie má bezpečné obslužné rutiny výjimek)](http://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
- **ImportLibrary**  
  
   Název knihovny importu zadané uživatelem, který nahrazuje výchozí název knihovny.  
  
   Další informace najdete v tématu [/IMPLIB (pojmenování knihovny importu)](http://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
- **KeyContainer**  
  
   Volitelné **řetězec** parametru.  
  
   Kontejner, který obsahuje klíč pro podepsané sestavení.  
  
   Další informace najdete v tématu [/keycontainer (určení kontejneru klíčů pro podpis sestavení)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Další informace naleznete **KeyFile** parametr v této tabulce.  
  
- **KeyFile**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje soubor, který obsahuje klíč pro podepsané sestavení.  
  
   Další informace najdete v tématu [/keyfile (zadat klíč nebo dvojici klíč k podepsání sestavení)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Další informace naleznete **KeyContainer** parametru.  
  
- **LargeAddressAware**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, že aplikace dokáže zpracovat adresy větší než 2 GB.  
  
   Další informace najdete v tématu [/LARGEADDRESSAWARE (zpracování velkých adres)](http://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
- **LinkDLL**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, sestavení a knihovny DLL jako hlavní výstupního souboru.  
  
   Další informace najdete v tématu [/DLL (sestavení knihovny DLL)](http://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
- **LinkErrorReporting**  
  
   Volitelné **řetězec** parametru.  
  
   Umožňuje poskytnout informace o kompilátoru vnitřní chybě (ICE) přímo společnosti Microsoft.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **NoErrorReport** -   **/errorreport: žádné**  
  
  - **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
  - **SendErrorReport** -   **/errorreport: Send**  
  
    Další informace najdete v tématu [/errorreport (sestava interními chybami Linkeru)](http://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
- **LinkIncremental**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, umožňuje přírůstkové propojení.  
  
   Další informace najdete v tématu [Parametr/incremental (Inkrementální odkaz)](http://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
- **LinkLibraryDependencies**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, určuje, že knihovny vytvořené jako výstupy závislostí projektu automaticky připojeny.  
  
   Tento parametr neodpovídá možností propojovacího programu.  
  
- **LinkStatus**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, určuje, zda linker zobrazit ukazatel průběhu, který ukazuje, jaké je procento odkazu je dokončena.  
  
   Další informace najdete v tématu `STATUS` argument [parametru/LTCG (generování kódu při propojování odkaz)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **LinkTimeCodeGeneration**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje možnosti pro optimalizace na základě profilu.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** - *\<žádné >*  
  
  - **UseLinkTimeCodeGeneration** - **/LTCG**  
  
  - **PGInstrument** - **/LTCG:PGInstrument**  
  
  - **PGOptimization** - **/LTCG:PGOptimize**  
  
  - **PGUpdate**  
  
     \- **/LTCG:PGUpdate**  
  
    Další informace najdete v tématu [parametru/LTCG (generování kódu při propojování odkaz)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **ManifestFile**  
  
   Volitelné **řetězec** parametru.  
  
   Mění název výchozího souboru manifestu pro zadaný název souboru.  
  
   Další informace najdete v tématu [manifestfile (pojmenování souboru manifestu)](http://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
- **MapExports**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, přikazuje linkeru začlenit exportované funkce v souboru mapy.  
  
   Další informace najdete v tématu `EXPORTS` argument [parametr/MapInfo (zahrnout informace do souboru mapování)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
- **MapFileName**  
  
   Volitelné **řetězec** parametru.  
  
   Výchozí název souboru mapy se změní na zadaný název souboru.  
  
- **MergedIDLBaseFileName**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název souboru a příponu souboru IDL.  
  
   Další informace najdete v tématu [/IDLOUT (název výstupních souborů MIDL)](http://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
- **MergeSections**  
  
   Volitelné **řetězec** parametru.  
  
   Kombinuje oddíly v obraze. Zadejte `from-section=to-section`.  
  
   Další informace najdete v tématu [/Merge (kombinovat oddílů)](http://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
- **MidlCommandFile**  
  
   Volitelné **řetězec** parametru.  
  
   Zadejte název souboru, který obsahuje parametry příkazového řádku MIDL.  
  
   Další informace najdete v tématu [/MIDL (určení možností příkazového řádku MIDL)](http://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
- **MinimumRequiredVersion**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje minimální požadovanou verzi subsystému. Argumenty jsou desetinná čísla v rozsahu 0 až 65535.  
  
- **ModuleDefinitionFile**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název [soubor definice modulu](http://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8).  
  
   Další informace najdete v tématu [def (zadat soubor definice modulu)](http://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
- **MSDOSStubFileName**  
  
   Volitelné **řetězec** parametru.  
  
   Připojí zadaný zástupný program MS-DOS k programu Win32.  
  
   Další informace najdete v tématu [/stub (název souboru zástupného kódu MS-DOS zástupné procedury)](http://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
- **NoEntryPoint**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, určuje knihovnu DLL pouze prostředků.  
  
   Další informace najdete v tématu [NOENTRY (bez vstupního bodu)](http://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
- **ObjectFiles**  
  
   Implicitní **String []** parametru.  
  
   Určuje soubory objektů, které jsou propojeny.  
  
- **OptimizeReferences**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, eliminuje funkce nebo data, která nejsou nikdy odkazována.  
  
   Další informace najdete v tématu `REF` argument v [/OPT (optimalizace)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **Výstupní soubor**  
  
   Volitelné **řetězec** parametru.  
  
   Přepíše výchozí název a umístění programu, který vytvoří linker.  
  
   Další informace najdete v tématu [/OUT (název výstupního souboru)](http://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
- **PerUserRedirection**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true` a je povolen výstup registru, vynutí registru zapisuje do **HKEY_CLASSES_ROOT** přesměrovat na **HKEY_CURRENT_USER**.  
  
- **PreprocessOutput**  
  
   Volitelné `ITaskItem[]` parametru.  
  
   Definuje pole objektů preprocesoru výstupní položky, které lze používat a, protože ho vygeneroval úlohy.  
  
- **PreventDllBinding**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, tak Bind.exe informaci, že by neměl být vázána propojený obrázek.  
  
   Další informace najdete v tématu [/ALLOWBIND (zabránit DLL vazby)](http://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
- **Profil**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, vytvoří výstupní soubor, který lze použít s **nástroje pro měření výkonu** profileru.  
  
   Další informace najdete v tématu [/Profile (Profiler nástrojů výkonu)](http://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
- **ProfileGuidedDatabase**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název souboru .pgd, který se použije k ukládání informací o spuštění programu  
  
   Další informace najdete v tématu [/PGD (určení databáze pro optimalizace Profile-Guided)](http://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
- **ProgramDatabaseFile**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název databáze programu (PDB), který vytvoří linker.  
  
   Další informace najdete v tématu [/pdb (použití databáze programu)](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
- **RandomizedBaseAddress**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, generuje spustitelnou bitovou kopii, která lze náhodně změnit základ v okamžiku načtení pomocí *náhodného generování rozložení prostoru adres* (technologie ASLR) funkce systému Windows.  
  
   Další informace najdete v tématu [možnost/DynamicBase (použití adres náhodného generování rozložení prostoru)](http://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
- **RegisterOutput**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, zaregistruje primární výstup tohoto sestavení.  
  
- **SectionAlignment**  
  
   Volitelné **celé číslo** parametru.  
  
   Určuje zarovnání jednotlivých oddílů uvnitř lineárního adresního prostoru programu. Hodnota tohoto parametru je jednotka počet bajtů a je mocninou čísla 2.  
  
   Další informace najdete v tématu [/align (zarovnání oddílů)](http://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
- **Setchecksum –**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, nastaví kontrolní součet v hlavičce souboru .exe.  
  
   Další informace najdete v tématu [/Release (nastavení kontrolního součtu)](http://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
- **ShowProgress**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje úroveň podrobností sestav průběhu pro operace propojení.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **NotSet** - *\<none>*  
  
  - **LinkVerbose** - **/VERBOSE**  
  
  - **LinkVerboseLib** - **/VERBOSE:Lib**  
  
  - **LinkVerboseICF** - **/VERBOSE:ICF**  
  
  - **LinkVerboseREF** - **/VERBOSE:REF**  
  
  - **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
  - **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
    Další informace najdete v tématu [verbose (Tisk zprávy o průběhu)](http://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
- **Zdroje**  
  
   Vyžaduje `ITaskItem[]` parametru.  
  
   Definuje pole objektů položky nástroje MSBuild zdrojových souborů, které lze používat a, protože ho vygeneroval úlohy.  
  
- **SpecifySectionAttributes**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje atributy oddílu. Tím se přepíše atributy, které byly nastavené při kompilaci souboru obj části.  
  
   Další informace najdete v tématu [/Section (určení atributů oddílu)](http://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
- **StackCommitSize**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje množství fyzické paměti v každém přidělení při další paměť je přidělena.  
  
   Další informace najdete v tématu `commit` argument [/Stack (přidělení zásobníku)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StackReserveSize**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje, celkovou velikost zásobníku přidělenou ve virtuální paměti.  
  
   Další informace najdete v tématu `reserve` argument [/Stack (přidělení zásobníku)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StripPrivateSymbols**  
  
   Volitelné **řetězec** parametru.  
  
   Vytvoří druhý soubor databáze (PDB) programu, která vynechává symboly, které nechcete k distribuci zákazníkům. Zadejte název druhý soubor PDB.  
  
   Další informace najdete v tématu [/PDBSTRIPPED (odstranění privátních symbolů)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
- **Subsystém**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje prostředí pro spustitelný soubor.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **NotSet** - *\<none>*  
  
  - **Konzola** -   **/Subsystem: Console**  
  
  - **Windows** -   **/Subsystem: Windows**  
  
  - **Nativní** - **souboru**  
  
  - **Aplikace EFI** - **/SUBSYSTEM:EFI_APPLICATION**  
  
  - **Ovladač spouštěcí služby EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
  - **PAMĚŤ ROM EFI** - **/SUBSYSTEM:EFI_ROM**  
  
  - **Modul Runtime EFI** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
  - **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
  - **POSIX** - **/SUBSYSTEM:POSIX**  
  
    Další informace najdete v tématu [/Subsystem (určení subsystému)](http://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, přikazuje linkeru, které nechcete zahrnout do finální bitové kopie s možností vazby tabulky importu adres (IAT).  
  
   Další informace najdete v tématu `NOBIND` argument [/delay (nastavení importu odloženého načtení)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, říká odloženě zaváděné pomocnou funkci, aby podporovala explicitní uvolnění knihovny DLL.  
  
   Další informace najdete v tématu `UNLOAD` argument [/delay (nastavení importu odloženého načtení)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SuppressStartupBanner**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.  
  
   Další informace najdete v tématu [/nologo (Potlačení úvodního nápisu) (Linker)](http://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
- **SwapRunFromCD**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, informuje operační systém nejprve zkopírovat linkeru výstupu do odkládacího souboru, a potom spusťte bitovou kopii z něj.  
  
   Další informace najdete v tématu `CD` argument [swaprun (Načtení výstupu Linkeru do odkládacího souboru)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Další informace naleznete **SwapRunFromNET** parametru.  
  
- **SwapRunFromNET**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, informuje operační systém nejprve zkopírovat linkeru výstupu do odkládacího souboru, a potom spusťte bitovou kopii z něj.  
  
   Další informace najdete v tématu `NET` argument [swaprun (Načtení výstupu Linkeru do odkládacího souboru)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Další informace naleznete **SwapRunFromCD** parametr v této tabulce.  
  
- **TargetMachine**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje cílovou platformu pro program nebo knihovnu DLL.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **NotSet** - *\<none>*  
  
  - **MachineARM** - **/MACHINE:ARM**  
  
  - **MachineEBC** - **/MACHINE:EBC**  
  
  - **MachineIA64** - **/MACHINE:IA64**  
  
  - **MachineMIPS** - **/MACHINE:MIPS**  
  
  - **MachineMIPS16** - **/MACHINE:MIPS16**  
  
  - **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
  - **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
  - **MachineSH4** - **/MACHINE:SH4**  
  
  - **MachineTHUMB** - **/MACHINE:THUMB**  
  
  - **MachineX64** - **/MACHINE:X 64**  
  
  - **MachineX86** - **/MACHINE:X 86**  
  
    Další informace najdete v tématu [/Machine (určení cílové platformy)](http://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
- **TerminalServerAware**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, nastaví příznak v poli IMAGE_OPTIONAL_HEADER dllcharacteristics v nepovinné hlavičce bitové kopie programu. Pokud je tento příznak nastaven, neprovede Terminálový Server určité změny aplikace.  
  
   Další informace najdete v tématu [parametr/TSAWARE (vytvoření Terminálový Server aplikace s)](http://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
- **TrackerLogDirectory**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje adresář protokolu sledovacího modulu.  
  
- **TreatLinkerWarningAsErrors**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, způsobí, že žádný výstupní soubor, který chcete vygenerovat, pokud linker vydá upozornění.  
  
   Další informace najdete v tématu [/WX (zpracovávat upozornění Linkeru jako chyb)](http://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
- **TurnOffAssemblyGeneration**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, vytvoří bitovou kopii pro aktuální výstupní soubor bez sestavení rozhraní .NET Framework.  
  
   Další informace najdete v tématu [parametr/noassembly (vytvoření modulu MSIL)](http://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
- **TypeLibraryFile**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje název souboru a příponu souboru tlb. Zadejte název souboru nebo název a cesta k souboru.  
  
   Další informace najdete v tématu [/TLBOUT (název. Soubor vyrovnávací paměti TLB)](http://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
- **TypeLibraryResourceID**  
  
   Volitelné **celé číslo** parametru.  
  
   Určuje hodnotu zadané uživatelem pro knihovnu typů vytvoří linker. Zadejte hodnotu od 1 do 65535.  
  
   Další informace najdete v tématu [/TLBID (určení ID prostředku pro knihovnu typů)](http://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
- **UACExecutionLevel**  
  
   Volitelné **řetězec** parametru.  
  
   Určuje požadovanou úroveň spuštění aplikace při spuštění v části s řízením uživatelských účtů.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
  - **AsInvoker** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **RequireAdministrator** - `level='requireAdministrator'`  
  
    Další informace najdete v tématu `level` argument [/MANIFESTUAC (vložené informace UAC v manifestu)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UACUIAccess**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, aplikace obchází úrovně ochrany uživatelského rozhraní a vstup na vyšší oprávnění windows na ploše; v opačném případě jednotky `false`.  
  
   Další informace najdete v tématu `uiAccess` argument [/MANIFESTUAC (vložené informace UAC v manifestu)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UseLibraryDependencyInputs**  
  
   Volitelné **logická** parametru.  
  
   Pokud `true`, jsou použity vstupy nástroje librarian spíše než soubor knihovny sám při knihovny výstupy závislostí projektu se připojují.  
  
- **Verze**  
  
   Volitelné **řetězec** parametru.  
  
   Vložil číslo verze v hlavičce souboru .exe nebo .dll. Zadejte "`major[.minor]`". `major` a `minor` argumenty jsou desetinná čísla od 0 do 65535.  
  
   Další informace najdete v tématu [/Version (informace o verzi)](http://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



