---
title: Enumerátor stavového kódu adresáře | Microsoft Docs
description: Enumerátor SccDirStatus obsahuje pojmenované konstantní hodnoty, které určují stav adresáře v systému správy zdrojového kódu a používá ho SccDirQueryInfo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e995fb1dcb879645f59d6d8750852a790c99e90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091250"
---
# <a name="directory-status-code-enumerator"></a>Enumerátor stavového kódu adresáře
`SccDirStatus`Enumerátor obsahuje pojmenované konstantní hodnoty, které určují stav adresáře v systému správy zdrojového kódu. Tento výčet používá [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Tato verze byla představena ve verzi 1,2 rozhraní API modulu plug-in správy zdrojového kódu.

## <a name="syntax"></a>Syntax

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Členové
 Nelze získat SCC_DIRSTATUS_INVALID stav; nespoléhá na ni.

 SCC_DIRSTATUS_NOTCONTROLLED adresář není pod správou zdrojových kódů.

 SCC_DIRSTATUS_CONTROLLED adresář je pod správou zdrojových kódů.

 SCC_DIRSTATUS_EMPTYPROJ projekt odpovídající tomuto adresáři je prázdný.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
