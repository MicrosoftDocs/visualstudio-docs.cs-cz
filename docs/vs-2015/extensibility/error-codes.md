---
title: Kódy chyb | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb27b2b64df0d7f8c0aefb5975844126363fe31d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808340"
---
# <a name="error-codes"></a>Chybové kódy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po návratu funkce rozhraní API modulu Plug-in zdroje ovládacího prvku k chybě, očekává se, že se na jednu z následující kódy chyb. Všechny chyby jsou upozornění nebo informační chybové kódy jsou kladná, záporná, a úspěchu je 0.  
  
|Kód chyby|Hodnota|Popis|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Modul plug-in podporuje přidávání souborů ze správy zdrojových kódů ve dvou krocích. Další informace najdete v tématu [sccsetoption –](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Místní soubor se liší od souboru v databázi správy zdrojových kódů (například [sccdiff –](../extensibility/sccdiff-function.md) může vrátit tuto hodnotu).|  
|`SCC_I_RELOADFILE`|5|Místní soubor byl změněn během operace správy zdrojů; integrované vývojové prostředí by měl znovu načíst soubor a pokud je to možné.|  
|`SCC_I_FILENOTAFFECTED`|4|Soubor nemá vliv.|  
|`SCC_I_PROJECTCREATED`|3|Projekt je vytvořený během operace správy zdrojů (například při volání [sccopenproject –](../extensibility/sccopenproject-function.md) při `SCC_OP_CREATEIFNEW` zadán příznak).|  
|`SCC_I_OPERATIONCANCELED`|2|Operace byla zrušena.|  
|`SCC_I_ADV_SUPPORT`|1|Modul plug-in podporuje rozšířené možnosti pro zadaný příkaz. Další informace najdete v tématu [sccgetcommandoptions –](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Úspěch.|  
|`SCC_E_INITIALIZEFAILED`|-1|Chyba: Inicializace se nezdařila.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Chyba: projekt neznámý.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Chyba: projekt se nepodařilo vytvořit.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Chyba: soubor není rezervován.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Chyba: soubor je již rezervován.|  
|`SCC_E_FILEISLOCKED`|-6|Chyba: soubor je uzamčen.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Chyba: soubor je exkluzivně zaregistrován.|  
|`SCC_E_ACCESSFAILURE`|-8|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|`SCC_E_CHECKINCONFLICT`|-9|Chyba: při vrácení se změnami došlo ke konfliktu.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Chyba: soubor již existuje.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Chyba: soubor není pod správou zdrojových kódů.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Chyba: soubor je rezervován.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Chyba: neexistuje žádné zadané verze.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Chyba: operace není podporována.|  
|`SCC_E_NONSPECIFICERROR`|-15|Došlo k nespecifikované chybě.|  
|`SCC_E_OPNOTPERFORMED`|-16|Chyba operace se neprovedla.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Chyba: typ souboru, například binární, nepodporuje systém správy zdrojového kódu.|  
|`SCC_E_VERIFYMERGE`|-18|Soubor se sloučit automaticky, ale nebyla byly vráceny, protože je ověření uživatele čekající na vyřízení.|  
|`SCC_E_FIXMERGE`|-19|Soubor se sloučit automaticky, ale nebyla vrácena kvůli konfliktu při slučování, který se musí ručně vyřešit.|  
|`SCC_E_SHELLFAILURE`|-20|Došlo k chybě z důvodu chyby prostředí.|  
|`SCC_E_INVALIDUSER`|-21|Chyba: uživatel je neplatný.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Chyba: projekt je již otevřen.|  
|`SCC_E_PROJSYNTAXERR`|-23|Chyba syntaxe v projektu.|  
|`SCC_E_INVALIDFILEPATH`|-24|Chyba: cesta k souboru je neplatná.|  
|`SCC_E_PROJNOTOPEN`|-25|Chyba: projekt není otevřený.|  
|`SCC_E_NOTAUTHORIZED`|-26|Chyba: uživatel nemá oprávnění k provedení této operace.|  
|`SCC_E_FILESYNTAXERR`|-27|Chyba syntaxe v souboru.|  
|`SCC_E_FILENOTEXIST`|-28|Chyba, místní soubor neexistuje.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Chyba: došlo k chybě připojení.|  
|`SCC_E_UNKNOWNERROR`|-30|Došlo k neznámé chybě.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Právě probíhá operace get na pozadí.|  
  
## <a name="macros-provided-for-quick-checking"></a>Makra, které jsou k dispozici pro rychlou kontrolu  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechny funkce rozhraní API modulu Plug-in zdroje ovládacího prvku (s výjimkou [sccadd –](../extensibility/sccadd-function.md), [scccheckin –](../extensibility/scccheckin-function.md), a [sccdiff –](../extensibility/sccdiff-function.md)) se očekává, že úspěšná, když místní soubory, které jsou předány jako argumenty v pracovní složce neexistuje. Rozhraní IDE může například vydávat volání [scccheckout –](../extensibility/scccheckout-function.md) nebo [sccuncheckout –](../extensibility/sccuncheckout-function.md) na soubor, který neexistuje v pracovní složce, ale existuje v systému správy zdrojového kódu. Toto volání bude úspěšné. Pouze v případě, že není dostupný žádný soubor v pracovní složce nebo v systému správy zdrojového kódu se funkce neočekává selhání.  
  
 Některé funkce, jako například `SccAdd` a `SccCheckin`, konkrétně by měla vrátit `SCC_E_FILENOTEXIST` při soubor v pracovní složce neexistuje. Další funkce se očekává uspět, když pracovní soubor buď neexistuje, pokud funkce pracují na platný název souboru v systému správy zdrojového kódu.  
  
 Modul plug-in správy zdrojového kódu by měl vytvořit žádné předpoklady týkající se oprávnění pro soubor v pracovní složce i v případě, že modul plug-in bylo označeno jako soubor jen pro čtení během nějaké operace. Soubor v pracovní složce můžete přesunout, odstranit a změnit mimo modul plug-in pro ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)

