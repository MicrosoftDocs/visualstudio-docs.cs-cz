---
title: Bitflags used by Specific Commands | Microsoft Docs
description: Přečtěte si o bitflagech používaných rozhraním API modulu plug-in správy zdrojového kódu uspořádaných podle funkce, která je používá.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be5915d96b574336d7091239275a2aaef456a7f3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899364"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflagy používané konkrétními příkazy
Chování několika funkcí v rozhraní API modulu plug-in správy zdrojového kódu je možné upravit nastavením jednoho nebo více bitů v jedné hodnotě. Tyto hodnoty se označuje jako bitflags. Podrobné informace o různých bitflagech používaných rozhraním API modulu plug-in správy zdrojového kódu jsou seskupené podle funkce, která je používá.

## <a name="checked-out-flag"></a>Příznak pro rezervování
 Tento příznak lze nastavit pro [SccAdd](../extensibility/sccadd-function.md) nebo [SccCheckin](../extensibility/scccheckin-function.md).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Nechte soubor zaškrtnut.|

## <a name="add-flags"></a>Přidání příznaků
 Tyto příznaky používá [SccAdd](../extensibility/sccadd-function.md).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Očekává se, že modul plug-in správy zdrojového kódu automaticky zjistí, jestli se jedná o textový nebo binární soubor.|
|`SCC_FILETYPE_TEXT`|0x01|Typ souboru je text.|
|`SCC_FILETYPE_BINARY`|0x04|Typ souboru je binární. **Poznámka:** `SCC_FILETYPE_TEXT` Příznaky `SCC_FILETYPE_BINARY` a se vzájemně vylučují.   Nastavte přesně jednu nebo ani jedno.|
|`SCC_ADD_STORELATEST`|0x02|Ukládat pouze nejnovější verzi (bez rozdílů).|

## <a name="diff-flags"></a>Rozdílové příznaky
 [SccDiff používá](../extensibility/sccdiff-function.md) tyto příznaky k definování oboru rozdílové operace. Příznaky `SCC_DIFF_QD_xxx` se vzájemně vylučují. Pokud je zadán některý z nich, není třeba poskytnout žádnou vizuální zpětnou vazbu. V "rychlém rozdílu" modul plug-in neliší, jak se soubor liší, pouze pokud se liší. Pokud žádný z těchto příznaků není zadaný, je hotový rozdíl vizuálu. Podrobné rozdíly mezi soubory se počítají a zobrazují. Pokud požadovaná technologie QD není podporovaná, modul plug-in přejde na další nejlepší. Pokud například integrované vývojové prostředí požaduje kontrolní součet a modul plug-in ho nepodporuje, modul plug-in zkontroluje celý obsah (stále je mnohem rychlejší než vizuální zobrazení).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorujte rozdíly mezi případy.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorujte rozdíly mezi prázdné znaky. **Poznámka:**  Příznaky `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` a jsou volitelné bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD porovnáním celého obsahu souboru|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD by checksum.|
|`SCC_DIFF_QD_TIME`|0x0040|QD podle data a času souboru.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Toto je maska, která slouží ke kontrole všech bitflagů QD. Neměl by být předán do funkce. Tyto tři bitflagy QD se vzájemně vylučují. QD vždy znamená, že se uživatelské rozhraní nezobrazí.|

## <a name="populatelist-flag"></a>Příznak PopulateList
 Tento příznak používá [SccPopulateList](../extensibility/sccpopulatelist-function.md) v `fOptions` parametru .

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|Integrované vývojové prostředí (IDE) předává adresáře, nikoli soubory.|

## <a name="populatedirlist-flags"></a>Příznaky PopulateDirList
 Tyto příznaky používá [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) v `fOptions` parametru .

|Hodnota možnosti|Hodnota|Popis|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Adresáře zkontrolujte pouze na jedné úrovni adresářů (toto je výchozí nastavení).|
|SCC_PDL_RECURSIVE|0x0001|Rekurzivně prozkoumejte všechny adresáře v každém daném adresáři.|
|SCC_PDL_INCLUDEFILES|0x0002|Zahrnout názvy souborů do procesu zkoumání.|

## <a name="openproject-flags"></a>Příznaky OpenProject
 Tyto příznaky používá projekt [SccOpenProject](../extensibility/sccopenproject-function.md) v `dwFlags` parametru .

|Hodnota možnosti|Hodnota|Popis|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Pokud projekt ve zdrojovém kódu neexistuje, vytvořte ho. Pokud tento příznak není nastavený, vyzve uživatele k vytvoření projektu (pokud `SCC_OP_SILENTOPEN` není zadaný příznak ).|
|SCC_OP_SILENTOPEN|0x00000002L|Nevytázejte uživatele, aby vytvořil projekt. stačí vrátit `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Získání příznaků
 Tyto příznaky používají [SccGet](../extensibility/sccget-function.md) a [SccCheckout](../extensibility/scccheckout-function.md).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|Integrované vývojové prostředí (IDE) předává adresáře, nikoli soubory: Získejte všechny soubory v těchto adresářích.|
|`SCC_GET_RECURSIVE`|0x00000002L|Integrované vývojové prostředí (IDE) předává adresáře: Získejte tyto adresáře a všechny jejich podadresáře.|

## <a name="noption-values"></a>nOption – hodnoty
 Tyto příznaky používá [SccSetOption](../extensibility/sccsetoption-function.md) v `nOption` parametru .

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Nastavte stav fronty událostí.|
|`SCC_OPT_USERDATA`|0x00000002L|Zadejte uživatelská data pro `SCC_OPT_NAMECHANGEPFN` .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|Integrované vývojové prostředí (IDE) může zpracovat zrušení.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Nastavte zpětné volání pro změny názvů.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Zakažte pokladnu uživatelského rozhraní modulu plug-in správy zdrojového kódu a nenastavujte pracovní adresář.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Přidejte ze systému správy zdrojového kódu a zadejte pracovní adresář. Pokud se jedná o přímého potomka, zkuste ho sdílet do přidruženého projektu.|

## <a name="dwval-bitflags"></a>dwVal bitflags
 Tyto příznaky používá [SccSetOption](../extensibility/sccsetoption-function.md) v `dwVal` parametru .

|Příznak|Hodnota|Popis|Používá se `nOption` hodnotou|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Pozastaví aktivitu fronty událostí.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Povolí protokolování fronty událostí.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Výchozí) Nemá žádný režim zrušení. Modul plug-in musí v případě potřeby dodávat.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|Integrované vývojové prostředí zpracovává zrušení.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Výchozí) OK – možnost se můžete podívat z uživatelského rozhraní modulu plug-in. je nastaven pracovní adresář.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Bez pokladny uživatelského rozhraní modulu plug-in, žádný pracovní adresář.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
