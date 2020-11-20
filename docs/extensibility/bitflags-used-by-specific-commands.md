---
title: Bitflags používané konkrétními příkazy | Microsoft Docs
description: Přečtěte si informace o bitflags, které používá rozhraní API modulu plug-in správy zdrojového kódu, uspořádané podle funkce, která je používá.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7c6c48dbad986d8bc4be58f1ebd9c5bd1fffbd57
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974592"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags používané konkrétními příkazy
Chování řady funkcí v rozhraní API modulu plug-in správy zdrojového kódu lze upravit nastavením jedné nebo více bitů v rámci jedné hodnoty. Tyto hodnoty se označují jako bitflags. Různé bitflags, které používá rozhraní API modulu plug-in správy zdrojových kódů, jsou zde popsány seskupeny podle funkce, která je používá.

## <a name="checked-out-flag"></a>Příznak rezervace
 Tento příznak lze nastavit buď pro [SccAdd](../extensibility/sccadd-function.md) , nebo pro [SccCheckin](../extensibility/scccheckin-function.md).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Ponechte soubor zarezervován.|

## <a name="add-flags"></a>Přidat příznaky
 Tyto příznaky používá [SccAdd](../extensibility/sccadd-function.md).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Je očekáván modul plug-in správy zdrojových kódů, který automaticky zjišťuje, zda je soubor textový nebo binární.|
|`SCC_FILETYPE_TEXT`|0x01|Typ souboru je text.|
|`SCC_FILETYPE_BINARY`|0x04|Typ souboru je binární. **Poznámka:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY`příznaky a se vzájemně vylučují.   Nastavte přesně jednu nebo žádnou.|
|`SCC_ADD_STORELATEST`|0x02|Uloží pouze nejnovější verzi (žádné rozdíly).|

## <a name="diff-flags"></a>Rozdílové příznaky
 [SccDiff](../extensibility/sccdiff-function.md) používá tyto příznaky k definování rozsahu rozdílové operace. `SCC_DIFF_QD_xxx`Příznaky se vzájemně vylučují. Pokud je některý z nich zadaný, nemusíte mít žádnou vizuální zpětnou vazbu. V "rychlém rozdílu" (hloubka fronty) modul plug-in neurčuje, jak se soubor liší, pouze pokud se liší. Pokud není zadán žádný z těchto příznaků, je provedeno "rozdíly v vizuálů"; Podrobné rozdíly v souborech se vypočítávají a zobrazují. Pokud požadovaný hloubka fronty není podporovaný, modul plug-in se přesune na další nejlepší. Například pokud rozhraní IDE požaduje kontrolní součet a modul plug-in ho nepodporuje, modul plug-in provede kontrolu celého obsahu (stále mnohem rychlejší než vizuální zobrazení).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorovat rozdíly v malých a velkých písmenech|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorujte rozdíly na prázdných prostorech. **Poznámka:**  `SCC_DIFF_IGNORECASE` Příznaky a `SCC_DIFF_IGNORESPACE` jsou volitelné bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|Hloubka fronty porovnáním celého obsahu souboru.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|Hloubka fronty podle kontrolního součtu.|
|`SCC_DIFF_QD_TIME`|0x0040|Hloubka fronty podle razítka data a času souboru.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Toto je maska, která slouží ke kontrole všech hloubka fronty bitflags. Neměl by být předán do funkce. tři hloubka fronty bitflags se vzájemně vylučují. Hloubka fronty vždy znamená bez zobrazení uživatelského rozhraní.|

## <a name="populatelist-flag"></a>Příznak PopulateList
 Tento příznak používá [SccPopulateList](../extensibility/sccpopulatelist-function.md) v `fOptions` parametru.

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|Rozhraní IDE odesílá adresáře, nikoli soubory.|

## <a name="populatedirlist-flags"></a>Příznaky PopulateDirList
 Tyto příznaky jsou používány [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) v `fOptions` parametru.

|Hodnota možnosti|Hodnota|Popis|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Prověřte pouze jednu úroveň adresářů adresářů (Jedná se o výchozí nastavení).|
|SCC_PDL_RECURSIVE|0x0001|Rekurzivně prověřte všechny adresáře pod každým daným adresářem.|
|SCC_PDL_INCLUDEFILES|0x0002|Do procesu kontroly zahrňte názvy souborů.|

## <a name="openproject-flags"></a>Příznaky OpenProject
 Tyto příznaky jsou používány [SccOpenProject](../extensibility/sccopenproject-function.md) v `dwFlags` parametru.

|Hodnota možnosti|Hodnota|Popis|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Pokud projekt ve správě zdrojového kódu neexistuje, vytvořte ho. Pokud tento příznak není nastavený, vyzvat uživatele k vytvoření pro projekt (Pokud `SCC_OP_SILENTOPEN` není zadaný příznak).|
|SCC_OP_SILENTOPEN|0x00000002L|Nedotazovat uživatele na vytvoření projektu; stačí vrátit `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Získat příznaky
 Tyto příznaky jsou používány [SccGet](../extensibility/sccget-function.md) a [SccCheckout](../extensibility/scccheckout-function.md).

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|Rozhraní IDE předává adresáře, nikoli soubory: načte všechny soubory v těchto adresářích.|
|`SCC_GET_RECURSIVE`|0x00000002L|Rozhraní IDE předává adresáře: získat tyto adresáře a všechny jejich podadresáře.|

## <a name="noption-values"></a>hodnoty nOption
 Tyto příznaky jsou používány [SccSetOption](../extensibility/sccsetoption-function.md) v `nOption` parametru.

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Nastavte stav fronty událostí.|
|`SCC_OPT_USERDATA`|0x00000002L|Zadejte uživatelská data pro `SCC_OPT_NAMECHANGEPFN` .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|Rozhraní IDE může zpracovat zrušení.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Nastavte zpětné volání pro změny názvu.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Zakáže registraci uživatelského rozhraní modulu plug-in správy zdrojových kódů a nenastaví pracovní adresář.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Přidejte ze systému správy zdrojového kódu, abyste určili pracovní adresář. Zkuste sdílet do přidruženého projektu, pokud se jedná o přímého následníka.|

## <a name="dwval-bitflags"></a>dwVal bitflags
 Tyto příznaky jsou používány [SccSetOption](../extensibility/sccsetoption-function.md) v `dwVal` parametru.

|Příznak|Hodnota|Popis|Použito `nOption` hodnotou|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00|Pozastaví činnost fronty událostí.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Povolí protokolování fronty událostí.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|Výchozí Nemá žádný režim zrušení; modul plug-in musí být dodán v případě potřeby.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|Rozhraní IDE zpracovává zrušení.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|Výchozí V případě, že se chcete podívat na uživatelské rozhraní modulu plug-in; pracovní adresář je nastaven.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Žádná rezervace uživatelského rozhraní modulu plug-in, neexistuje pracovní adresář.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
