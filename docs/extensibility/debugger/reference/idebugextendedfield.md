---
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad10050aa157b4481fa2041ec5f322451983149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729034"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Rozšiřuje typy polí, která jsou k dispozici pro podporu obecných kódů spravovaného kódu.

## <a name="syntax"></a>Syntax

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Načte zadaný rozšířený typ pole.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Určuje, zda pole představuje uzavřený typ.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
