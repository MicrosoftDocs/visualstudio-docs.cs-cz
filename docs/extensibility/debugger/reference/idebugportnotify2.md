---
title: IDebugPortNotify2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d3d1161d488ed4a9e12b7af6b70bf336c9f286
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724915"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Toto rozhraní registruje nebo zruší registrace programu, který lze ladit s portem, na který je spuštěn.

## <a name="syntax"></a>Syntaxe

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní pro podporu přidávání a odebírání programů z portu. Obvykle se implementuje na stejném objektu, který implementuje rozhraní [IDebugPort2.](../../../extensibility/debugger/reference/idebugport2.md)

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [QueryInterface](/cpp/atl/queryinterface) v `IDebugPort2` rozhraní vrátí toto rozhraní. Také volání [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) vrátí toto rozhraní. Ladicí modul může vidět toto rozhraní jako parametr [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugPortNotify2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Zaregistruje program, který lze ladit s portem, na který je spuštěn.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Zruší registrace programu, který lze ladit z portu, na který je spuštěn.|

## <a name="remarks"></a>Poznámky
 Pokud ladicí port nemá způsob, jak zjistit, kdy jsou programy načteny nebo uvolněny, musí toto rozhraní implementovat vlastní dodavatel portu. Všechny programy, které jsou načteny pro ladění prostřednictvím určitého portu jsou sledovány pomocí tohoto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
