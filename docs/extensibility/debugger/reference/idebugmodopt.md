---
description: Představuje volitelný modifikátor ladění.
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 047c01f78931e1b13110640952c67c11a68bc8a2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149857"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Představuje volitelný modifikátor ladění.

## <a name="syntax"></a>Syntax

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Poznámky pro volající
 Získáno z objektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , který představuje třídu nebo metodu.

## <a name="methods"></a>Metody
 Toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Načte seznam volitelných modifikátorů.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
