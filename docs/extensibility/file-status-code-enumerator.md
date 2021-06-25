---
title: Enumerátor kódu stavu | Microsoft Docs
description: Enumerátor SccStatus obsahuje konstantní hodnoty, které určují stav souboru v systému správy zdrojového kódu a používají ho SccQueryInfo a POPLISTFUNC.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 95de8a29efcd56880cdaf452c9f21b90bba1c5c9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900964"
---
# <a name="file-status-code-enumerator"></a>Enumerátor kódu stavu souboru
`SccStatus`Enumerátor obsahuje pojmenované konstantní hodnoty, které určují stav souboru v systému správy zdrojového kódu. Tento výčet používá [SccQueryInfo](../extensibility/sccqueryinfo-function.md) a funkce zpětného volání (podrobnosti najdete v tématu `POPLISTFUNC` [POPLISTFUNC).](../extensibility/poplistfunc.md)

## <a name="syntax"></a>Syntax

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Členové
 SCC_STATUS_INVALID stav se nepokusí získat. Nespoléhejte na to.

 SCC_STATUS_NOTCONTROLLED soubor není ve zdrojovém kódu.

 SCC_STATUS_CONTROLLED File (Soubor) je pod ssíní zdrojového kódu.

 SCC_STATUS_CHECKEDOUT rezervováno aktuálním uživatelem na místním disku.

 SCC_STATUS_OUTOTHER soubor je rezervován jiným uživatelem.

 SCC_STATUS_OUTEXCLUSIVE soubor je vyhrazený výhradně.

 SCC_STATUS_OUTMULTIPLE soubor je rezervován více než jedním uživatelem.

 SCC_STATUS_OUTOFDATE Soubor není nejnovější.

 SCC_STATUS_DELETED soubor byl z projektu odstraněn.

 SCC_STATUS_LOCKED soubor je uzamčený. nejsou povoleny žádné další verze.

 SCC_STATUS_MERGED soubor byl sloučen, ale ještě nebyl opraven nebo ověřen.

 SCC_STATUS_SHARED soubor se sdílí mezi projekty.

 SCC_STATUS_PINNED file se sdílí s explicitní verzí.

 SCC_STATUS_MODIFIED soubor se změnil, porušoval nebo porušoval.

 SCC_STATUS_OUTBYUSER soubor je rezervován aktuálním uživatelem.

 SCC_STATUS_NOMERGE soubor nelze nikdy sloučit s a není nutné ho uložit před GET.

 SCC_STATUS_RESERVED_1 vyhrazeno pro interní použití.

 SCC_STATUS_RESERVED_2 vyhrazeno pro interní použití.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
