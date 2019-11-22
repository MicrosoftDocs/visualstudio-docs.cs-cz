---
title: Propojit úkol | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 181c32017a84328037ea46d49698821fa3cb41ea
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295882"
---
# <a name="link-task"></a>Úloha odkazu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabalí nástroj vizuálního C++ linkeru, Link. exe. Nástroj Linker propojuje soubory objektů a knihoven Common Object File Format (COFF) a vytvoří spustitelný soubor (. exe) nebo dynamickou knihovnu (DLL). Další informace naleznete v tématu [Možnosti linkeru](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úkolu **propojení** . Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.  
  
- **AdditionalDependencies**  
  
   Parametr volitelného **řetězce []** .  
  
   Určuje seznam vstupních souborů, které mají být přidány do příkazu.  
  
   Další informace najdete v tématu [připojení vstupních souborů](https://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
- **AdditionalLibraryDirectories**  
  
   Parametr volitelného **řetězce []** .  
  
   Přepíše cestu ke knihovně prostředí. Zadejte název adresáře.  
  
   Další informace najdete v tématu [/LIBPATH (Další Libpath)](https://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
- **AdditionalManifestDependencies**  
  
   Parametr volitelného **řetězce []** .  
  
   Určuje atributy, které budou umístěny v sekci `dependency` souboru manifestu.  
  
   Další informace najdete v tématu [/MANIFESTDEPENDENCY (určení závislostí manifestu)](https://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Viz také "konfigurační soubory vydavatele" na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) .  
  
- **AdditionalOptions**  
  
   Volitelný **řetězcový** parametr.  
  
   Seznam možností linkeru, jak je uvedeno na příkazovém řádku. Například **"** _/option1/option2/Option #_ ". Pomocí tohoto parametru lze zadat možnosti linkeru, které nejsou reprezentovány žádným jiným parametrem **Propojovací úlohy.**  
  
   Další informace naleznete v tématu [Možnosti linkeru](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
- **AddModuleNamesToAssembly**  
  
   Parametr volitelného **řetězce []** .  
  
   Přidá do sestavení odkaz na modul.  
  
   Další informace naleznete v tématu [/ASSEMBLYMODULE (Přidání modulu MSIL do sestavení)](https://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
- **AllowIsolation**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, způsobí, že operační systém provede vyhledání a načtení manifestu. Pokud `false`, označuje, že knihovny DLL jsou načteny, jako kdyby nebyl žádný manifest.  
  
   Další informace naleznete v tématu [/ALLOWISOLATION (Lookup Manifesting)](https://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
- **AssemblyDebug**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, vygeneruje atribut **DebuggableAttribute** společně s trasováním informací o ladění a ZAKÁŽE optimalizace JIT. Pokud `false`, vygeneruje atribut **DebuggableAttribute** , ale zakáže sledování ladicích informací a POVOLÍ optimalizace JIT.  
  
   Další informace najdete v tématu [/ASSEMBLYDEBUG (Add DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
- **AssemblyLinkResource**  
  
   Parametr volitelného **řetězce []** .  
  
   Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru; zdrojový soubor není umístěný do výstupního souboru. Zadejte název prostředku.  
  
   Další informace najdete v tématu [/ASSEMBLYLINKRESOURCE (odkaz na prostředek .NET Framework)](https://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
- **AttributeFileTracking**  
  
   Implicitní parametr **Boolean**  
  
   Umožňuje hlubší sledování souborů pro funkci přírůstkového propojení při zachytávání. Vždycky vrátí `true`.  
  
- **BaseAddress**  
  
   Volitelný **řetězcový** parametr.  
  
   Nastaví základní adresu pro sestavení programu nebo knihovny DLL. Zadejte `{address[,size] | @filename,key}`.  
  
   Další informace najdete v tématu [/Base (základní adresa)](https://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
- **BuildingInIDE**  
  
   Volitelný **logický** parametr.  
  
   Pokud je nastaveno na true, označuje, že nástroj MSBuild je vyvolán z rozhraní IDE. V opačném případě označuje, že nástroj MSBuild je vyvolán z příkazového řádku.  
  
   Tento parametr nemá ekvivalentní možnost linkeru.  
  
- **CLRImageType**  
  
   Volitelný **řetězcový** parametr.  
  
   Nastaví typ image modulu CLR (Common Language Runtime).  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti linkeru.  
  
  - **Výchozí** -  *\<žádné >*  
  
  - **ForceIJWImage** -  **/CLRIMAGETYPE: IJW**  
  
  - **ForcePureILImage** -  **/CLRIMAGETYPE: Pure**  
  
  - **ForceSafeILImage** -  **/CLRIMAGETYPE: Safe**  
  
    Další informace najdete v tématu [/CLRIMAGETYPE (určení typu image CLR)](https://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
- **CLRSupportLastError**  
  
   Volitelný **řetězcový** parametr.  
  
   Zachová poslední chybový kód funkcí volaných prostřednictvím mechanismu volání nespravovaného kódu.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti linkeru.  
  
  - **Povoleno** -  **/CLRSupportLastError**  
  
  - **Disabled** -  **/CLRSupportLastError: No**  
  
  - **SystemDlls** -  **/CLRSupportLastError: SYSTEMDLL**  
  
    Další informace naleznete v tématu [/CLRSUPPORTLASTERROR (zachování kódu poslední chyby pro volání PInvoke)](https://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
- **CLRThreadAttribute**  
  
   Volitelný **řetězcový** parametr.  
  
   Explicitně určuje atribut vlákna pro vstupní bod programu CLR.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti linkeru.  
  
  - **DefaultThreadingAttribute** -  **/CLRTHREADATTRIBUTE: žádné**  
  
  - **MTAThreadingAttribute** -  **/CLRTHREADATTRIBUTE: MTA**  
  
  - **STAThreadingAttribute** -  **/CLRTHREADATTRIBUTE: sta**  
  
    Další informace najdete v tématu [/CLRTHREADATTRIBUTE (nastavení atributu vlákna modulu CLR)](https://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
- **CLRUnmanagedCodeCheck**  
  
   Volitelný **logický** parametr.  
  
   Určuje, zda linker bude použít **SuppressUnmanagedCodeSecurityAttribute** na volání volání volání nespravovaného kódu do nativních knihoven DLL.  
  
   Další informace najdete v tématu [/CLRUNMANAGEDCODECHECK (přidání SuppressUnmanagedCodeSecurityAttribute)](https://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
- **CreateHotPatchableImage**  
  
   Volitelný **řetězcový** parametr.  
  
   Připraví obrázek pro Hot patching.  
  
   Zadejte jednu z následujících hodnot, která odpovídá možnosti linkeru.  
  
  - **Povoleno** -  **/functionpadmin**  
  
  - **X86Image** -  **/functionpadmin: 5**  
  
  - **X64Image** -  **/functionpadmin: 6**  
  
  - **ItaniumImage** -  **/functionpadmin: 16**  
  
    Další informace najdete v tématu [/functionpadmin (Create opravitelnou za provozu image)](https://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
- **DataExecutionPrevention**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, označuje, že spustitelný soubor byl testován tak, aby byl kompatibilní s funkcí Zabránění spuštění dat systému Windows.  
  
   Další informace najdete v tématu [/NXCOMPAT (kompatibilní se zabráněním spuštění dat)](https://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
- **DelayLoadDLLs**  
  
   Parametr volitelného **řetězce []** .  
  
   Tento parametr způsobí *opožděné načtení* knihoven DLL. Zadejte název knihovny DLL pro odložené načtení.  
  
   Další informace najdete v tématu [/DELAYLOAD (import zpožděného načtení)](https://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
- **DelaySign**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, částečně podepíše sestavení. Ve výchozím nastavení je hodnota `false`.  
  
   Další informace naleznete v tématu [/delaysign (částečné podepsání sestavení)](https://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
- **Ovladač**  
  
   Volitelný **řetězcový** parametr.  
  
   Zadáním tohoto parametru sestavíte ovladač režimu jádra systému Windows NT.  
  
   Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti linkeru.  
  
  - **NotSet** -  *\<none>*  
  
  - **/Driver** **ovladače** -   
  
  - **Pouze** -  **/Driver: pouze** pro  
  
  - **Wdm** -  **/Driver: WDM**  
  
    Další informace najdete v tématu [/Driver (ovladač režimu jádra Windows NT)](https://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
- **EmbedManagedResourceFile**  
  
   Parametr volitelného **řetězce []** .  
  
   Vloží soubor prostředků do sestavení. Zadejte požadovaný název souboru prostředků. Volitelně můžete zadat logický název, který se používá k načtení prostředku, a možnost **Private** , která označuje manifest sestavení, že soubor prostředků je privátní.  
  
   Další informace najdete v tématu [/ASSEMBLYRESOURCE (vložení spravovaného prostředku)](https://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
- **EnableCOMDATFolding**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, povolí identické skládání COMDAT.  
  
   Další informace najdete v argumentu `ICF[= iterations]` [/opt (optimalizace)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **EnableUAC**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, určuje, že informace nástroje řízení uživatelských účtů (UAC) budou vloženy do manifestu programu.  
  
   Další informace naleznete v tématu [/MANIFESTUAC (vložení informací o nástroji Řízení uživatelských účtů v manifestu)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **EntryPointSymbol**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje funkci vstupního bodu jako počáteční adresu souboru. exe nebo knihovny DLL. Jako hodnotu parametru zadejte název funkce.  
  
   Další informace naleznete v tématu [/entry (symbol vstupního bodu)](https://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
- **FixedBaseAddress**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, vytvoří program nebo knihovnu DLL, které se dají načíst jenom na upřednostňovanou základní adresu.  
  
   Další informace najdete v tématu [/fixed (pevná základní adresa)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
- **ForceFileOutput**  
  
   Volitelný **řetězcový** parametr.  
  
   Instruuje linker, aby vytvořil platný soubor. exe nebo knihovnu DLL i v případě, že se na symbol odkazuje, ale není definován, nebo je definován násobek.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Povoleno** -  **/Force**  
  
  - **MultiplyDefinedSymbolOnly** -  **/Force: více**  
  
  - **UndefinedSymbolOnly** -  **/Force: nevyřešené**  
  
    Další informace najdete v tématu [/Force (vynucení výstupu souboru)](https://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
- **ForceSymbolReferences**  
  
   Parametr volitelného **řetězce []** .  
  
   Tento parametr oznamuje linkeru, aby přidal zadaný symbol do tabulky symbolů.  
  
   Další informace naleznete v tématu [/include (vynucení odkazů na symboly)](https://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
- **FunctionOrder**  
  
   Volitelný **řetězcový** parametr.  
  
   Tento parametr optimalizuje program tím, že do bitové kopie umístí zadané zabalené funkce (sekvence COMDAT) do obrazu v předdefinovaném pořadí.  
  
   Další informace najdete v tématu [/Order (vložení funkcí v pořadí)](https://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
- **GenerateDebugInformation**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, vytvoří informace o ladění pro soubor. exe nebo knihovnu DLL.  
  
   Další informace najdete v tématu [/Debug (generování informací o ladění)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
- **GenerateManifest**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, vytvoří soubor souběžného manifestu.  
  
   Další informace naleznete v tématu [/manifest (Vytvoření manifestu souběžného sestavení)](https://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
- **GenerateMapFile**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, vytvoří *soubor mapy*. Přípona názvu souboru souboru mapy je. map.  
  
   Další informace najdete v tématu [parametr/map (generování souboru mapování)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
- **HeapCommitSize**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje velikost fyzické paměti v haldě, která se má přidělit v čase.  
  
   Další informace najdete v argumentu `commit` v [/Heap (nastavení velikosti haldy)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Další informace najdete také v parametru **HeapReserveSize** .  
  
- **HeapReserveSize**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje celkové přidělení haldy ve virtuální paměti.  
  
   Další informace najdete v argumentu `reserve` v [/Heap (nastavení velikosti haldy)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Viz také parametr **HeapCommitSize** v této tabulce.  
  
- **IgnoreAllDefaultLibraries**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, přikáže linkeru, aby odebral jednu nebo více výchozích knihoven ze seznamu knihoven, které vyhledává, když přeloží externí odkazy.  
  
   Další informace najdete v tématu [/NODEFAULTLIB (ignorování knihoven)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **IgnoreEmbeddedIDL**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, určuje, že žádné atributy IDL ve zdrojovém kódu by neměly být zpracovány do souboru. idl.  
  
   Další informace naleznete v tématu [/IGNOREIDL (Nezpracovávat atributy do MIDL)](https://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
- **IgnoreImportLibrary**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, určuje, že knihovna importu vygenerovaná touto konfigurací by neměla být importována do závislých projektů.  
  
   Tento parametr neodpovídá Možnosti linkeru.  
  
- **IgnoreSpecificDefaultLibraries**  
  
   Parametr volitelného **řetězce []** .  
  
   Určuje jeden nebo více názvů výchozích knihoven, které se mají ignorovat. Více knihoven oddělte středníkem.  
  
   Další informace najdete v tématu [/NODEFAULTLIB (ignorování knihoven)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **ImageHasSafeExceptionHandlers**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, linker vytvoří obrázek pouze v případě, že může také vytvořit tabulku bezpečných obslužných rutin výjimek pro image.  
  
   Další informace naleznete v tématu [/SAFESEH (Image má bezpečné obslužné rutiny výjimek)](https://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
- **ImportLibrary**  
  
   Uživatelem zadaný název knihovny importu, který nahradí výchozí název knihovny.  
  
   Další informace najdete v tématu [/IMPLIB (pojmenování knihovny importu)](https://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
- **KeyContainer**  
  
   Volitelný **řetězcový** parametr.  
  
   Kontejner, který obsahuje klíč pro podepsané sestavení.  
  
   Další informace naleznete v tématu [/keycontainer (určení kontejneru klíčů pro podepsání sestavení)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Podívejte se také na parametr **keyfile** v této tabulce.  
  
- **KeyFile**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje soubor, který obsahuje klíč pro podepsané sestavení.  
  
   Další informace naleznete v tématu [/keyfile (určení klíče nebo páru klíčů pro podepsání sestavení)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Podívejte se také na parametr **obsahuje** .  
  
- **LargeAddressAware**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, aplikace může zpracovávat adresy větší než 2 gigabajty.  
  
   Další informace najdete v tématu [/LARGEADDRESSAWARE (zpracování velkých adres)](https://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
- **LinkDLL**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, aplikace vytvoří knihovnu DLL jako hlavní výstupní soubor.  
  
   Další informace naleznete v tématu [/DLL (sestavení knihovny DLL)](https://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
- **LinkErrorReporting**  
  
   Volitelný **řetězcový** parametr.  
  
   Umožňuje poskytnout informace o vnitřní chybě kompilátoru (ICE) přímo společnosti Microsoft.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **NoErrorReport** -  **/errorreport: none**  
  
  - **Vyzvat okamžitě** -  **/errorreport: prompt**  
  
  - **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**  
  
  - **SendErrorReport** -  **/errorreport: Send**  
  
    Další informace najdete v tématu [/errorreport (hlášení chyb interního linkeru)](https://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
- **LinkIncremental**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, umožňuje přírůstkové propojení.  
  
   Další informace najdete v tématu [/incremental (propojování přírůstkově)](https://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
- **LinkLibraryDependencies**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, určuje, že výstupy knihoven ze závislostí projektu jsou automaticky propojeny v.  
  
   Tento parametr neodpovídá Možnosti linkeru.  
  
- **LinkStatus**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, určuje, že linker má zobrazit indikátor průběhu, který ukazuje, jaké procento odkazu je dokončeno.  
  
   Další informace naleznete v argumentu `STATUS` [/LTCG (generování kódu při propojování)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **LinkTimeCodeGeneration**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje možnosti optimalizace na základě profilu.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Výchozí** -  *\<žádné >*  
  
  - **UseLinkTimeCodeGeneration** -  **/LTCG**  
  
  - **PGInstrument** -  **/LTCG: PGInstrument**  
  
  - **PGOptimization** -  **/LTCG: PGOptimize**  
  
  - **PGUpdate**  
  
     \- **/LTCG:PGUpdate**  
  
    Další informace naleznete v tématu [/LTCG (generování kódu při propojování)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **ManifestFile**  
  
   Volitelný **řetězcový** parametr.  
  
   Změní výchozí název souboru manifestu na zadaný název souboru.  
  
   Další informace naleznete v tématu [/MANIFESTFILE (název souboru manifestu)](https://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
- **MapExports**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, instruuje linker, aby zahrnoval exportované funkce v souboru mapy.  
  
   Další informace najdete v argumentu `EXPORTS` [/MapInfo (zahrnutí informací v souboru mapování)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
- **MapFileName**  
  
   Volitelný **řetězcový** parametr.  
  
   Změní výchozí název souboru mapy na zadaný název souboru.  
  
- **MergedIDLBaseFileName**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje název souboru a příponu názvu souboru. idl.  
  
   Další informace naleznete v tématu [/IDLOUT (pojmenování výstupních souborů MIDL)](https://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
- **MergeSections**  
  
   Volitelný **řetězcový** parametr.  
  
   Kombinuje oddíly v obrázku. Zadejte `from-section=to-section`.  
  
   Další informace naleznete v tématu [/merge (kombinování oddílů)](https://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
- **MidlCommandFile**  
  
   Volitelný **řetězcový** parametr.  
  
   Zadejte název souboru, který obsahuje možnosti příkazového řádku MIDL.  
  
   Další informace naleznete v tématu [/MIDL (určení možností příkazového řádku MIDL)](https://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
- **MinimumRequiredVersion**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje minimální požadovanou verzi subsystému. Argumenty jsou desítková čísla v rozsahu 0 až 65535.  
  
- **ModuleDefinitionFile**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje název [souboru definice modulu](https://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8).  
  
   Další informace najdete v tématu [/def (určení souboru definice modulu)](https://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
- **MSDOSStubFileName**  
  
   Volitelný **řetězcový** parametr.  
  
   Připojí zadaný program pro zástupné procedury systému MS-DOS k programu Win32.  
  
   Další informace najdete v tématu [/stub (název souboru zástupného kódu MS-DOS)](https://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
- **NoEntryPoint**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, určuje knihovnu DLL pouze pro prostředky.  
  
   Další informace najdete v tématu [/NOENTRY (bez vstupního bodu)](https://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
- **ObjectFiles**  
  
   Parametr implicitního **řetězce []** .  
  
   Určuje soubory objektů, které jsou propojeny.  
  
- **OptimizeReferences**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, eliminuje funkce nebo data, která nejsou nikdy odkazována.  
  
   Další informace najdete v argumentu `REF` v [/opt (optimalizace)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **OutputFile**  
  
   Volitelný **řetězcový** parametr.  
  
   Přepíše výchozí název a umístění programu, který vytvoří linker.  
  
   Další informace naleznete v tématu [/out (název výstupního souboru)](https://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
- **PerUserRedirection**  
  
   Volitelný **logický** parametr.  
  
   Pokud je povolený výstup `true` a registru, vynutí **HKEY_CLASSES_ROOT** přesměrování zápisy registru do **HKEY_CURRENT_USER**.  
  
- **PreprocessOutput**  
  
   Volitelný parametr `ITaskItem[]`.  
  
   Definuje pole výstupních položek preprocesoru, které mohou být spotřebovány a generovány úlohami.  
  
- **PreventDllBinding**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, označuje, že se má svázat. exe, že by se neměla svázat propojený obrázek.  
  
   Další informace naleznete v tématu [/ALLOWBIND (zabránění vazbě knihoven DLL)](https://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
- **Profilu**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, vytvoří výstupní soubor, který se dá použít s profilerem **Performance Tools** .  
  
   Další informace najdete v tématu [/Profile (Performance Tools profiler)](https://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
- **ProfileGuidedDatabase**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje název souboru. PGD, který se použije k uložení informací o spuštěném programu.  
  
   Další informace najdete v tématu [/PGD (určení databáze pro optimalizace na základě profilu)](https://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
- **ProgramDatabaseFile**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje název pro databázi programu (PDB), kterou linker vytvoří.  
  
   Další informace najdete v tématu [/PDB (použití databáze programu)](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
- **RandomizedBaseAddress**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, nástroj vygeneruje spustitelnou bitovou kopii, která se dá náhodně využít při načítání, pomocí funkce ASLR ( *Address Space Layout layout* ) systému Windows.  
  
   Další informace najdete v tématu [/DYNAMICBASE (použití náhodnosti rozložení adresního prostoru)](https://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
- **RegisterOutput**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, zaregistruje primární výstup tohoto sestavení.  
  
- **Zarovnání oddílu**  
  
   Volitelný **celočíselný** parametr  
  
   Určuje zarovnání jednotlivých oddílů v rámci lineárního adresního prostoru programu. Hodnota parametru je jednotkový počet bajtů a je mocninou dvou.  
  
   Další informace najdete v tématu [/align (zarovnání oddílů)](https://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
- **SetChecksum –**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, nastaví kontrolní součet v hlavičce souboru. exe.  
  
   Další informace naleznete v tématu [/release (Nastavení kontrolního součtu)](https://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
- **ShowProgress**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje podrobnosti o sestavách průběhu operace propojení.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **NotSet** -  *\<none>*  
  
  - **LinkVerbose** -  **/VERBOSE**  
  
  - **LinkVerboseLib** -  **/VERBOSE:Lib**  
  
  - **LinkVerboseICF** -  **/VERBOSE:ICF**  
  
  - **LinkVerboseREF** -  **/VERBOSE:REF**  
  
  - **LinkVerboseSAFESEH** -  **/VERBOSE:SAFESEH**  
  
  - **LinkVerboseCLR** -  **/VERBOSE:CLR**  
  
    Další informace najdete v tématu [/verbose (Tisk zpráv o průběhu)](https://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
- **Prostředky**  
  
   Vyžaduje se `ITaskItem[]` parametr.  
  
   Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.  
  
- **SpecifySectionAttributes**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje atributy oddílu. Tím dojde k přepsání atributů, které byly nastaveny při kompilaci souboru. obj pro oddíl.  
  
   Další informace najdete v tématu [/section (určení atributů oddílu)](https://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
- **StackCommitSize**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje velikost fyzické paměti v každém přidělení, pokud je přidělena další paměť.  
  
   Další informace naleznete v argumentu `commit` [/Stack (přidělení zásobníku)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StackReserveSize**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje celkovou velikost alokačního zásobníku ve virtuální paměti.  
  
   Další informace naleznete v argumentu `reserve` [/Stack (přidělení zásobníku)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StripPrivateSymbols**  
  
   Volitelný **řetězcový** parametr.  
  
   Vytvoří druhý soubor programové databáze (PDB), který vynechá symboly, které nechcete distribuovat vašim zákazníkům. Zadejte název druhého souboru PDB.  
  
   Další informace naleznete v tématu [/PDBSTRIPPED (proložení privátních symbolů)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
- **Provozuschopn**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje prostředí pro spustitelný soubor.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **NotSet** -  *\<none>*  
  
  - **Konzola** -  **/SUBSYSTEM: konzola**  
  
  - **Windows** -  **/SUBSYSTEM:WINDOWS**  
  
  - **Nativní** -  **/SUBSYSTEM: Native**  
  
  - **Aplikace rozhraní EFI** -  **/SUBSYSTEM: EFI_APPLICATION**  
  
  - **EFI Boot Service Driver** -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
  - /Subsystem **EFI ROM** -  **: EFI_ROM**  
  
  - **EFI Runtime** -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
  - **WindowsCE** -  **/SUBSYSTEM:WINDOWSCE**  
  
  - **POSIX** -  **/SUBSYSTEM:POSIX**  
  
    Další informace najdete v tématu [/Subsystem (určení subsystému)](https://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, sdělí linkeru, aby do finální image nezahrnula tabulku importních adres (IAT) s možností vazby.  
  
   Další informace najdete v argumentu `NOBIND` [/Delay (nastavení importu zpožděného načtení)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, sdělí pomocnou funkci opožděného načtení, aby podporovala explicitní uvolnění knihovny DLL.  
  
   Další informace najdete v argumentu `UNLOAD` [/Delay (nastavení importu zpožděného načtení)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SuppressStartupBanner**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.  
  
   Další informace naleznete v tématu [/nologo (potlačení úvodního nápisu při spouštění) (Linker)](https://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
- **SwapRunFromCD**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, sdělí operačnímu systému, aby nejprve zkopíroval výstup linkeru do odkládacího souboru, a pak z něj spusťte bitovou kopii.  
  
   Další informace naleznete v argumentu `CD` [/SWAPRUN (načtení výstupu linkeru do odkládacího souboru)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Další informace najdete také v parametru **SwapRunFromNET** .  
  
- **SwapRunFromNET**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, sdělí operačnímu systému, aby nejprve zkopíroval výstup linkeru do odkládacího souboru, a pak z něj spusťte bitovou kopii.  
  
   Další informace naleznete v argumentu `NET` [/SWAPRUN (načtení výstupu linkeru do odkládacího souboru)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Viz také parametr **SwapRunFromCD** v této tabulce.  
  
- **TargetMachine**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje cílovou platformu pro program nebo knihovnu DLL.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **NotSet** -  *\<none>*  
  
  - **MachineARM** -  **/Machine: ARM**  
  
  - **MachineEBC** -  **/Machine: EBC**  
  
  - **MachineIA64** -  **/Machine: ia64**  
  
  - **MachineMIPS** -  **/Machine: MIPS**  
  
  - **MachineMIPS16** -  **/MACHINE:MIPS16**  
  
  - **MachineMIPSFPU** -  **/Machine: MIPSFPU**  
  
  - **MachineMIPSFPU16** -  **/Machine: MIPSFPU16**  
  
  - **MachineSH4** -  **/MACHINE:SH4**  
  
  - **MachineTHUMB** -  **/Machine: palec**  
  
  - **MachineX64** -  **/Machine: x64**  
  
  - **MachineX86** -  **/Machine: x86**  
  
    Další informace najdete v tématu [/Machine (určení cílové platformy)](https://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
- **TerminalServerAware**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, nastaví příznak v poli IMAGE_OPTIONAL_HEADER DllCharacteristics v volitelné hlavičce bitové kopie programu. Pokud je tento příznak nastaven, terminálový server neprovede určité změny aplikace.  
  
   Další informace najdete v tématu [/TSAWARE (vytvoření aplikace pracující s terminálovým serverem)](https://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
- **TrackerLogDirectory**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje adresář protokolu sledování.  
  
- **TreatLinkerWarningAsErrors**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, negeneruje žádný výstupní soubor, pokud linker vygeneruje upozornění.  
  
   Další informace naleznete v tématu [/WX (zpracovávání upozornění linkeru jako chyby)](https://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
- **TurnOffAssemblyGeneration**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, vytvoří obrázek pro aktuální výstupní soubor bez sestavení .NET Framework.  
  
   Další informace naleznete v tématu [/NOASSEMBLY (Vytvoření modulu MSIL)](https://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
- **TypeLibraryFile**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje název souboru a příponu názvu souboru. tlb. Zadejte název souboru nebo cestu a název souboru.  
  
   Další informace najdete v tématu [/TLBOUT (název. Soubor TLB)](https://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
- **TypeLibraryResourceID**  
  
   Volitelný **celočíselný** parametr  
  
   Určuje uživatelem zadanou hodnotu pro knihovnu typů vytvořenou linkerem. Zadejte hodnotu od 1 do 65535.  
  
   Další informace najdete v tématu [/TLBID (určení ID prostředku pro knihovnu TypeLib)](https://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
- **UACExecutionLevel**  
  
   Volitelný **řetězcový** parametr.  
  
   Určuje požadovanou úroveň spuštění aplikace v případě, že je spuštěna pomocí nástroje řízení uživatelských účtů.  
  
   Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
  - **Podle volajícího** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **Vyžadovat správce** - `level='requireAdministrator'`  
  
    Další informace naleznete v argumentu `level` [/MANIFESTUAC (vložení informací o nástroji Řízení uživatelských účtů v manifestu)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UACUIAccess**  
  
   Volitelný **logický** parametr.  
  
   Pokud `true`, aplikace obchází úrovně ochrany uživatelského rozhraní a vstup jednotek do oken s vyšším oprávněním na ploše. v opačném případě `false`.  
  
   Další informace naleznete v argumentu `uiAccess` [/MANIFESTUAC (vložení informací o nástroji Řízení uživatelských účtů v manifestu)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UseLibraryDependencyInputs**  
  
   Volitelný **logický** parametr.  
  
   Pokud je `true`, místo samotného souboru knihovny se použijí vstupy pro nástroj Librarian, když jsou v knihovně výstupy na závislosti projektu.  
  
- **Verze**  
  
   Volitelný **řetězcový** parametr.  
  
   Vložte číslo verze do hlavičky souboru. exe nebo. dll. Zadejte "`major[.minor]`". Argumenty `major` a `minor` jsou desítková čísla od 0 do 65535.  
  
   Další informace najdete v tématu [/Version (informace o verzi)](https://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
