---
title: IDebugProcessEx2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723338"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Toto rozhraní umožňuje správci ladění relace (SDM) oznamovat proces, ke kterému se připojuje nebo odpojuje od tohoto procesu.

## <a name="syntax"></a>Syntax

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní na stejném objektu jako rozhraní [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , aby:

- Podpora sledování relací připojených k procesu

- Podpora automatického připojení mezi několika ladicími moduly

  Vlastní dodavatel portu může implementovat toto rozhraní, pokud se rozhodne.

## <a name="notes-for-callers"></a>Poznámky pro volající

- SDM zavolá metodu [QueryInterface](/cpp/atl/queryinterface) na `IDebugProcess2` rozhraní, aby získala toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugProcessEx2` .

|Metoda|Popis|
|------------|-----------------|
|[Připojit](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informuje o procesu, že relace právě ladí proces.|
|[Odpojit](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informuje o procesu, že relace již neprovádí ladění procesu.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Přidá uzly programu pro seznam ladicích modulů.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je privátní mezi modelem SDM a procesem.

## <a name="requirements"></a>Požadavky
 Záhlaví: Portpriv. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
