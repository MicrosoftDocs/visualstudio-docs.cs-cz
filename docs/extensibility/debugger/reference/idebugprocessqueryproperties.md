---
title: Vlastnosti IDebugProcessQueryProperties | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723275"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Toto rozhraní je rozšíření rozhraní implementované [implementátory IDebugProcess2.](../../../extensibility/debugger/reference/idebugprocess2.md) Umožňuje implementátoru získat informace o prostředí procesu ladění.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementujte toto rozhraní získat informace o spuštění prostředí procesu ladění.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugProcessQueryProperties`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Dotazy na hodnotu vlastnosti.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Dotazy na hodnoty vlastností.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je zřídka implementováno.

## <a name="requirements"></a>Požadavky
 Záhlaví: Portpriv.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
