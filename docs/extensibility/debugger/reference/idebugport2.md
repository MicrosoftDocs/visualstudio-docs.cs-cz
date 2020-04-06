---
title: IDebugPort2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725227"
---
# <a name="idebugport2"></a>IDebugPort2
Toto rozhraní představuje ladicí port v počítači.

## <a name="syntax"></a>Syntaxe

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní představující ladicí port v počítači.

 Pokud port podporuje odesílání událostí portu, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> musí také <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> implementovat rozhraní pro podporu rozhraní, které zase poskytuje rozhraní [IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) nebo [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) vrátit toto rozhraní, představující požadovaný port.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugPort2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Vrátí název portu.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Vrátí identifikátor portu.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Vrátí požadavek použitý k vytvoření portu (pokud je k dispozici).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Vrátí dodavatele portu pro tento port.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Vrátí rozhraní procesu s ohledem na identifikátor procesu.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Vyjmenovává všechny procesy spuštěné na portu.|

## <a name="remarks"></a>Poznámky
 Místní port poskytuje přístup ke všem procesům a programům spuštěných v místním počítači. Jiné porty mohou představovat připojení sériového kabelu k zařízení se systémem Windows CE nebo síťové připojení k počítači bez dcom. Rozhraní `IDebugPort2` se používá k vyhledání názvu a identifikátoru portu a vytvoření výčtu všech procesů spuštěných na portu. Zařízení pro spouštění a ukončování `IDebugPortEx2` procesů na portu jsou implementována v rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
