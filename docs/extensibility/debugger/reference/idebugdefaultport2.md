---
title: IDebugDefaultPort2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732311"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Toto rozhraní poskytuje několik metod pro přístup k serveru portu a oznamovacím zařízením.

## <a name="syntax"></a>Syntaxe

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní představující ladicí port pro přístup k programům. Vlastní port dodavatel můžete také implementovat toto rozhraní, pokud zpracovává vzdálené ladění.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní poskytuje argument metod v rozhraní [IDebugProgramProvider2.](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Volání [QueryInterface](/cpp/atl/queryinterface) v rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) můžete také získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod definovaných v [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Získá rozhraní oznámení portu z tohoto portu.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Získá rozhraní k serveru hostující tento port.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Určuje, zda je tento port spuštěn v místním počítači.|

## <a name="remarks"></a>Poznámky
 Název "`IDebugDefaultPort2`" je trochu nesprávné hod, protože nepředstavuje výchozí port. To by mohlo být nazýváno "IDebugPort3."

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
