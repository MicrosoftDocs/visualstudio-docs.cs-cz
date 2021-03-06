---
description: Ladicí stroj (DE) pošle toto rozhraní do Správce ladění relace (SDM), aby během načítání symbolů nastavil zprávu stavového řádku.
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e3e7c0428a96b8841a598e7b91986aa1555ea5c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067475"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Ladicí stroj (DE) pošle toto rozhraní do Správce ladění relace (SDM), aby během načítání symbolů nastavil zprávu stavového řádku.

## <a name="syntax"></a>Syntax

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, když musí nastavit zprávu stavového řádku během načítání symbolů. Toto rozhraní je implementováno pouze ladicími moduly, které pracují s nebo jsou součástí překladačů skriptů. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se musí implementovat na stejný objekt jako toto rozhraní (SDM používá pro přístup k rozhraní **IDebugEvent2** **QueryInterface** .).

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události, když musí nastavit zprávu stavového řádku během načítání symbolů. Událost se posílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , kterou poskytuje SDM, když je připojená k laděnému programu.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody `IDebugBeforeSymbolSearchEvent2` .

|Metoda|Popis|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Načte název aktuálně laděného modulu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
