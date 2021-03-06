---
description: Tato metoda získá počet typů vizualizací, které jsou k dispozici z této služby.
title: 'IEEVisualizerService:: GetCustomViewerCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerCount
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerCount method
ms.assetid: f7b095c2-e538-4352-8cad-d4c6d4f6bdbc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d44cc0c53185f823a8092335052e52dcfd201c1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227148"
---
# <a name="ieevisualizerservicegetcustomviewercount"></a>IEEVisualizerService::GetCustomViewerCount
Tato metoda získá počet typů vizualizací, které jsou k dispozici z této služby.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomViewerCount(
   ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametry
`pcelt`\
mimo Vrátí počet dostupných typů vizualizací.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) předá požadavek této metodě ve své podpoře pro typy vizualizací.

## <a name="see-also"></a>Viz také
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
