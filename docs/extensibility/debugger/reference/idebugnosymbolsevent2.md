---
title: IDebugNoSymbolsEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9483c5a434ddfddb3f877111deabea9be6520b05
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726719"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Signalizuje [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uživatelskérozhraní ladicího programu, aby uživatele varoval, že symboly nelze nalézt pro spuštěný spustitelný soubor.

## <a name="syntax"></a>Syntaxe

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementováno ladicími [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] moduly a spotřebováno uzlem ladicího programu.

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
