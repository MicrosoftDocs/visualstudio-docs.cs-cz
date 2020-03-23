---
title: MIDL Úkol | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 7a43975244eaf064c9ed7608fa41c16854ca140f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633470"
---
# <a name="midl-task"></a>MIDL – úloha

Zalomí kompilátor jazyka Microsoft Interface Definition Language (MIDL), *midl.exe*. Další informace naleznete v [tématu ODKAZ NA PŘÍKAZOVÝ ŘÁDEK MIDL](/windows/desktop/Midl/midl-command-line-reference).

## <a name="parameters"></a>Parametry

 Následující text popisuje parametry úlohy **MIDL.** Většina parametrů úlohy a několik sad parametrů odpovídají možnosti příkazového řádku.

- **Další includeředitelé adresáře**

     Volitelný **parametr String[].**

     Přidá adresář do seznamu adresářů, které jsou vyhledávány pro importované soubory IDL, zahrnuté soubory hlaviček a konfigurační soubory aplikací (ACF).

     Další informace naleznete v možnosti **/I** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Další možnosti**

     Volitelný **parametr String.**

     Seznam možností příkazového řádku. Například /\<option1\<> /\<option2> / option#>. Tento parametr slouží k určení možností příkazového řádku, které nejsou reprezentovány žádným jiným parametrem úlohy MIDL.

     Další informace naleznete v [tématu ODKAZ NA PŘÍKAZOVÝ ŘÁDEK MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ApplicationConfigurationMode**

     Volitelný **logický** parametr.

     Pokud `true`umožňuje použít některá klíčová slova ACF v souboru IDL.

     Další informace naleznete v tématu **/app_config** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Soubor ClientStubFile**

     Volitelný **parametr String.**

     Určuje název souboru se zakázaným inzerováním klienta pro rozhraní vzdáleného volání procedur.

     Další informace naleznete v tématu **/cstub** možnost v [MIDL příkaz-line odkaz](/windows/desktop/Midl/midl-command-line-reference). Viz také parametr **ServerStubFile** v této tabulce.

- **CPreprocessMožnosti**

     Volitelný **parametr String.**

     Určuje možnosti, které mají být předávány preprocesoru C/C++. Zadejte seznam možností preprocesoru oddělený mezerami.

     Další informace naleznete v tématu **/cpp_opt** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **DefaultCharType**

     Volitelný **parametr String.**

     Určuje výchozí typ znaku, který kompilátor Jazyka C použije ke kompilaci generovaného kódu.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Podepsané**|**/char podepsáno**|
    |**Nepodepsané**|**/char nepodepsané**|
    |**Ascii**|**/char ascii7**|

     Další informace naleznete v tématu **/char** možnost v [MIDL příkazový řádek odkaz](/windows/desktop/Midl/midl-command-line-reference).

- **DllDataFileName**

     Volitelný **parametr String.**

     Určuje název souboru generovaného *souboru dlldata* pro proxy dll.

     Další informace naleznete v tématu **/dlldata** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference).

- **EnableErrorChecks**

     Volitelný **parametr String.**

     Určuje typ kontroly chyb, které budou generované zástupné procedury provádět za běhu.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Žádné**|**/chyba žádná**|
    |**EnableCustom**|**/chyba**|
    |**Všechny**|**/chyba všechny**|

     Další informace naleznete v tématu **/error** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckAllocations**

     Volitelný **logický** parametr.

     Pokud `true`zkontrolujte chyby nedostatku paměti.

     Další informace naleznete v tématu **/error allocation** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckBounds**

     Volitelný **logický** parametr.

     Pokud `true`, zkontroluje velikost konformní-měnit a různé pole proti specifikaci délky přenosu.

     Další informace naleznete v možnosti **/error bounds_check** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckEnumRange**

     Volitelný **logický** parametr.

     Pokud `true`, zkontroluje, zda jsou hodnoty výčtu v povoleném rozsahu.

     Další informace naleznete v možnosti **/error výčtu** v nápovědě příkazového řádku (**/?**) pro *midl.exe*.

