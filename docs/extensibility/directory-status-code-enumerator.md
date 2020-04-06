---
title: Čítač stavového kódu adresáře | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b5ebf61f2baa6e4277e27cd3c4d18a51e64f835
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712148"
---
# <a name="directory-status-code-enumerator"></a>Čítač stavového kódu adresáře
Čítač `SccDirStatus` obsahuje pojmenované konstantní hodnoty, které určují stav adresáře v systému správy zdrojového kódu. Tento výčet používá [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). To bylo zavedeno ve verzi 1.2 rozhraní plug-in správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Členové
 SCC_DIRSTATUS_INVALID status nelze získat; nespoléhejte na to.

 SCC_DIRSTATUS_NOTCONTROLLED Directory není pod shodou zdrojového kódu.

 SCC_DIRSTATUS_CONTROLLED Directory je pod shodou zdrojového kódu.

 SCC_DIRSTATUS_EMPTYPROJ Project odpovídající tomuto adresáři je prázdný.

## <a name="see-also"></a>Viz také
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
