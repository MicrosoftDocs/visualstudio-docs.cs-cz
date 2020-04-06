---
title: IDebugSourceServerModule | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719911"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Představuje informace o zdrojovém serveru, který je obsažen v souboru PDB.

## <a name="syntax"></a>Syntaxe

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno ladicími moduly a spotřebovává uživatelské rozhraní ladicího programu.

## <a name="methods"></a>Metody
 V následující tabulce jsou `IDebugSourceServerModule`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Načte pole informací zdrojového serveru.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
