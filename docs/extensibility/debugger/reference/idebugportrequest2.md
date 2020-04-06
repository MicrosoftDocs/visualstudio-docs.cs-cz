---
title: IDebugPortRequest2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 163718fda344ba5f3f44ef630b4eba3e5613dc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724795"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Toto rozhraní popisuje port. Tento popis slouží k přidání portu k dodavateli portu.

## <a name="syntax"></a>Syntaxe

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio obvykle implementuje toto rozhraní v procesu získávání ladicí port od dodavatele portu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je předáno do [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) vytvořit ladicí port. Volání [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) vrátí toto rozhraní, představující požadavek použitý k vytvoření portu na prvním místě.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugPortRequest2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Získá název portu vytvořit.|

## <a name="remarks"></a>Poznámky
 Ladicí modul obvykle nespolupracuje s dodavatelem portu a nebude mít žádné využití pro toto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
