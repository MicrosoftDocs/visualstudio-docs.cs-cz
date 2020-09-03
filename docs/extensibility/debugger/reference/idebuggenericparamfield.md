---
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b04b0805aec5ecee818fa42e1d76a76cce12b66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727838"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Představuje parametr pro obecný typ spravovaného kódu.

## <a name="syntax"></a>Syntax

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Používá se pro podporu generických typů.

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Vrátí počet omezení, která jsou přidružena k tomuto obecnému parametru.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Načte omezení, která jsou přidružena k tomuto obecnému parametru.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Načte příznaky pro tento obecný parametr.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Načte index tohoto obecného parametru.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Načte název tohoto obecného parametru.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Načte typ nebo vlastníka metody tohoto obecného parametru.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
