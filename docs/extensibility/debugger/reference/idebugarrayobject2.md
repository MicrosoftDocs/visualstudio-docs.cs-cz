---
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 418ec9bdef9621f7623e254856ae33dec501a9c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870022"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Představuje objekt spravovaného pole a umožňuje vyhodnocovacímu filtru výrazů (EE) určit základní index (dolní meze) pro pole.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto je implementováno pomocí spravovaného ladicího stroje (DE).

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Načte základní indexy (dolní meze) pro každý index s ohledem na počet rozměrů v poli.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Určuje, zda je v poli definováno základní indexy (dolní meze).|

## <a name="remarks"></a>Poznámky
 Vyhodnocovací filtr výrazů používá toto rozhraní k zastupování spravovaných polí ve stromové struktuře analýzy.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
