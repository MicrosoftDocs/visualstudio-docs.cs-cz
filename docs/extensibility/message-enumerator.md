---
title: Message Enumerator | Microsoft Docs
description: Členy tohoto enumerátoru se používají pro funkci TEXTOUTPROC, což je funkce zpětného volání, kterou integrované vývojové prostředí poskytuje při volání objektu SccOpenProject.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77c49f79ccdcfc4aa0325b89dfb38f3f8d4da721
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902589"
---
# <a name="message-enumerator"></a>Enumerátor zpráv
Pro funkci se používají následující příznaky, což je funkce zpětného volání, kterou integrované vývojové prostředí poskytuje při volání SccOpenProject (podrobnosti o funkci zpětného volání najdete v části `TEXTOUTPROC` [LPTEXTOUTPROC).](../extensibility/lptextoutproc.md) [](../extensibility/sccopenproject-function.md)

 Pokud je integrované vývojové prostředí (IDE) požádáno o zrušení procesu, může se zobrazit jedna ze zpráv o zrušení. V tomto případě modul plug-in správy zdrojového kódu použije k tomu, aby požádal integrované vývojové prostředí `SCC_MSG_STARTCANCEL` (IDE) o **zobrazení tlačítka Zrušit.** Potom může být odeslána jakákoli sada normálních zpráv. Pokud některý z těchto hodnot vrátí `SCC_MSG_RTN_CANCEL` , modul plug-in operaci ukončí a vrátí. Modul plug-in se také pravidelně dotazuje, jestli uživatel `SCC_MSG_DOCANCEL` operaci zrušil. Po provedení všech operací nebo zrušení uživatelem modul plug-in odešle `SCC_MSG_STOPCANCEL` . Typy , SCC_MSG_WARNING a SCC_MSG_ERROR se používají pro zprávy, které se zobrazují v posouvání `SCC_MSG_INFO` seznamu zpráv. `SCC_MSG_STATUS` je speciální typ, který označuje, že se text má zobrazit ve stavovém řádku nebo dočasné oblasti zobrazení. Nezůtrval trvale v seznamu.

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
 SCC_MSG_RTN_CANCEL vrácení ze zpětného volání k označení zrušení.

 SCC_MSG_RTN_OK pokračovat návratem ze zpětného volání.

 SCC_MSG_INFO zpráva je informační.

 SCC_MSG_WARNING zpráva je upozornění.

 SCC_MSG_ERROR zpráva je chyba.

 SCC_MSG_STATUS zpráva je určena pro stavový řádek.

 SCC_MSG_DOCANCEL žádný text; Integrované vývojové prostředí (IDE) `SCC_MSG_RTN_OK` vrátí nebo `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL Spustí smyčku zrušení.

 SCC_MSG_STOPCANCEL Zastaví smyčku zrušení.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
