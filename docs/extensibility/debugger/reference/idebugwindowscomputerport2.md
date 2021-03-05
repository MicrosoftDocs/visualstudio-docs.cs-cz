---
description: Umožňuje dotazování na informace o cílovém počítači.
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c7e940c2284b5b39097226f9a5b0c3b34a0d18
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222949"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Umožňuje dotazování na informace o cílovém počítači.

## <a name="syntax"></a>Syntax

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno pomocí objektů portů Správce ladění relace.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody `IDebugWindowsComputerPort2` .

|Metoda|Popis|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Načte informace o počítači, na kterém je spuštěný ladicí program.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
