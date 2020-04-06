---
title: Enumerátor kódu stavu souboru | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711457"
---
# <a name="file-status-code-enumerator"></a>Čítač stavového kódu souboru
Čítač `SccStatus` obsahuje pojmenované konstantní hodnoty, které určují stav souboru v systému správy zdrojového kódu. Tento výčet používá [SccQueryInfo](../extensibility/sccqueryinfo-function.md) a `POPLISTFUNC` funkce zpětného volání (podrobnosti naleznete v tématu [POPLISTFUNC).](../extensibility/poplistfunc.md)

## <a name="syntax"></a>Syntaxe

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Členové
 SCC_STATUS_INVALID status nelze získat; nespoléhejte na to.

 SCC_STATUS_NOTCONTROLLED soubor není pod sohledem zdrojového kódu.

 SCC_STATUS_CONTROLLED soubor je pod shodou zdrojového kódu.

 SCC_STATUS_CHECKEDOUT Rezervováno aktuálním uživatelem na místním disku.

 SCC_STATUS_OUTOTHER soubor je rezervován jiným uživatelem.

 SCC_STATUS_OUTEXCLUSIVE soubor je výhradně rezervován.

 SCC_STATUS_OUTMULTIPLE soubor je rezervován více než jedním uživatelem.

 SCC_STATUS_OUTOFDATE Soubor není nejnovější.

 SCC_STATUS_DELETED soubor byl z projektu odstraněn.

 SCC_STATUS_LOCKED soubor je uzamčen; žádné další verze povoleny.

 SCC_STATUS_MERGED soubor byl sloučen, ale ještě nebyl opraven/ověřen.

 SCC_STATUS_SHARED Soubor je sdílen mezi projekty.

 SCC_STATUS_PINNED soubor je sdílen s explicitní verzí.

 SCC_STATUS_MODIFIED soubor byl změněn/poškozen/porušen.

 soubor SCC_STATUS_OUTBYUSER je rezervován aktuálním uživatelem.

 SCC_STATUS_NOMERGE soubor nelze nikdy sloučit s a nemusí být uloženy před GET.

 SCC_STATUS_RESERVED_1 Vyhrazeno pro interní použití.

 SCC_STATUS_RESERVED_2 Vyhrazeno pro interní použití.

## <a name="see-also"></a>Viz také
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
