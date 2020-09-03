---
title: Enumerátor zprávy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702511"
---
# <a name="message-enumerator"></a>Enumerátor zprávy
Následující příznaky jsou použity pro `TEXTOUTPROC` funkci, což je funkce zpětného volání, která rozhraní IDE poskytuje při volání [SccOpenProject](../extensibility/sccopenproject-function.md) (podrobnosti o funkci zpětného volání naleznete v tématu [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) ).

 Pokud je rozhraní IDE požádáno o zrušení procesu, může se zobrazit jedna z zpráv zrušení. V tomto případě modul plug-in správy zdrojových kódů používá k tomu, aby `SCC_MSG_STARTCANCEL` se zobrazilo tlačítko **Zrušit** , aby se zobrazilo tlačítko Storno. V takovém případě může být odeslána jakákoli sada běžných zpráv. Pokud některý z těchto `SCC_MSG_RTN_CANCEL` operací vrátí, modul plug-in ukončí operaci a vrátí. Modul plug-in se také pravidelně dotazuje `SCC_MSG_DOCANCEL` , aby zjistil, jestli uživatel operaci zrušil. Když jsou všechny operace dokončené nebo pokud se uživatel zrušil, modul plug-in ho pošle `SCC_MSG_STOPCANCEL` . `SCC_MSG_INFO`Typy, SCC_MSG_WARNING a SCC_MSG_ERROR se používají pro zprávy, které se zobrazují v seznamu posouvaných zpráv. `SCC_MSG_STATUS` je speciální typ, který označuje, že se má text zobrazit ve stavovém řádku nebo v dočasné zobrazované oblasti. Nezůstane v seznamu trvale.

## <a name="syntax"></a>Syntax

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
 SCC_MSG_RTN_CANCEL návratu ze zpětného volání k označení Cancel.

 Pokračování SCC_MSG_RTN_OK návratem ze zpětného volání.

 SCC_MSG_INFO zpráva je informační.

 SCC_MSG_WARNING zpráva je upozornění.

 SCC_MSG_ERROR zpráva je chyba.

 SCC_MSG_STATUS zpráva je určena pro stavový řádek.

 NeSCC_MSG_DOCANCEL žádný text; IDE vrátí `SCC_MSG_RTN_OK` nebo `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL spustí smyčku Cancel.

 SCC_MSG_STOPCANCEL zastaví smyčku Cancel.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
