---
description: Toto rozhraní umožňuje správci ladění relace (SDM) řídit programy a procesy spuštěné na portu.
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e26fec4b47a301bfb266f40b41fd88216ccf671f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072426"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Toto rozhraní umožňuje správci ladění relace (SDM) řídit programy a procesy spuštěné na portu.

## <a name="syntax"></a>Syntax

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní na stejný objekt, který implementuje [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Model SDM zavolá na rozhraní [QueryInterface](/cpp/atl/queryinterface) , `IDebugPort2` aby získal toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugPortEx2` .

|Metoda|Popis|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Spustí spustitelný soubor.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Obnoví spuštění procesu.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Určuje, zda může být proces ukončen.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Ukončí proces.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Získá ID procesu samotného portu.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Načte program přidružený k uzlu programu.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je obvykle privátní mezi serverem SDM a vlastním dodavatelem portu.

 V případě potřeby může ladicí stroj (DE) vyhledat toto rozhraní v rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) předaném do [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) a použít [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) pro spuštění programu. Nejedná se však o požadavek a v případě, že je to nutné k tomu, aby bylo možné spustit program žádosti.

## <a name="requirements"></a>Požadavky
 Záhlaví: portpriv. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
