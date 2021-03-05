---
description: Určuje stav čeká na zarážce (zarážka, která ještě není vázaná).
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce0ceedd50fbdf6345b49143c4634f49dec308f7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222117"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Určuje stav čeká na zarážce (zarážka, která ještě není vázaná).

## <a name="syntax"></a>Syntax

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Pole
 `PBPS_NONE`\
 Zástupný symbol pro nulu Tato hodnota se nikdy nevrátí.

 `PBPS_DELETED`\
 Indikuje, že se odstranila nevyřízená zarážka.

 `PBPS_DISABLED`\
 Indikuje, že probíhající zarážka je zakázaná.

 `PBPS_ENABLED`\
 Indikuje, že je povolená nedokončená zarážka.

## <a name="remarks"></a>Poznámky
 Použijte jako `state` člen struktury [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
