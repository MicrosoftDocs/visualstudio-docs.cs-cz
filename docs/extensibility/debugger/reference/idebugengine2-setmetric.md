---
description: Tato metoda nastaví hodnotu registru známou jako metrika.
title: 'IDebugEngine2:: SetMetric | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ec947a97506283b6d26f0e4cb26b06afb183dd57
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087883"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Tato metoda nastaví hodnotu registru známou jako metrika.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Parametry
`pszMetric`\
pro Název metriky.

`varValue`\
pro Určuje hodnotu metriky.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Metrika je hodnota registru, která slouží ke změně chování ladicího modulu nebo k inzerování podporovaných funkcí. Tato metoda může přeslat volání příslušnému formuláři [pomocníků sady SDK pro funkci ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` .

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
