---
description: Slouží k určení, zda může program zastavit provádění po dosažení určitého bodu v provádění.
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39a22a0534a464e9899e666550b31ab24503c05d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096522"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Slouží k určení, zda může program zastavit provádění po dosažení určitého bodu v provádění.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Pole
`CANSTOP_ENTRYPOINT`\
Určuje vstupní bod daného programu.

`CANSTOP_STEPIN`\
Určuje krokování do funkce.

## <a name="remarks"></a>Poznámky
Předána jako argument metodě [getdůvod](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) pro potvrzení se správcem ladění relace (SDM), pokud je v pořádku, aby se zastavil po dosažení vstupního bodu programu nebo po rozkrokování do funkce nebo metody.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
