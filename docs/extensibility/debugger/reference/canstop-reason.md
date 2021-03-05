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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: def5bdbb6433f6a154eb6f84a88fb39004bc41ae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170995"
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
