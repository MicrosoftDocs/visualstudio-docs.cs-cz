---
title: IDebugPointerObject3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8605f1cdd50b6e98d6e30a7b550cce1d22543ff9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725464"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Představuje ukazatel ve stromové struktuře analýzy a rozšiřuje rozhraní **IDebugPointerObject** .

## <a name="syntax"></a>Syntax

```
IDebugPointerObject3 : IDebugPointerObject
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní implementuje vyhodnocení výrazu (EE).

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|Načte adresu ukazatele.|

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
