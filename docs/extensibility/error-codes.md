---
title: Chybové kódy | Microsoft Docs
description: Tento článek obsahuje seznam chybových kódů, hodnot a popisů pro funkce rozhraní API modulu plug-in správy zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 32557b2a476be9f662decc9992771fe359967a94
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070164"
---
# <a name="error-codes"></a>Kódy chyb
Pokud funkce rozhraní API modulu plug-in správy zdrojových kódů vrátí chybu, bude se jednat o jeden z následujících kódů chyb. Všechny chyby jsou záporné, upozornění nebo informativní chybové kódy jsou kladné a úspěch je 0.

|Kód chyby|Hodnota|Popis|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Modul plug-in podporuje přidávání souborů ze správy zdrojového kódu ve dvou krocích. Další informace najdete v tématu [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Místní soubor se liší od souboru v databázi správy zdrojů (například [SccDiff](../extensibility/sccdiff-function.md) může vracet tuto hodnotu).|
|`SCC_I_RELOADFILE`|5|Místní soubor byl během operace správy zdrojových kódů změněn; Pokud je to možné, by IDE měl soubor znovu načíst.|
|`SCC_I_FILENOTAFFECTED`|4|Soubor není ovlivněn.|
|`SCC_I_PROJECTCREATED`|3|Projekt byl vytvořen během operace správy zdrojových kódů (například během volání [SccOpenProject](../extensibility/sccopenproject-function.md) při `SCC_OP_CREATEIFNEW` zadání příznaku).|
|`SCC_I_OPERATIONCANCELED`|2|Operace byla zrušena.|
|`SCC_I_ADV_SUPPORT`|1|Modul plug-in podporuje rozšířené možnosti pro zadaný příkaz. Další informace najdete v tématu [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Úspěch.|
|`SCC_E_INITIALIZEFAILED`|-1|Chyba: inicializace se nezdařila.|
|`SCC_E_UNKNOWNPROJECT`|-2|Chyba: projekt je neznámý.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Chyba: projekt nelze vytvořit.|
|`SCC_E_NOTCHECKEDOUT`|-4|Chyba: soubor není rezervován.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Chyba: soubor je již rezervován.|
|`SCC_E_FILEISLOCKED`|-6|Chyba: soubor je uzamčen.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Chyba: soubor je exkluzivně zaregistrován.|
|`SCC_E_ACCESSFAILURE`|-8|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|`SCC_E_CHECKINCONFLICT`|-9|Chyba: během vracení se změnami došlo ke konfliktu.|
|`SCC_E_FILEALREADYEXISTS`|-10|Chyba: soubor již existuje.|
|`SCC_E_FILENOTCONTROLLED`|-11|Chyba: soubor není pod správou zdrojových kódů.|
|`SCC_E_FILEISCHECKEDOUT`|– 12|Chyba: soubor je rezervován.|
|`SCC_E_NOSPECIFIEDVERSION`|– 13|Chyba: není určena žádná verze.|
|`SCC_E_OPNOTSUPPORTED`|– 14|Chyba: operace není podporována.|
|`SCC_E_NONSPECIFICERROR`|-15|Nespecifická chyba|
|`SCC_E_OPNOTPERFORMED`|– 16|Chyba: operace nebyla provedena.|
|`SCC_E_TYPENOTSUPPORTED`|– 17|Chyba: typ souboru, například Binary, není podporován systémem správy zdrojového kódu.|
|`SCC_E_VERIFYMERGE`|-18|Soubor byl automaticky sloučen, ale nebyl zkontrolován, protože čeká na ověření uživatele.|
|`SCC_E_FIXMERGE`|– 19|Soubor byl automaticky sloučen, ale nebyl vrácen se změnami z důvodu konfliktu sloučení, který je nutné ručně vyřešit.|
|`SCC_E_SHELLFAILURE`|-20|Chyba v důsledku selhání prostředí.|
|`SCC_E_INVALIDUSER`|– 21|Chyba: uživatel je neplatný.|
|`SCC_E_PROJECTALREADYOPEN`|– 22|Chyba: projekt je již otevřen.|
|`SCC_E_PROJSYNTAXERR`|-23|Chyba syntaxe projektu|
|`SCC_E_INVALIDFILEPATH`|– 24|Chyba: cesta k souboru je neplatná.|
|`SCC_E_PROJNOTOPEN`|-25|Chyba: projekt není otevřen.|
|`SCC_E_NOTAUTHORIZED`|– 26|Chyba: uživatel nemá oprávnění k provedení této operace.|
|`SCC_E_FILESYNTAXERR`|– 27|Chyba syntaxe souboru|
|`SCC_E_FILENOTEXIST`|– 28|Chyba: místní soubor neexistuje.|
|`SCC_E_CONNECTIONFAILURE`|– 29|Chyba: došlo k chybě připojení.|
|`SCC_E_UNKNOWNERROR`|-30|Neznámou chybu.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|– 31|Právě probíhá operace Get elementu Background.|

## <a name="macros-provided-for-quick-checking"></a>Makra, která jsou k dispozici pro rychlou kontrolu

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Poznámky
 Všechny funkce rozhraní API modulu plug-in správy zdrojového kódu (s výjimkou [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)a [SccDiff](../extensibility/sccdiff-function.md)) mají být úspěšné, pokud místní soubory, které jsou předány jako argumenty, v pracovní složce neexistují. Rozhraní IDE může například vydávat volání [SccCheckout](../extensibility/scccheckout-function.md) nebo [SccUncheckout](../extensibility/sccuncheckout-function.md) na soubor, který neexistuje v pracovní složce, ale existuje v systému správy zdrojového kódu. Toto volání by bylo úspěšné. Pouze v případě, že v pracovní složce nebo v systému správy zdrojů není žádný soubor, je funkce očekávat selhání.

 Některé funkce, jako například `SccAdd` a `SccCheckin` , by měly vracet konkrétně `SCC_E_FILENOTEXIST` v případě, že soubor v pracovní složce neexistuje. Pokud funkce pracují s platným názvem souboru v systému správy zdrojového kódu, očekává se, že další funkce budou úspěšné, pokud pracovní soubor neexistuje.

 Modul plug-in správy zdrojových kódů by neměl vytvářet předpoklady týkající se oprávnění k souboru v pracovní složce, a to ani v případě, že modul plug-in v průběhu nějaké operace označil soubor jen pro čtení. Soubor v pracovní složce se dá přesunout, odstranit a změnit mimo ovládací prvek modulu plug-in.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
