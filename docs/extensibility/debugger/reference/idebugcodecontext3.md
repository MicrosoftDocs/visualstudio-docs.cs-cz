---
title: IDebugCodeContext3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734185"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Rozšiřuje rozhraní [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) povolit načítání modulu a rozhraní procesu.

## <a name="syntax"></a>Syntaxe

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementována ladicími [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] moduly a spotřebována balíčkem ladění.

## <a name="methods"></a>Metody
 Kromě metod na `IDebugCodeContext2` rozhraní toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Načte odkaz na rozhraní ladicího modulu.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Načte odkaz na rozhraní procesu ladění.|

## <a name="remarks"></a>Poznámky
 Jedná se o volitelné rozhraní, které obecně nemusí být implementováno.

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
