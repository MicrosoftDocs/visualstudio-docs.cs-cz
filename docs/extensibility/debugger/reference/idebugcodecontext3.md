---
description: Rozšiřuje rozhraní IDebugCodeContext2, aby bylo možné načíst rozhraní modulu a procesu.
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db806a4b45e855533e4ded1419f2d2117fb4f912
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164016"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Rozšiřuje rozhraní [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , aby bylo možné načíst rozhraní modulu a procesu.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementováno ladicími moduly a spotřebované [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ladicím balíčkem.

## <a name="methods"></a>Metody
 Kromě metod v `IDebugCodeContext2` rozhraní implementuje toto rozhraní následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Načte odkaz na rozhraní modulu ladění.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Načte odkaz na rozhraní procesu ladění.|

## <a name="remarks"></a>Poznámky
 Toto je volitelné rozhraní, které obecně nemusí být implementováno.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