- **ChybaKontrolní refři**

     Volitelný **logický** parametr.

     Pokud `true`zkontrolujte, zda žádné ukazatele nulového odkazu jsou předány zástupné procedury klienta.

     Další informace naleznete v odkazu na **příkazový** řádek kláves /error v [příkazovém řádku MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckStubData**

     Volitelný **logický** parametr.

     Pokud `true`aplikace vygeneruje se zakázaným inzerováním, který zachytí výjimky unmarshaling na straně serveru a rozšíří je zpět klientovi.

     Další informace naleznete v tématu **/error stub_data** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Generovat soubory klienta**

     Volitelný **parametr String.**

     Určuje, zda kompilátor generuje zdrojové soubory C na straně klienta pro rozhraní Vzdáleného volání procedur.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Žádné**|**/klient žádný**|
    |**Se zakázaným inzerováním**|**/zástupný kód klienta**|

     Další informace naleznete v tématu **/client** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateServerFiles**

     Volitelný **parametr String.**

     Určuje, zda kompilátor generuje zdrojové soubory C na straně serveru pro rozhraní Vzdáleného volání procedur.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Žádné**|**/server žádný**|
    |**Se zakázaným inzerováním**|**/server se zakázaným inzerováním**|

     Další informace naleznete v možnosti **/server** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateStubless Proxies**

     Volitelný **logický** parametr.

     Pokud `true`, generuje plně interpretované zástupné procedury spolu se zástupnými kódy bez útržku pro rozhraní objektů.

     Další informace naleznete v tématu **/Oicf** možnost v [MIDL příkazový řádek odkaz](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateTypeLibrary**

     Volitelný **logický** parametr.

     Pokud `true`není generován soubor knihovny typů (*TLB*).

     Další informace naleznete v tématu **/notlb** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference).

- **Název souboru záhlaví**

     Volitelný **parametr String.**

     Určuje název generovaného souboru záhlaví.

     Další informace naleznete v tématu **/h** nebo **/header** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Ignorovat cestu standardních zahrnutí**

     Volitelný **logický** parametr.

     Pokud `true`úloha MIDL prohledá pouze adresáře určené pomocí **přepínače AdditionalIncludeDirectories** a ignoruje aktuální adresář a adresáře určené proměnnou prostředí INCLUDE.

     Další informace naleznete v možnosti **/no_def_idir** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Název_souboru_rozhraní**

     Volitelný **parametr String.**

     Určuje název *souboru identifikátoru rozhraní rozhraní* COM. Tím přepíšete výchozí název získaný přidáním "_i.c" k názvu souboru IDL.

     Další informace naleznete v **možnosti /iid** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Localeid**

     Volitelný **parametr int.**

     Určuje *identifikátor národního prostředí,* který umožňuje použití mezinárodních znaků ve vstupních souborech, názvech souborů a cestách adresářů. Zadejte identifikátor desetinného národního prostředí.

     Další informace naleznete v tématu **/lcid** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference). Viz také [identifikátory národního prostředí](/windows/desktop/intl/locale-identifiers).

- **Kompatibilní s MkTypLib**

     Volitelný **logický** parametr.

     Pokud `true`, vyžaduje, aby byl formát vstupního souboru kompatibilní s *mktyplib.exe* verze 2.03.

     Další informace naleznete v tématu **/mktyplib203** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také [syntaxe souboru ODL](/previous-versions/windows/desktop/automat/odl-file-syntax) na webu MSDN.

- **Výstupní adresář**

     Volitelný **parametr String.**

     Určuje výchozí adresář, ve kterém úloha MIDL zapisuje výstupní soubory.

     Další informace naleznete v možnosti **/out** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Definice preprocesoru**

     Volitelný **parametr String[].**

     Určuje jednu nebo více *definic*; to znamená, že název a volitelná hodnota, která má `#define` být předána preprocesoru C, jako by byla direktivou. Forma každého define je, *name[=value]*.

     Další informace naleznete v možnosti **/D** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také parametr **UndefinePreprocessorDefinitions** v této tabulce.

