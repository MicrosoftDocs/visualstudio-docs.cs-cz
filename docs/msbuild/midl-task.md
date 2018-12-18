---
title: MIDL – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1affc4d84b8ea44cbaed51f656c8a3e97e04f97a
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219806"
---
# <a name="midl-task"></a>MIDL – úloha
Zabalí nástroj kompilátoru Microsoft Interface Definition Language (MIDL) *midl.exe*. Další informace najdete v tématu [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
## <a name="parameters"></a>Parametry  
 Následující text popisuje parametry **MIDL** úloh. Většinu úkolů parametrů a několik sad parametrů, odpovídají možnost příkazového řádku.  
  
-   **AdditionalIncludeDirectories**  
  
     Volitelné **String []** parametru.  
  
     Přidá adresář na seznam adresářů, které se vyhledávají importované soubory IDL zahrnuté hlavičkové soubory a konfigurační soubory aplikace (ACF).  
  
     Další informace najdete v tématu **/I** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **AdditionalOptions**  
  
     Volitelné **řetězec** parametru.  
  
     Seznam možností příkazového řádku. Třeba /\<možnost1 > /\<možnost2 > /\<možnost #>. Tento parametr použijte k určení možnosti příkazového řádku, které nejsou reprezentovány všechny ostatní parametry MIDL – úloha.  
  
     Další informace najdete v tématu [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ApplicationConfigurationMode**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, vám umožní používat některé klíčová slova ACF v souboru IDL.  
  
     Další informace najdete v tématu **/app_config** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ClientStubFile**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název souboru zástupné procedury klienta pro rozhraní RPC.  
  
     Další informace najdete v tématu **/cstub** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Viz také **ServerStubFile** parametr v této tabulce.  
  
-   **CPreprocessOptions**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje možnosti, které chcete předat preprocesoru C/C++. Zadejte seznam možnosti preprocesoru oddělených mezerami.  
  
     Další informace najdete v tématu **/cpp_opt** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **DefaultCharType**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje výchozí znakový typ kompilátoru jazyka C bude používat pro kompilaci vygenerovaného kódu.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**podepsané**|**/ Char podepsané**|  
    |**bez znaménka**|**/ Char unsigned**|  
    |**ASCII**|**/char ascii7**|  
  
     Další informace najdete v tématu **/char** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **DllDataFileName**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název souboru pro vygenerovaný *dlldata* soubor pro proxy server knihovny DLL.  
  
     Další informace najdete v tématu **/dlldata** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **EnableErrorChecks**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje typ Chyba při kontrole, že generované zástupné procedury provede v době běhu.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**None**|**/ Error none**|  
    |**EnableCustom**|**/ Error**|  
    |**Všechny**|**/ Error všechny**|  
  
     Další informace najdete v tématu **/Error** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ErrorCheckAllocations**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, zkontrolujte chyby na více instancí z důvodu nedostatku paměti.  
  
     Další informace najdete v tématu **/Error allocation** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ErrorCheckBounds**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, kontroluje velikost s různými splňující podmínky a různých polí proti specifikací délky přenosu.  
  
     Další informace najdete v tématu **/Error bounds_check** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ErrorCheckEnumRange**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, zkontroluje, zda jsou hodnoty výčtu v povoleném rozmezí.  
  
     Další informace najdete v tématu **/Error enum** možnost Nápověda příkazového řádku (**/?**) pro *midl.exe*.  
  
-   **ErrorCheckRefPointers**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, zkontrolujte, zda klienta zástupné procedury jsou předány žádné ukazatele odkaz s hodnotou null.  
  
     Další informace najdete v tématu **/Error ref** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ErrorCheckStubData**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, generuje zástupnou proceduru, která zachytává unmarshaling výjimky na straně serveru a šíří je zpět do klienta.  
  
     Další informace najdete v tématu **/Error stub_data** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **GenerateClientFiles**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje, zda kompilátor generuje zdrojových souborů C na straně klienta pro rozhraní RPC.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**None**|**/ Client none**|  
    |**Zástupné procedury**|**Zástupná procedura/Client**|  
  
     Další informace najdete v tématu **/Client** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **GenerateServerFiles**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje, zda kompilátor generuje zdrojových souborů C na straně serveru v rámci rozhraní RPC.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**None**|**/ Server žádné**|  
    |**Zástupné procedury**|**Zástupná Procedura/Server**|  
  
     Další informace najdete v tématu **/server** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **GenerateStublessProxies**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, generuje plně interpretované zástupné procedury spolu s proxy bez zástupných procedur pro rozhraní objektů.  
  
     Další informace najdete v tématu **/oicf** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **GenerateTypeLibrary**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, knihovnu typů (*.tlb*) soubor.  
  
     Další informace najdete v tématu **/notlb** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **HeaderFileName**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název vygenerovaného souboru hlavičky.  
  
     Další informace najdete v tématu **/h** nebo **/header** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **IgnoreStandardIncludePath**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, MIDL – úloha v adresářích jenom určené vlastností **AdditionalIncludeDirectories** přepnutí a bude ignorovat aktuální adresář a adresáře určené proměnnou prostředí INCLUDE.  
  
     Další informace najdete v tématu **/no_def_idir** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **InterfaceIdentifierFileName**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název *souboru identifikátoru rozhraní* pro rozhraní modelu COM. Tím se přepíše výchozí název, získat tak, že přidáte "_i.c" k názvu souboru IDL.  
  
     Další informace najdete v tématu **/iid** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **Identifikátor národního prostředí**  
  
     Volitelné **int** parametru.  
  
     Určuje, *identifikátor národního prostředí* , který umožňuje použití mezinárodní znaky ve vstupních souborů, názvy souborů a cesty k adresářům. Zadejte identifikátor desítkové národního prostředí.  
  
     Další informace najdete v tématu **/LCID** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Viz také [identifikátory národního prostředí](https://docs.microsoft.com/windows/desktop/intl/locale-identifiers).  
  
-   **MkTypLibCompatible**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, vyžaduje formát vstupního souboru, aby byl kompatibilní s *mktyplib.exe* verze 2.03 nástroje MkTypLib.exe.  
  
     Další informace najdete v tématu **/mktyplib203** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Viz také [syntaxi souboru ODL](/previous-versions/windows/desktop/automat/odl-file-syntax) na webu MSDN.  
  
-   **OutputDirectory**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje výchozí adresář, ve kterém MIDL – úloha zapíše výstupní soubory.  
  
     Další informace najdete v tématu **/out** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **PreprocessorDefinitions**  
  
     Volitelné **String []** parametru.  
  
     Určuje jeden nebo více *definuje*; to znamená, názvu a které se mají předat preprocesoru C jako volitelná hodnota if podle `#define` směrnice. Každá definice má hodnotu, *[= value] název*.  
  
     Další informace najdete v tématu **/D** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Další informace naleznete **UndefinePreprocessorDefinitions** parametr v této tabulce.  
  
-   **ProxyFileName**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název souboru proxy rozhraní pro rozhraní modelu COM.  
  
     Další informace najdete v tématu **/proxy** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **RedirectOutputAndErrors**  
  
     Volitelné **řetězec** parametru.  
  
     Přesměruje výstup, jako je například chybové zprávy a upozornění z standardní výstup do zadaného souboru.  
  
     Další informace najdete v tématu **/o** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **ServerStubFile**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název souboru serveru zástupných procedur pro rozhraní RPC.  
  
     Další informace najdete v tématu **/sstub** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Další informace naleznete **ClientStubFile** parametr v této tabulce.  
  
-   **Zdroj**  
  
     Vyžaduje `ITaskItem[]` parametru.  
  
     Určuje seznam zdrojových souborů, oddělené mezerami.  
  
-   **StructMemberAlignment**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje zarovnání (*balení úroveň*) struktur v cílovém systému.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**Nenastaveno**|*\<žádné >*|  
    |**1**|**/Zp1**|  
    |**2**|**/Zp2**|  
    |**4**|**/Zp4**|  
    |**8**|**/Zp8**|  
  
     Další informace najdete v tématu **/zp** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). **/Zp** možnost je ekvivalentní **/pack** možnost a starší **/ align** možnost.  
  
-   **SuppressCompilerWarnings**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, potlačí zprávy upozornění z MIDL – úloha.  
  
     Další informace najdete v tématu **/no_warn** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **SuppressStartupBanner**  
  
     Volitelné `Boolean` parametru.  
  
     Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.  
  
     Další informace najdete v tématu **/nologo** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **TargetEnvironment**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje prostředí, ve kterém je aplikace spuštěná.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**Nenastaveno**|*\<žádné >*|  
    |**Win32**|**/ env win32**|  
    |**Itanium**|**/ env ia64**|  
    |**X64**|**/env x64**|  
  
     Další informace najdete v tématu **/env** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **TrackerLogDirectory**  
  
     Volitelné `String` parametru.  
  
     Určuje zprostředkující adresář, kde jsou uloženy protokoly sledování pro tuto úlohu.  
  
-   **TypeLibFormat**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje formát souboru knihovny typů.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**NewFormat**|**/newtlb**|  
    |**OldFormat**|**/oldtlb**|  
  
     Další informace najdete v tématu **/newtlb** a **/oldtlb** možnosti [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **TypeLibraryName**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje název souboru knihovny typů.  
  
     Další informace najdete v tématu **/TLB** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Volitelné **String []** parametru.  
  
     Odebere všechny předchozí definice názvu předáním názvu pro preprocesor C jako if podle `#undefine` směrnice. Zadejte jeden nebo více dříve definované názvy.  
  
     Další informace najdete v tématu **/U** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Další informace naleznete **PreprocessorDefinitions** parametr v této tabulce.  
  
-   **ValidateAllParameters**  
  
     Volitelné `Boolean` parametru.  
  
     Pokud `true`, vygeneruje další kontrolu chyb informace, které slouží k provádění kontrol integrity za běhu. Pokud `false`, kontrolu chyb informace se nevygeneroval.  
  
     Další informace najdete v tématu **/ robust** a **/no_robust** možnosti [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).  
  
-   **WarnAsError**  
  
     Volitelné `Boolean` parametru.  
  
     Pokud `true`, zpracuje všechna upozornění jako chyby.  
  
     Pokud **WarningLevel** MIDL – úloha parametr není zadán, upozornění na výchozí úrovni úrovně 1, jsou považována za chyby.  
  
     Další informace najdete v tématu **/WX** možnosti [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Další informace naleznete **WarningLevel** parametr v této tabulce.  
  
-   **WarningLevel**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje závažnost (*úroveň pro upozornění*) ke generování upozornění. Bez upozornění je vygenerován pro hodnotu 0. V opačném případě je aktivováno upozornění, pokud jeho úroveň pro upozornění je číselně menší nebo rovna zadané hodnotě.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.  
  
    |Hodnota|Možnost příkazového řádku|  
    |-----------|--------------------------|  
    |**0**|**/W0**|  
    |**1**|**/W1**|  
    |**2**|**/W2**|  
    |**3**|**/W3**|  
    |**4**|**/W4**|  
  
     Další informace najdete v tématu **/W** možnost [příkazového řádku MIDL odkazu](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Další informace naleznete **WarnAsError** parametr v této tabulce.  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)