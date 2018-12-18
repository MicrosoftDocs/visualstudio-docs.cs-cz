---
title: Enumerátor zpráv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f83692db7755ae4b65f794a570b8c656d6dad145
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897014"
---
# <a name="message-enumerator"></a>Enumerátor zpráv
Následující příznaky se používají pro `TEXTOUTPROC` funkce, což je funkce zpětného volání, která poskytuje integrované vývojové prostředí při volání [sccopenproject –](../extensibility/sccopenproject-function.md) (naleznete v tématu [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) podrobnosti o zpětné volání funkce).  
  
 Pokud integrovaného vývojového prostředí se zobrazí výzva, proces zrušení, může zobrazit jedna z zprávy Storno. V tomto případě používá modul plug-in ovládací prvek zdroje `SCC_MSG_STARTCANCEL` žádat rozhraní IDE zobrazíte **zrušit** tlačítko. Potom může být odeslán libovolnou sadu normální zprávy. Pokud některý z těchto vrátí `SCC_MSG_RTN_CANCEL`, modul plug-in operace se ukončí a vrátí. Modul plug-in také dotazuje `SCC_MSG_DOCANCEL` pravidelně k určení, pokud uživatel operaci zrušil. Když se provádějí všechny operace, nebo pokud uživatel zrušil, modul plug-in odešle `SCC_MSG_STOPCANCEL`. `SCC_MSG_INFO`, SCC_MSG_WARNING, a SCC_MSG_ERROR typy se používají pro zprávy, která se zobrazí v posuvný seznam zpráv. `SCC_MSG_STATUS` je speciální typ, který označuje, že text by se zobrazit na stavovém řádku nebo dočasné oblasti. Není trvale zůstanou v seznamu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Členové  
 SCC_MSG_RTN_CANCEL  
 Návrat z zpětného volání k označení zrušit.  
  
 SCC_MSG_RTN_OK  
 Vrátí ze zpětného volání, abyste mohli pokračovat.  
  
 SCC_MSG_INFO  
 Zpráva je informační.  
  
 SCC_MSG_WARNING  
 Zpráva se upozornění.  
  
 SCC_MSG_ERROR  
 Zpráva se o chybu.  
  
 SCC_MSG_STATUS  
 Zpráva je určená pro stavový řádek.  
  
 SCC_MSG_DOCANCEL  
 Žádný text. Vrátí IDE `SCC_MSG_RTN_OK` nebo `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Zahájí cyklus Storno.  
  
 SCC_MSG_STOPCANCEL  
 Ukončí smyčku Storno.  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvek moduly plug-in zdrojového kódu](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)