---
title: Úloha MIDL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), MIDL task
- MIDL task (MSBuild (Visual C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 336a02927374e856a2d6f5a55eb03c5ae1ac7037
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845180"
---
# <a name="midl-task"></a>MIDL – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabalí nástroj kompilátoru MIDL (Microsoft Interface Definition Language), midl.exe. Další informace naleznete v tématu "Reference k příkazovému řádku" MIDL "na webu [MSDN](https://msdn.microsoft.com/) .  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úlohy **MIDL** . Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.  
  
- **AdditionalIncludeDirectories**  
  
     Parametr volitelného **řetězce []** .  
  
     Přidá adresář do seznamu adresářů, ve kterých jsou prohledány importované soubory IDL, zahrnuté hlavičkové soubory a konfigurační soubory aplikace (ACF).  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/I** v tématu Reference příkazového řádku MIDL.  
  
- **AdditionalOptions**  
  
     Volitelný **řetězcový** parametr.  
  
     Seznam možností příkazového řádku Například **"**_/option1/option2/Option #_". Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy MIDL.  
  
     Další informace naleznete v tématu "Reference k příkazovému řádku" MIDL "na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **ApplicationConfigurationMode**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` , umožňuje použít některá klíčová slova ACF v souboru IDL.  
  
     Další informace naleznete v tématu možnost **/app_config** v části "Reference příkazového řádku MIDL" na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **ClientStubFile**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje název souboru zástupné procedury klienta pro rozhraní RPC.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/cstub** v části "Reference příkazového řádku MIDL". V této tabulce se také zobrazí parametr **ServerStubFile** .  
  
- **CPreprocessOptions**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje možnosti, které se mají předat preprocesoru C/C++. Zadejte seznam možností preprocesoru oddělených mezerami.  
  
     Další informace naleznete v tématu možnost **/cpp_opt** v části "Reference příkazového řádku MIDL" na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **DefaultCharType**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje výchozí typ znaku, který kompilátor jazyka C použije pro zkompilování generovaného kódu.  
  
     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**Podpisy**|**/char podepsané**|  
    |**Celé**|**/char bez znaménka**|  
    |**Abecední**|**/char ascii7**|  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/char** v části "Reference příkazového řádku MIDL".  
  
- **DllDataFileName**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje název souboru vygenerovaného souboru *dlldata* pro proxy server dll.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/dlldata** v části "Reference příkazového řádku MIDL".  
  
- **EnableErrorChecks**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje typ kontroly chyb, který vygenerované zástupné procedury budou provádět za běhu.  
  
     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**Žádný**|**/Error None**|  
    |**EnableCustom**|**/Error**|  
    |**Vše**|**/Error All**|  
  
     Další informace naleznete v možnosti **/Error** v tématu Referenční příručka příkazového řádku MIDL na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **ErrorCheckAllocations**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` je, vyhledejte chyby nedostatku paměti.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/Error alokace** v tématu "Reference příkazového řádku MIDL".  
  
- **ErrorCheckBounds**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` aplikace kontroluje velikost vyhovujících a proměnlivých polí podle specifikace délky přenosu.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/Error Bounds_check** v tématu Referenční příručka příkazového řádku MIDL.  
  
- **ErrorCheckEnumRange**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` aplikace kontroluje, zda jsou hodnoty výčtu v povoleném rozsahu.  
  
     Další informace najdete v tématu možnost **/Error enum** v příkazovém řádku Help (**/?**) pro midl.exe.  
  
- **ErrorCheckRefPointers**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` je zaškrtnuto, nemusíte předávat žádné ukazatele na odkazy null do zástupných procedur klienta.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/Error ref** v tématu "MIDL příkazového řádku Reference".  
  
- **ErrorCheckStubData**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` , vygeneruje zástupnou proceduru, která zachytává výjimky při zařazování na straně serveru a šíří je zpátky do klienta.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/Error Stub_data** v tématu Referenční příručka příkazového řádku MIDL.  
  
- **GenerateClientFiles**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje, zda kompilátor generuje zdrojové soubory jazyka C na straně klienta pro rozhraní RPC.  
  
     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**Žádný**|**/Client žádné**|  
    |**Metrik**|**/Client zástupná procedura**|  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/Client** v části "Reference příkazového řádku MIDL".  
  
- **GenerateServerFiles**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje, zda kompilátor generuje zdrojové soubory jazyka C na straně serveru pro rozhraní vzdáleného volání procedur (RPC).  
  
     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**Žádný**|**/Server žádné**|  
    |**Metrik**|**/Server – zástupná procedura**|  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/Server** v tématu Reference příkazového řádku MIDL.  
  
- **GenerateStublessProxies**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` , vygeneruje plně interpretované zástupné procedury spolu s proxy bez zástupných procedur pro rozhraní objektů.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/oicf** v části "Reference příkazového řádku MIDL".  
  
- **GenerateTypeLibrary**  
  
     Volitelný **logický** parametr.  
  
     Pokud se `true` negeneruje soubor knihovny typů (. tlb).  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/notlb** v části "Reference příkazového řádku MIDL".  
  
- **HeaderFileName**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje název vygenerovaného souboru hlaviček.  
  
     Další informace naleznete v části **/h** nebo **/header** v části "Reference příkazového řádku MIDL" na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **IgnoreStandardIncludePath**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` , úloha MIDL vyhledává pouze adresáře určené pomocí přepínače **AdditionalIncludeDirectories** a ignoruje aktuální adresář a adresáře určené proměnnou prostředí include.  
  
     Další informace naleznete v tématu možnost **/no_def_idir** v části "Reference příkazového řádku MIDL" na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **InterfaceIdentifierFileName**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje název *souboru identifikátoru rozhraní* modelu COM. Tato možnost přepíše výchozí název získaný přidáním "_i. c" do názvu souboru IDL.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/IID** v části "Reference příkazového řádku MIDL".  
  
- **LocaleID**  
  
     Volitelný parametr **int**  
  
     Určuje *identifikátor národního prostředí* , který umožňuje použití mezinárodních znaků ve vstupních souborech, názvech souborů a cestách adresářů. Zadejte desítkový identifikátor národního prostředí.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/LCID** v části "Reference příkazového řádku MIDL". Viz také "ID národního prostředí přiřazené společností Microsoft" na webu MSDN.  
  
- **MkTypLibCompatible**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` vyžaduje Formát vstupního souboru, aby byl kompatibilní s mktyplib.exe verze 2,03.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/mktyplib203** v části "Reference příkazového řádku MIDL". Viz také "syntaxe souboru jazyka ODL" na webu MSDN.  
  
- **OutputDirectory**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje výchozí adresář, ve kterém úloha MIDL zapisuje výstupní soubory.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/out** v tématu Referenční příručka příkazového řádku MIDL.  
  
- **PreprocessorDefinitions**  
  
     Parametr volitelného **řetězce []** .  
  
     Určuje jednu nebo více *definicí*; To znamená, že název a volitelná hodnota, která má být předána preprocesoru jazyka C, jako by byla `#define` direktivou. Formát každé definice je, *název [= hodnota]*.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/D** v tématu Referenční příručka příkazového řádku MIDL. Viz také parametr **UndefinePreprocessorDefinitions** v této tabulce.  
  
- **ProxyFileName**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje název souboru proxy rozhraní pro rozhraní COM.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/proxy** v části "Reference příkazového řádku MIDL".  
  
- **RedirectOutputAndErrors**  
  
     Volitelný **řetězcový** parametr.  
  
     Přesměruje výstup, například chybové zprávy a upozornění, ze standardního výstupu do zadaného souboru.  
  
     Další informace naleznete v části **/o** v tématu Referenční příručka příkazového řádku MIDL na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **ServerStubFile**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje název souboru zástupné procedury serveru pro rozhraní RPC.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/sstub** v části "Reference příkazového řádku MIDL". Viz také parametr **ClientStubFile** v této tabulce.  
  
- **Zdroj**  
  
     Požadovaný parametr `ITaskItem[]`.  
  
     Určuje seznam zdrojových souborů oddělených mezerami.  
  
- **StructMemberAlignment**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje zarovnání (*úroveň balení*) struktur v cílovém systému.  
  
     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**NotSet**|*\<none>*|  
    |**1**|**/Zp1**|  
    |**2**|**/Zp2**|  
    |**4**|**/Zp4**|  
    |**8**|**/ZP8**|  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/zp** v části "Reference příkazového řádku MIDL". Možnost **/zp** je ekvivalentní možnosti **/Pack** a starší možnosti **/align** .  
  
- **SuppressCompilerWarnings**  
  
     Volitelný **logický** parametr.  
  
     `true`Potlačí zprávy upozornění z úlohy MIDL.  
  
     Další informace naleznete v tématu možnost **/no_warn** v části "Reference příkazového řádku MIDL" na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **SuppressStartupBanner**  
  
     Volitelný `Boolean` parametr.  
  
     Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/nologo** v tématu Referenční příručka příkazového řádku MIDL.  
  
- **TargetEnvironment**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje prostředí, ve kterém se aplikace spouští.  
  
     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**NotSet**|*\<none>*|  
    |**Win32**|**/ENV Win32**|  
    |**Itanium**|**/ENV ia64**|  
    |**Platformě**|**/ENV x64**|  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/ENV** v části "Reference příkazového řádku MIDL".  
  
- **TrackerLogDirectory**  
  
     Volitelný `String` parametr.  
  
     Určuje zprostředkující adresář, ve kterém jsou uložené protokoly sledování pro tento úkol.  
  
- **TypeLibFormat**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje formát souboru knihovny typů.  
  
     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**NewFormat**|**/newtlb**|  
    |**OldFormat**|**/oldtlb**|  
  
     Další informace naleznete v možnostech **/newtlb** a **/oldtlb** v tématu "MIDL příkazového řádku Reference" na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **Názevknihovnytypů**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje název souboru knihovny typů.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/TLB** v části "Reference příkazového řádku MIDL".  
  
- **UndefinePreprocessorDefinitions**  
  
     Parametr volitelného **řetězce []** .  
  
     Odebere všechny předchozí definice názvu předáním názvu do preprocesoru jazyka C, jako by byl `#undefine` direktivou. Zadejte jeden nebo více dříve definovaných názvů.  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/U** v tématu Referenční příručka příkazového řádku MIDL. Viz také parametr **PreprocessorDefinitions** v této tabulce.  
  
- **ValidateAllParameters**  
  
     Volitelný `Boolean` parametr.  
  
     Pokud `true` , vygeneruje další informace o kontrole chyb, které se používají k provádění kontrol integrity v době běhu. `false`V případě není vygenerována informace o kontrole chyb.  
  
     Další informace naleznete v možnostech **/Robust** a **/no_robust** v části "referenční příručka příkazového řádku" MIDL "na webu [MSDN](https://msdn.microsoft.com/) .  
  
- **Warnaserror –**  
  
     Volitelný `Boolean` parametr.  
  
     Pokud `true` aplikace považuje všechna upozornění za chyby.  
  
     Pokud není zadán parametr úlohy **WarningLevel** MIDL, jsou upozornění na výchozí úrovni úrovně 1 považována za chyby.  
  
     Další informace naleznete v tématu **/WX** Options in "MIDL příkazového řádku Reference" na webu [MSDN](https://msdn.microsoft.com/) . Viz také parametr **WarningLevel** v této tabulce.  
  
- **WarningLevel**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje závažnost (*úroveň upozornění*) upozornění, která se mají vygenerovat. Nevysílá se žádné upozornění na hodnotu 0. V opačném případě je vygenerováno upozornění, pokud je úroveň upozornění numericky menší nebo rovna zadané hodnotě.  
  
     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**0**|**/W0**|  
    |**1**|**/W1**|  
    |**2**|**/W2**|  
    |**3**|**/W3**|  
    |**4**|**/W4**|  
  
     Další informace naleznete na webu [MSDN](https://msdn.microsoft.com/) v možnosti **/w** v části "Reference k příkazovému řádku" MIDL. Viz také parametr **warnaserror –** v této tabulce.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
