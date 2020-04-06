---
title: Čítač výčtu zpráv | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702511"
---
# <a name="message-enumerator"></a>Čítač výčtu zpráv
Následující příznaky se používají `TEXTOUTPROC` pro funkci, což je funkce zpětného volání, kterou poskytuje ide při volání [SccOpenProject](../extensibility/sccopenproject-function.md) (viz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) podrobnosti o funkci zpětného volání).

 Pokud ide je vyzván ke zrušení procesu, může získat jednu ze zpráv zrušení. V takovém případě modul plug-in `SCC_MSG_STARTCANCEL` správy zdrojového kódu používá k tomu, aby ide zobrazilo tlačítko **Storno.** Poté může být odeslána libovolná sada normálních zpráv. Pokud některá `SCC_MSG_RTN_CANCEL`z těchto vrátí , pak modul plug-in ukončí operaci a vrátí. Modul plug-in `SCC_MSG_DOCANCEL` také pravidelně dotazování k určení, zda uživatel zrušil operaci. Po dokončení všech operací nebo pokud uživatel zrušil, modul `SCC_MSG_STOPCANCEL`plug-in odešle . Typy `SCC_MSG_INFO`, SCC_MSG_WARNING a SCC_MSG_ERROR se používají pro zprávy, které se zobrazí v seznamu posouvání zpráv. `SCC_MSG_STATUS`je zvláštní typ, který označuje, že text by se měl zobrazit na stavovém řádku nebo v oblasti dočasného zobrazení. Nezůstává trvale v seznamu.

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
 SCC_MSG_RTN_CANCEL Návrat z zpětného volání označuje zrušení.

 SCC_MSG_RTN_OK Pokračovat z zpětného volání.

 SCC_MSG_INFO Zpráva je informační.

 SCC_MSG_WARNING Zpráva je varování.

 SCC_MSG_ERROR Zpráva je chyba.

 SCC_MSG_STATUS Zpráva je určena pro stavový řádek.

 SCC_MSG_DOCANCEL Žádný text; IDE `SCC_MSG_RTN_OK` vrátí `SCC_MSG_RTN_CANCEL`nebo .

 SCC_MSG_STARTCANCEL Spustí smyčku zrušení.

 SCC_MSG_STOPCANCEL Zastaví smyčku zrušení.

## <a name="see-also"></a>Viz také
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
