---
title: Kódy chyb | Microsoft Docs
description: Tento článek obsahuje seznam kódů chyb, hodnot a popisů pro funkce rozhraní API modulu plug-in správy zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: eedc9311bcafdd4241e065b40079abed3977dcef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898302"
---
# <a name="error-codes"></a>Kódy chyb
Když funkce rozhraní API modulu plug-in správy zdrojového kódu vrátí chybu, očekává se, že se jedná o jeden z následujících kódů chyb. Všechny chyby jsou záporné, upozornění nebo informační kódy chyb jsou kladné a úspěch je 0.

|Kód chyby|Hodnota|Popis|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Modul plug-in podporuje přidávání souborů ze správy zdrojového kódu ve dvou krocích. Další informace najdete v tématu [SccSetOption.](../extensibility/sccsetoption-function.md)|
|`SCC_I_FILEDIFFERS`|6|Místní soubor se liší od souboru v databázi správy zdrojového kódu (například [SccDiff](../extensibility/sccdiff-function.md) může tuto hodnotu vrátit).|
|`SCC_I_RELOADFILE`|5|Místní soubor se během operace správy zdrojového kódu změnil. Pokud je to možné, integrované vývojové prostředí (IDE) by mělo soubor znovu načíst.|
|`SCC_I_FILENOTAFFECTED`|4|Na soubor to nemá vliv.|
|`SCC_I_PROJECTCREATED`|3|Projekt byl vytvořen během operace správy zdrojového kódu (například při volání [SccOpenProject,](../extensibility/sccopenproject-function.md) když je `SCC_OP_CREATEIFNEW` zadán příznak ).|
|`SCC_I_OPERATIONCANCELED`|2|Operace se zrušila.|
|`SCC_I_ADV_SUPPORT`|1|Modul plug-in podporuje upřesňující možnosti pro zadaný příkaz. Další informace najdete v tématu [SccGetCommandOptions.](../extensibility/sccgetcommandoptions-function.md)|
|`SCC_OK`|0|Úspěch.|
|`SCC_E_INITIALIZEFAILED`|-1|Chyba: Inicializace se nezdařila.|
|`SCC_E_UNKNOWNPROJECT`|-2|Chyba: Projekt je neznámý.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Chyba: Projekt se nepokusí vytvořit.|
|`SCC_E_NOTCHECKEDOUT`|-4|Chyba: Soubor není rezervován.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Chyba: Soubor je už rezervován.|
|`SCC_E_FILEISLOCKED`|-6|Chyba: Soubor je uzamčený.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Chyba: Soubor je vyhrazený výhradně.|
|`SCC_E_ACCESSFAILURE`|-8|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|`SCC_E_CHECKINCONFLICT`|-9|Chyba: Při přihlášení došlo ke konfliktu.|
|`SCC_E_FILEALREADYEXISTS`|-10|Chyba: Soubor již existuje.|
|`SCC_E_FILENOTCONTROLLED`|-11|Chyba: Soubor není ve zdrojovém kódu.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Chyba: Soubor je rezervován.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Chyba: Neexistuje žádná zadaná verze.|
|`SCC_E_OPNOTSUPPORTED`|-14|Chyba: Operace se nepodporuje.|
|`SCC_E_NONSPECIFICERROR`|-15|Nespeciká chyba.|
|`SCC_E_OPNOTPERFORMED`|-16|Chyba– operace nebyla provedena.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Chyba: Systém správy zdrojového kódu nepodporuje typ souboru, například binární soubor.|
|`SCC_E_VERIFYMERGE`|-18|Soubor se automaticky sloučil, ale nebyl zkontrolován, protože čeká na ověření uživatele.|
|`SCC_E_FIXMERGE`|-19|Soubor se sloučil automaticky, ale nebyl se ohlásil kvůli konfliktu sloučení, který je třeba vyřešit ručně.|
|`SCC_E_SHELLFAILURE`|-20|Chyba kvůli chybě prostředí.|
|`SCC_E_INVALIDUSER`|-21|Chyba: Uživatel je neplatný.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Chyba: Projekt je už otevřený.|
|`SCC_E_PROJSYNTAXERR`|-23|Chyba syntaxe projektu.|
|`SCC_E_INVALIDFILEPATH`|-24|Chyba: Cesta k souboru je neplatná.|
|`SCC_E_PROJNOTOPEN`|-25|Chyba: Projekt není otevřený.|
|`SCC_E_NOTAUTHORIZED`|-26|Chyba: Uživatel nemá oprávnění k provedení této operace.|
|`SCC_E_FILESYNTAXERR`|-27|Chyba syntaxe souboru.|
|`SCC_E_FILENOTEXIST`|-28|Chyba– místní soubor neexistuje.|
|`SCC_E_CONNECTIONFAILURE`|-29|Chyba: Došlo k selhání připojení.|
|`SCC_E_UNKNOWNERROR`|-30|Neznámou chybu.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operace získání na pozadí právě probíhá.|

## <a name="macros-provided-for-quick-checking"></a>Makra poskytnutá pro rychlou kontrolu

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Poznámky
 Očekává se, že všechny funkce rozhraní API modulu plug-in správy zdrojového kódu (s výjimkou [funkcí SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)a [SccDiff)](../extensibility/sccdiff-function.md)budou úspěšné, pokud místní soubory předané jako argumenty neexistují v pracovní složce. Integrované vývojové prostředí (IDE) může například vydat volání [SccCheckout](../extensibility/scccheckout-function.md) nebo [SccUncheckout](../extensibility/sccuncheckout-function.md) pro soubor, který v pracovní složce neexistuje, ale existuje v systému správy zdrojového kódu. Toto volání by bylo úspěšné. Funkce by měla selhat pouze v případě, že v pracovní složce není žádný soubor nebo v systému správy zdrojového kódu.

 Některé funkce, například a , by měly vrátit konkrétní hodnotu, pokud soubor v pracovní složce `SccAdd` `SccCheckin` `SCC_E_FILENOTEXIST` neexistuje. Očekává se, že jiné funkce budou úspěšné, když pracovní soubor neexistuje, pokud funkce pracují s platným názvem souboru v systému správy zdrojového kódu.

 Modul plug-in správy zdrojového kódu by neměl provádět žádné předpoklady týkající se oprávnění k souboru v pracovní složce, i když modul plug-in během určité operace označil soubor jen pro čtení. Soubor v pracovní složce je možné přesunout, odstranit a změnit mimo ovládací prvek modulu plug-in.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
