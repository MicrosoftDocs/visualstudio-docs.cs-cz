---
title: IDebugProgramHost2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0680e0a174716dc79a9819386901d8687422906
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898771"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Toto rozhraní poskytuje informace o programu hostitele (procesu).

## <a name="syntax"></a>Syntax

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul implementuje toto rozhraní na stejném objektu jako rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) pro poskytnutí informací o hostitelském procesu. Toto je volitelné rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 [](/cpp/atl/queryinterface) `IDebugProgram2` Chcete-li získat toto rozhraní, zavolejte na rozhraní QueryInterface.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugProgramHost2` .

|Metoda|Popis|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Získá název, popisný název nebo název souboru hostujícího procesu tohoto programu.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Získá identifikátor procesu hostitelského procesu tohoto programu.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Získá název počítače, na kterém je spuštěn hostitelský proces tohoto programu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
