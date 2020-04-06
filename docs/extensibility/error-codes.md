---
title: Kódy chyb | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711844"
---
# <a name="error-codes"></a>Kódy chyb
Pokud funkce rozhraní plug-in správy zdrojového kódu vrátí chybu, očekává se, že bude jedním z následujících kódů chyb. Všechny chyby jsou záporné, upozornění nebo kódy chyb informací jsou kladné a úspěch je 0.

|Kód chyby|Hodnota|Popis|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Modul plug-in podporuje přidávání souborů ze správy zdrojového kódu ve dvou krocích. Další informace naleznete v tématu [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Místní soubor se liší od souboru v databázi správy zdrojového kódu (například [SccDiff](../extensibility/sccdiff-function.md) může vrátit tuto hodnotu).|
|`SCC_I_RELOADFILE`|5|Místní soubor byl změněn během operace správy zdrojového kódu. IDE by měl znovu načíst soubor, pokud je to možné.|
|`SCC_I_FILENOTAFFECTED`|4|Soubor není ovlivněn.|
|`SCC_I_PROJECTCREATED`|3|Projekt byl vytvořen během operace správy zdrojového kódu (například během `SCC_OP_CREATEIFNEW` volání [SccOpenProject](../extensibility/sccopenproject-function.md) při zadání příznaku).|
|`SCC_I_OPERATIONCANCELED`|2|Operace byla zrušena.|
|`SCC_I_ADV_SUPPORT`|1|Modul plug-in podporuje rozšířené možnosti určeného příkazu. Další informace naleznete v tématu [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Úspěch|
|`SCC_E_INITIALIZEFAILED`|-1|Chyba: Inicializace se nezdařila.|
|`SCC_E_UNKNOWNPROJECT`|-2|Chyba: Projekt není znám.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Chyba: Projekt nelze vytvořit.|
|`SCC_E_NOTCHECKEDOUT`|-4|Chyba: Soubor není rezervován.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Chyba: Soubor je již rezervován.|
|`SCC_E_FILEISLOCKED`|-6|Chyba: soubor je uzamčen.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Chyba: Soubor je výhradně rezervován.|
|`SCC_E_ACCESSFAILURE`|-8|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|`SCC_E_CHECKINCONFLICT`|-9|Chyba: Při vrácení se změnami došlo ke konfliktu.|
|`SCC_E_FILEALREADYEXISTS`|-10|Chyba: soubor již existuje.|
|`SCC_E_FILENOTCONTROLLED`|-11|Chyba: Soubor není pod shodou zdrojového kódu.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Chyba: Soubor je rezervován.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Chyba: Neexistuje žádná zadaná verze.|
|`SCC_E_OPNOTSUPPORTED`|-14|Chyba: operace není podporována.|
|`SCC_E_NONSPECIFICERROR`|-15|Nespecifická chyba.|
|`SCC_E_OPNOTPERFORMED`|-16|Chyba, operace nebyla provedena.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Chyba: Typ souboru, například binární, není podporován systémem správy zdrojového kódu.|
|`SCC_E_VERIFYMERGE`|-18|Soubor byl automaticky sloučen, ale nebyl zkontrolován, protože čeká na ověření uživatele.|
|`SCC_E_FIXMERGE`|-19|Soubor byl automaticky sloučen, ale nebyl vrácen se změnami z důvodu konfliktu sloučení, který je nutné ručně vyřešit.|
|`SCC_E_SHELLFAILURE`|-20|Chyba způsobená selháním prostředí.|
|`SCC_E_INVALIDUSER`|-21|Chyba: uživatel je neplatný.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Chyba: projekt je již otevřen.|
|`SCC_E_PROJSYNTAXERR`|-23|Chyba syntaxe projektu.|
|`SCC_E_INVALIDFILEPATH`|-24|Chyba: Cesta k souboru je neplatná.|
|`SCC_E_PROJNOTOPEN`|-25|Chyba: projekt není otevřen.|
|`SCC_E_NOTAUTHORIZED`|-26|Chyba: Uživatel není oprávněn provést tuto operaci.|
|`SCC_E_FILESYNTAXERR`|-27|Chyba syntaxe souboru.|
|`SCC_E_FILENOTEXIST`|-28|Chyba, místní soubor neexistuje.|
|`SCC_E_CONNECTIONFAILURE`|-29|Chyba: Došlo k selhání připojení.|
|`SCC_E_UNKNOWNERROR`|-30|Neznámou chybu.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operace získání na pozadí právě probíhá.|

## <a name="macros-provided-for-quick-checking"></a>Makra pro rychlou kontrolu

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Poznámky
 Očekává se, že všechny funkce rozhraní PLUG-in správy zdrojového kódu (s výjimkou [funkcí SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)a [SccDiff](../extensibility/sccdiff-function.md)) budou úspěšné, pokud místní soubory, které jsou předány jako argumenty, neexistují v pracovní složce. Například ide může vydat volání [SccCheckout](../extensibility/scccheckout-function.md) nebo [SccUncheckout](../extensibility/sccuncheckout-function.md) na soubor, který neexistuje v pracovní složce, ale existuje v systému správy zdrojového kódu. Toto volání by bylo úspěšné. Pouze v případě, že není žádný soubor v pracovní složce nebo v systému správy zdrojového kódu je funkce očekává selhání.

 Některé funkce, `SccAdd` například a `SccCheckin` `SCC_E_FILENOTEXIST` , by se měly konkrétně vrátit, pokud soubor v pracovní složce neexistuje. Očekává se, že ostatní funkce budou úspěšné, pokud pracovní soubor neexistuje, pokud funkce pracují s platným názvem souboru v systému správy zdrojového kódu.

 Modul plug-in správy zdrojového kódu by neměl provádět žádné předpoklady týkající se oprávnění k souboru v pracovní složce, a to ani v případě, že modul plug-in označil soubor jen pro čtení během určité operace. Soubor v pracovní složce lze přesunout, odstranit a změnit mimo ovládací prvek modulu plug-in.

## <a name="see-also"></a>Viz také
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
