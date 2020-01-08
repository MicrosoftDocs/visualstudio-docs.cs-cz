---
title: Úloha MIDL | Microsoft Docs
ms.date: 11/04/2016
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
- MSBuild (C++), MIDL task
- MIDL task (MSBuild (C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44b51617aa28f02763cc513a4619b3bd3b041cc5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592149"
---
# <a name="midl-task"></a>MIDL – úloha
Zabalí nástroj kompilátoru MIDL (Microsoft Interface Definition Language), *MIDL. exe*. Další informace naleznete v tématu [Reference k příkazovému řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

## <a name="parameters"></a>Parametry
 Následující popis popisuje parametry úlohy **MIDL** . Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.

- **AdditionalIncludeDirectories**

     Parametr volitelného **řetězce []** .

     Přidá adresář do seznamu adresářů, ve kterých jsou prohledány importované soubory IDL, zahrnuté hlavičkové soubory a konfigurační soubory aplikace (ACF).

     Další informace naleznete v části **/i** v tématu [Reference k příkazovému řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **AdditionalOptions**

     Volitelný **řetězcový** parametr.

     Seznam možností příkazového řádku Například/\<možnost1 >/\<možnost2 >/\<možnost # >. Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy MIDL.

     Další informace naleznete v tématu [Reference k příkazovému řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ApplicationConfigurationMode**

     Volitelný **logický** parametr.

     Pokud `true`, umožňuje použít některá klíčová slova ACF v souboru IDL.

     Další informace naleznete v tématu možnost **/app_config** v [odkazu příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ClientStubFile**

     Volitelný **řetězcový** parametr.

     Určuje název souboru zástupné procedury klienta pro rozhraní RPC.

     Další informace naleznete v tématu možnost **/cstub** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference). V této tabulce se také zobrazí parametr **ServerStubFile** .

- **CPreprocessOptions**

     Volitelný **řetězcový** parametr.

     Určuje možnosti, které se mají předat CC++ /preprocesoru. Zadejte seznam možností preprocesoru oddělených mezerami.

     Další informace naleznete v tématu možnost **/cpp_opt** v [odkazu příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **DefaultCharType**

     Volitelný **řetězcový** parametr.

     Určuje výchozí typ znaku, který kompilátor jazyka C použije pro zkompilování generovaného kódu.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Podpisy**|**/char podepsané**|
    |**Celé**|**/char bez znaménka**|
    |**Ascii**|**/char ascii7**|

     Další informace naleznete v tématu možnost **/char** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **DllDataFileName**

     Volitelný **řetězcový** parametr.

     Určuje název souboru vygenerovaného souboru *dlldata* pro proxy server dll.

     Další informace naleznete v tématu možnost **/dlldata** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **EnableErrorChecks**

     Volitelný **řetězcový** parametr.

     Určuje typ kontroly chyb, který vygenerované zástupné procedury budou provádět za běhu.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Žádné**|**/Error None**|
    |**EnableCustom**|**/Error**|
    |**Vše**|**/Error All**|

     Další informace naleznete v tématu možnost **/Error** v [referenci příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckAllocations**

     Volitelný **logický** parametr.

     Pokud `true`, vyhledejte chyby nedostatku paměti.

     Další informace naleznete v části **/Error Allocation** v [odkazu příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckBounds**

     Volitelný **logický** parametr.

     Pokud `true`, zkontroluje velikost vyhovujících a proměnlivých polí podle specifikace délky přenosu.

     Další informace naleznete v tématu možnost **/error bounds_check** v [odkazu příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckEnumRange**

     Volitelný **logický** parametr.

     Pokud `true`, zkontroluje, jestli jsou hodnoty výčtu v povoleném rozsahu.

     Další informace naleznete v možnosti **/Error enum** v příkazovém řádku Help ( **/?** ) pro soubor *MIDL. exe*.

- **ErrorCheckRefPointers**

     Volitelný **logický** parametr.

     Pokud `true`, ověřte, že neexistují žádné ukazatele odkazů s hodnotou null do zástupných procedur klienta.

     Další informace naleznete v tématu možnost **/Error ref** v [referenci příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckStubData**

     Volitelný **logický** parametr.

     Pokud `true`, vygeneruje zástupnou proceduru, která zachytává výjimky při zařazování na straně serveru a šíří je zpátky do klienta.

     Další informace naleznete v tématu možnost **/error stub_data** v [odkazu příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateClientFiles**

     Volitelný **řetězcový** parametr.

     Určuje, zda kompilátor generuje zdrojové soubory jazyka C na straně klienta pro rozhraní RPC.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Žádné**|**/Client žádné**|
    |**Metrik**|**/Client zástupná procedura**|

     Další informace naleznete v tématu možnost **/Client** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateServerFiles**

     Volitelný **řetězcový** parametr.

     Určuje, zda kompilátor generuje zdrojové soubory jazyka C na straně serveru pro rozhraní vzdáleného volání procedur (RPC).

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Žádné**|**/Server žádné**|
    |**Metrik**|**/Server – zástupná procedura**|

     Další informace naleznete v části **/Server** v tématu [Reference k příkazovému řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateStublessProxies**

     Volitelný **logický** parametr.

     Pokud `true`, vygeneruje plně interpretované zástupné procedury spolu s proxy bez zástupných procedur pro rozhraní objektů.

     Další informace naleznete v tématu možnost **/oicf** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateTypeLibrary**

     Volitelný **logický** parametr.

     Pokud `true`, soubor knihovny typů ( *. tlb*) se nevygeneruje.

     Další informace naleznete v tématu možnost **/notlb** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **HeaderFileName**

     Volitelný **řetězcový** parametr.

     Určuje název vygenerovaného souboru hlaviček.

     Další informace naleznete v tématu možnost **/h** nebo **/header** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **IgnoreStandardIncludePath**

     Volitelný **logický** parametr.

     Pokud `true`, úloha MIDL vyhledá pouze adresáře určené pomocí přepínače **AdditionalIncludeDirectories** a ignoruje aktuální adresář a adresáře určené PROMĚNNOU prostředí include.

     Další informace naleznete v tématu možnost **/no_def_idir** v [odkazu příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **InterfaceIdentifierFileName**

     Volitelný **řetězcový** parametr.

     Určuje název *souboru identifikátoru rozhraní* modelu COM. Tato možnost přepíše výchozí název získaný přidáním "_i. c" do názvu souboru IDL.

     Další informace naleznete v tématu možnost **/IID** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **LocaleID**

     Volitelný parametr **int**

     Určuje *identifikátor národního prostředí* , který umožňuje použití mezinárodních znaků ve vstupních souborech, názvech souborů a cestách adresářů. Zadejte desítkový identifikátor národního prostředí.

     Další informace naleznete v tématu možnost **/LCID** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také [identifikátory národního prostředí](/windows/desktop/intl/locale-identifiers).

- **MkTypLibCompatible**

     Volitelný **logický** parametr.

     Pokud `true`, vyžaduje, aby Formát vstupního souboru byl kompatibilní s *MkTypLib. exe* verze 2,03.

     Další informace naleznete v tématu možnost **/mktyplib203** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také [syntaxe souboru ODL](/previous-versions/windows/desktop/automat/odl-file-syntax) na webu MSDN.

- **OutputDirectory**

     Volitelný **řetězcový** parametr.

     Určuje výchozí adresář, ve kterém úloha MIDL zapisuje výstupní soubory.

     Další informace naleznete v tématu možnost **/out** v [referenci příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **PreprocessorDefinitions**

     Parametr volitelného **řetězce []** .

     Určuje jednu nebo více *definicí*; To znamená, že název a volitelná hodnota, která má být předána preprocesoru jazyka C, jako by byla direktivou `#define`. Formát každé definice je, *název [= hodnota]* .

     Další informace naleznete v tématu **/d** možnost v [referenci příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také parametr **UndefinePreprocessorDefinitions** v této tabulce.

- **ProxyFileName**

     Volitelný **řetězcový** parametr.

     Určuje název souboru proxy rozhraní pro rozhraní COM.

     Další informace naleznete v tématu možnost **/proxy** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **RedirectOutputAndErrors**

     Volitelný **řetězcový** parametr.

     Přesměruje výstup, například chybové zprávy a upozornění, ze standardního výstupu do zadaného souboru.

     Další informace naleznete v tématu možnost **/o** v [referenci příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ServerStubFile**

     Volitelný **řetězcový** parametr.

     Určuje název souboru zástupné procedury serveru pro rozhraní RPC.

     Další informace naleznete v tématu možnost **/sstub** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také parametr **ClientStubFile** v této tabulce.

- **Zdroj**

     Vyžaduje se `ITaskItem[]` parametr.

     Určuje seznam zdrojových souborů oddělených mezerami.

- **StructMemberAlignment**

     Volitelný **řetězcový** parametr.

     Určuje zarovnání (*úroveň balení*) struktur v cílovém systému.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**NotSet**|*\<žádné >*|
    |**1**|**/Zp1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/Zp8**|

     Další informace naleznete v tématu možnost **/zp** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference). Možnost **/zp** je ekvivalentní možnosti **/Pack** a starší možnosti **/align** .

- **SuppressCompilerWarnings**

     Volitelný **logický** parametr.

     Pokud `true`, potlačí zprávy upozornění z úlohy MIDL.

     Další informace naleznete v tématu možnost **/no_warn** v [odkazu příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **SuppressStartupBanner**

     Volitelný parametr `Boolean`.

     Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.

     Další informace naleznete v tématu možnost **/nologo** v [referenci příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **TargetEnvironment**

     Volitelný **řetězcový** parametr.

     Určuje prostředí, ve kterém se aplikace spouští.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**NotSet**|*\<žádné >*|
    |**Win32**|**/ENV Win32**|
    |**Procesor**|**/ENV ia64**|
    |**X64**|**/env x64**|

     Další informace naleznete v tématu možnost **/ENV** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **TrackerLogDirectory**

     Volitelný parametr `String`.

     Určuje zprostředkující adresář, ve kterém jsou uložené protokoly sledování pro tento úkol.

- **TypeLibFormat**

     Volitelný **řetězcový** parametr.

     Určuje formát souboru knihovny typů.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**NewFormat**|**/newtlb**|
    |**OldFormat**|**/oldtlb**|

     Další informace naleznete v tématu možnosti **/newtlb** a **/oldtlb** v článku [Referenční příručka příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **TypeLibraryName**

     Volitelný **řetězcový** parametr.

     Určuje název souboru knihovny typů.

     Další informace naleznete v tématu možnost **/TLB** v [Referenční příručce příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **UndefinePreprocessorDefinitions**

     Parametr volitelného **řetězce []** .

     Odebere všechny předchozí definice názvu předáním názvu do preprocesoru jazyka C, jako by bylo direktivou `#undefine`. Zadejte jeden nebo více dříve definovaných názvů.

     Další informace naleznete v tématu možnost **/u** v [referenci příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také parametr **PreprocessorDefinitions** v této tabulce.

- **ValidateAllParameters**

     Volitelný parametr `Boolean`.

     Pokud `true`, vygeneruje další informace o kontrole chyb, které se používají k provádění kontrol integrity v době běhu. Pokud `false`, informace o kontrole chyb nejsou vygenerovány.

     Další informace naleznete v možnostech **/Robust** a **/no_robust** v tématu [Reference k příkazovému řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **WarnAsError**

     Volitelný parametr `Boolean`.

     Pokud `true`, zpracovává všechna upozornění jako chyby.

     Pokud není zadán parametr úlohy **WarningLevel** MIDL, jsou upozornění na výchozí úrovni úrovně 1 považována za chyby.

     Další informace naleznete v tématu **/WX** Options in [MIDL příkazového řádku reference](/windows/desktop/Midl/midl-command-line-reference). Viz také parametr **WarningLevel** v této tabulce.

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

     Další informace naleznete v tématu možnost **/w** v [referenci příkazového řádku MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také parametr **warnaserror –** v této tabulce.

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
