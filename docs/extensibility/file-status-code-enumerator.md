---
title: Enumerátor kódu stavu souboru | Microsoft Docs
description: Enumerátor SccStatus obsahuje konstantní hodnoty, které určují stav souboru v systému správy zdrojového kódu a používají je SccQueryInfo a POPLISTFUNC.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 981e4e4561db7bc7fb8a9f0ce92522d34e4b34fa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874045"
---
# <a name="file-status-code-enumerator"></a>Výčet stavových kódů souborů
`SccStatus`Enumerátor obsahuje pojmenované konstantní hodnoty, které určují stav souboru v systému správy zdrojového kódu. Tento výčet používá [SccQueryInfo](../extensibility/sccqueryinfo-function.md) a `POPLISTFUNC` funkci zpětného volání (podrobnosti viz [POPLISTFUNC](../extensibility/poplistfunc.md) ).

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
 Nelze získat SCC_STATUS_INVALID stav; nespoléhá na ni.

 SCC_STATUS_NOTCONTROLLED soubor není pod správou zdrojových kódů.

 SCC_STATUS_CONTROLLED soubor je pod správou zdrojového kódu.

 SCC_STATUS_CHECKEDOUT zaregistrováno aktuálním uživatelem na místním disku.

 Soubor SCC_STATUS_OUTOTHER je rezervován jiným uživatelem.

 Soubor SCC_STATUS_OUTEXCLUSIVE je exkluzivně zaregistrován.

 SCC_STATUS_OUTMULTIPLE soubor je rezervován více než jedním uživatelem.

 SCC_STATUS_OUTOFDATE soubor není poslední.

 SCC_STATUS_DELETED soubor byl odstraněn z projektu.

 Soubor SCC_STATUS_LOCKED je zamčený. nejsou povoleny žádné další verze.

 SCC_STATUS_MERGED soubor byl sloučen, ale ještě nebyl opraven/ověřen.

 SCC_STATUS_SHARED soubor se sdílí mezi projekty.

 Soubor SCC_STATUS_PINNED se sdílí s explicitní verzí.

 Soubor SCC_STATUS_MODIFIED byl změněn/přerušen nebo porušen.

 Soubor SCC_STATUS_OUTBYUSER je rezervován aktuálním uživatelem.

 Soubor SCC_STATUS_NOMERGE nelze nikdy sloučit s a nemusí být před ZÍSKÁNÍm uložen.

 SCC_STATUS_RESERVED_1 vyhrazena pro interní použití.

 SCC_STATUS_RESERVED_2 vyhrazena pro interní použití.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
