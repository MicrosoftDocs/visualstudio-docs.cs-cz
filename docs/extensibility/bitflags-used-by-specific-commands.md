---
title: Bitové příznaky používané určitými příkazy | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740008"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitové příznaky používané určitými příkazy
Chování několika funkcí v rozhraní plug-in správy zdrojového kódu lze upravit nastavením jednoho nebo více bitů v jedné hodnotě. Tyto hodnoty jsou označovány jako bitové příznaky. Různé bitové příznaky používané rozhraním API modulu plug-in správy zdrojového kódu jsou podrobně popsány podle funkce, která je používá.

## <a name="checked-out-flag"></a>Rezervováno příznak
 Tento příznak lze nastavit buď [pro SccAdd](../extensibility/sccadd-function.md) nebo [SccCheckin](../extensibility/scccheckin-function.md).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Udržujte soubor rezervován.|

## <a name="add-flags"></a>Přidání příznaků
 Tyto příznaky jsou používány [SccAdd](../extensibility/sccadd-function.md).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Očekává se, že modul plug-in správy zdrojového kódu automaticky zjistí, zda je soubor textový nebo binární.|
|`SCC_FILETYPE_TEXT`|0x01|Typ souboru je text.|
|`SCC_FILETYPE_BINARY`|0x04|Typ souboru je binární. **Poznámka:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` a vlajky se vzájemně vylučují.   Nastavte přesně jeden nebo jeden.|
|`SCC_ADD_STORELATEST`|0x02|Uložit pouze nejnovější verzi (žádné rozdíly).|

## <a name="diff-flags"></a>Příznaky rozdílů
 [SccDiff](../extensibility/sccdiff-function.md) používá tyto příznaky k definování rozsahu operace diff. Vlajky se `SCC_DIFF_QD_xxx` vzájemně vylučují. Pokud je některý z nich zadán, pak není poskytnuta žádná vizuální zpětná vazba. V "rychlé diff" (QD) modul plug-in neurčuje, jak se soubor liší, pouze v případě, že se liší. Pokud není zadán žádný z těchto příznaků, "vizuální rozdíl" se provádí; jsou vypočítány a zobrazeny podrobné rozdíly v souborech. Pokud požadovaný qd není podporován, modul plug-in se přesune na další nejlepší. Například pokud ide požaduje kontrolní součet a modul plug-in nepodporuje, modul plug-in provádí kontrolu celého obsahu (stále mnohem rychlejší než vizuální zobrazení).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorovat rozdíly v případech.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorovat mezery mezery prázdného místa. **Poznámka:**  A `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` příznaky jsou volitelné bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD porovnáním celého obsahu souboru.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD kontrolním součtem.|
|`SCC_DIFF_QD_TIME`|0x0040|QD podle data a časového razítka souboru.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Toto je maska slouží ke kontrole všech QD bitflags. Neměl by být předán do funkce; tři QD bitflagy se vzájemně vylučují. QD vždy znamená žádné zobrazení uI.|

## <a name="populatelist-flag"></a>Příznak Naplnit list
 Tento příznak je používán [SccPopulateList](../extensibility/sccpopulatelist-function.md) v parametru. `fOptions`

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE je předávání adresářů, nikoli soubory.|

## <a name="populatedirlist-flags"></a>Příznaky PopulateDirList
 Tyto příznaky jsou používány [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) v parametru. `fOptions`

|Hodnota možnosti|Hodnota|Popis|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Zkontrolujte pouze jednu úroveň adresářů pro adresáře (toto je výchozí).|
|SCC_PDL_RECURSIVE|0x0001|Rekurzivně zkontrolujte všechny adresáře v rámci každého daného adresáře.|
|SCC_PDL_INCLUDEFILES|0x0002|Zahrnout názvy souborů do procesu kontroly.|

## <a name="openproject-flags"></a>Příznaky OpenProject
 Tyto příznaky jsou používány [SccOpenProject](../extensibility/sccopenproject-function.md) v parametru. `dwFlags`

|Hodnota možnosti|Hodnota|Popis|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Pokud projekt neexistuje ve správě zdrojového kódu, vytvořte jej. Pokud tento příznak není nastaven, vyzve uživatele `SCC_OP_SILENTOPEN` k vytvoření projektu (pokud není zadán příznak).|
|SCC_OP_SILENTOPEN|0x00000002L|Nezobrazovat výzvu uživateli k vytvoření projektu. stačí `SCC_E_UNKNOWNPROJECT`vrátit .|

## <a name="get-flags"></a>Získání příznaků
 Tyto příznaky jsou používány [SccGet](../extensibility/sccget-function.md) a [SccCheckout](../extensibility/scccheckout-function.md).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE je předávání adresářů, nikoli soubory: Získat všechny soubory v těchto adresářích.|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE prochází adresáře: Získejte tyto adresáře a všechny jejich podadresáře.|

## <a name="noption-values"></a>nHodnoty Option
 Tyto příznaky jsou používány [SccSetOption](../extensibility/sccsetoption-function.md) v parametru. `nOption`

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Nastavte stav fronty událostí.|
|`SCC_OPT_USERDATA`|0x00000002L|Zadejte uživatelská data pro . `SCC_OPT_NAMECHANGEPFN`|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE může zpracovat zrušit.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Nastavte zpětné volání pro změny názvů.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Zakažte pokladnu modulu plug-in správy zdrojového kódu a nenastavujte pracovní adresář.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Přidejte ze systému správy zdrojového kódu a určete pracovní adresář. Pokuste se sdílet do přidruženého projektu, pokud je přímým potomkem.|

## <a name="dwval-bitflags"></a>dwVal bitové vlajky
 Tyto příznaky jsou používány [SccSetOption](../extensibility/sccsetoption-function.md) v parametru. `dwVal`

|Příznak|Hodnota|Popis|Používá `nOption` se podle hodnoty|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Pozastaví aktivitu fronty událostí.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Povolí protokolování fronty událostí.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Výchozí) Nemá žádný režim zrušení; v případě potřeby musí být dodávek.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|Popisovače ide zrušit.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Výchozí) OK se podívat z plug-in uI; je nastaven pracovní adresář.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Žádná pokladna plug-in ui, žádný pracovní adresář.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Viz také
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