- **Název_proxy souboru**

     Volitelný **parametr String.**

     Určuje název souboru proxy rozhraní pro rozhraní COM.

     Další informace naleznete v možnosti **/proxy** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **RedirectOutputAndErrors**

     Volitelný **parametr String.**

     Přesměruje výstup, například chybové zprávy a upozornění, ze standardního výstupu na zadaný soubor.

     Další informace naleznete v možnosti **/o** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Soubor ServerStubFile**

     Volitelný **parametr String.**

     Určuje název souboru se zakázaným inzerováním serveru pro rozhraní vzdáleného volání procedur.

     Další informace naleznete v tématu **/sstub** možnost v [midl příkaz-line odkaz](/windows/desktop/Midl/midl-command-line-reference). Také naleznete **parametr ClientStubFile** v této tabulce.

- **Zdroj**

     Požadovaný parametr `ITaskItem[]`.

     Určuje seznam zdrojových souborů oddělených mezerami.

- **StructMemberAlignment**

     Volitelný **parametr String.**

     Určuje trasu (*úroveň balení*) konstrukcí v cílovém systému.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Notset**|*\<žádný>*|
    |**1**|**/Zp1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/Zp8**|

     Další informace naleznete v tématu **/Zp** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference). Možnost **/Zp** je ekvivalentní možnosti **/pack** a starší možnost **/align.**

- **Potlačení upozornění na kompilátor**

     Volitelný **logický** parametr.

     Pokud `true`potlačí varovné zprávy z úlohy MIDL.

     Další informace naleznete v tématu **/no_warn** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **PotlačitStartupBanner**

     Volitelný `Boolean` parametr.

     Pokud `true`aplikace zabraňuje zobrazení zprávy o autorských právech a čísle verze při spuštění úlohy.

     Další informace naleznete v tématu **/nologo** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference).

- **TargetEnvironment**

     Volitelný **parametr String.**

     Určuje prostředí, ve kterém je aplikace spuštěna.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Notset**|*\<žádný>*|
    |**Win32**|**/env win32**|
    |**Itanium**|**/env ia64**|
    |**X64**|**/env x64**|

     Další informace naleznete v možnosti **/env** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **TrackerLogDirectory**

     Volitelný `String` parametr.

     Určuje zprostředkující adresář, ve kterém jsou uloženy protokoly sledování pro tuto úlohu.

- **TypeLibFormat**

     Volitelný **parametr String.**

     Určuje formát souboru knihovny typů.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**Nový formát**|**/newtlb**|
    |**Starý formát**|**/oldtlb**|

     Další informace naleznete v možnostech **/newtlb** a **/oldtlb** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **TypeLibraryName**

     Volitelný **parametr String.**

     Určuje název souboru knihovny typů.

     Další informace naleznete v tématu **/tlb** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference).

- **UndefinePreprocessorDefinitions UndefinePreprocessorDefinitions UndefinePreprocessorDefinitions Undefine**

     Volitelný **parametr String[].**

     Odebere všechny předchozí definice názvu předáním názvu preprocesoru C, jako by direktivou. `#undefine` Zadejte jeden nebo více dříve definovaných názvů.

     Další informace naleznete v možnosti **/U** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také parametr **PreprocessorDefinitions** v této tabulce.

- **Ověřit všechny parametry**

     Volitelný `Boolean` parametr.

     Pokud `true`, generuje další informace o kontrole chyb, které se používají k provádění kontrol integrity za běhu. Pokud `false`nejsou generovány informace o kontrole chyb.

     Další informace naleznete v možnostech **/robust** a **/no_robust** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Chyba WarnAs**

     Volitelný `Boolean` parametr.

     Pokud `true`, považuje všechna upozornění za chyby.

     Pokud není zadán parametr úlohy **WarningLevel** MIDL, upozornění na výchozí úrovni, úroveň 1, jsou považována za chyby.

     Další informace naleznete v možnostech **/WX** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také Parametr **WarningLevel** v této tabulce.

- **Úroveň upozornění**

     Volitelný **parametr String.**

     Určuje závažnost *(úroveň upozornění)* upozornění, která mají být emitována. Pro hodnotu 0 není vyzařováno žádné upozornění. V opačném případě je vyzařováno upozornění, pokud je jeho úroveň upozornění číselně menší nebo rovna zadané hodnotě.

     Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.

    |Hodnota|Možnost příkazového řádku|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     Další informace naleznete v možnosti **/W** v [odkazu na příkazový řádek MIDL](/windows/desktop/Midl/midl-command-line-reference). Viz také parametr **WarnAsError** v této tabulce.

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
