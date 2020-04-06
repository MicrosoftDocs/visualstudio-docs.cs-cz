---
title: IDebugProcessEx2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723338"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Toto rozhraní umožňuje správce ladění relace (SDM) upozornit proces, který se připojuje k procesu nebo od něj odpojit.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Dodavatel vlastního portu implementuje toto rozhraní na stejném objektu jako rozhraní [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) aby:

- Podpora sledování relací připojených k procesu

- Podpora automatického připojení mezi více ladicími moduly

  Vlastní port dodavatel můžete implementovat toto rozhraní, pokud se rozhodne.

## <a name="notes-for-callers"></a>Poznámky pro volající

- SDM volá [QueryInterface](/cpp/atl/queryinterface) `IDebugProcess2` na rozhraní získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugProcessEx2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Připojit](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informuje proces, že relace je nyní ladění procesu.|
|[Odpojit](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informuje proces, že relace již není ladění procesu.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Přidá uzly programu pro seznam ladicích modulů.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je soukromé mezi SDM a procesem.

## <a name="requirements"></a>Požadavky
 Záhlaví: Portpriv.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
