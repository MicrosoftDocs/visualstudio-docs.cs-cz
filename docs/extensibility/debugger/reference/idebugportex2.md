---
title: IDebugPortEx2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5789681b0da70f46dadac1e29d0d6bb9dc905d1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724999"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Toto rozhraní umožňuje správci ladění relace (SDM) řídit programy a procesy spuštěné na portu.

## <a name="syntax"></a>Syntaxe

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní port dodavatel implementuje toto rozhraní na stejný objekt, který implementuje [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Poznámky pro volající
 SDM volá [QueryInterface](/cpp/atl/queryinterface) `IDebugPort2` v rozhraní získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugPortEx2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Spustí spustitelný soubor.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Pokračuje v provádění procesu.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Určuje, zda lze proces ukončit.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Ukončí proces.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Získá ID procesu portu samotného.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Získá program přidružený k uzlu programu.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je obvykle soukromé mezi SDM a dodavatelem vlastního portu.

 V případě potřeby ladicí modul (DE) můžete vyhledat toto rozhraní na rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) předán [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) a použít [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) ke spuštění programu. To však není požadavek a DE může dělat, co je třeba udělat pro spuštění programu požadavku.

## <a name="requirements"></a>Požadavky
 Záhlaví: portpriv.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
