---
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74b9e62b2e442bbab01942f155647f16eae29b09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941655"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Toto rozhraní registruje nebo odregistruje program, který se dá ladit s portem, na kterém je spuštěný.

## <a name="syntax"></a>Syntax

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní, aby podporovalo přidávání a odebírání programů z portu. Obvykle je implementován na stejném objektu, který implementuje rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) .

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [QueryInterface](/cpp/atl/queryinterface) na `IDebugPort2` rozhraní vrací toto rozhraní. Také volání [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) vrací toto rozhraní. Ladicí stroj může toto rozhraní zobrazit jako parametr pro [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugPortNotify2` .

|Metoda|Popis|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Zaregistruje program, který se dá ladit s portem, na kterém je spuštěný.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Zruší registraci programu, který je možné ladit z portu, na kterém je spuštěný.|

## <a name="remarks"></a>Poznámky
 Pokud port ladění nemá způsob, jak zjistit, kdy jsou programy načteny nebo uvolněny, musí implementovat toto rozhraní vlastní dodavatel portu. Všechny programy načtené pro ladění prostřednictvím konkrétního portu jsou sledovány pomocí tohoto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
