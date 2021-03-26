---
description: Představuje definici pole pro obecný typ spravovaného kódu.
title: IDebugGenericFieldDefinition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0c9b2a4b9dbdbf5d1b5faefb8dfbf498f873ec01
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063354"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Představuje definici pole pro obecný typ spravovaného kódu.

## <a name="syntax"></a>Syntax

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Metody
 Toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Vytvoří instanci pole s daným polem argumentů typu.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Načte parametry typu s daným počtem parametrů.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Načte počet parametrů typu přidružených k obecnému poli.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
