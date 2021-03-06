---
description: Načte počet řetězců hodnot, které se mají zobrazit pro zadanou vlastnost nebo pole.
title: 'IEEVisualizerService:: GetValueDisplayStringCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b77e2537e7581bb15f6458b4515d407fcfa1f827
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222845"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Načte počet řetězců hodnot, které se mají zobrazit pro zadanou vlastnost nebo pole.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>Parametry
`displayKind`\
pro Hodnota z výčtu [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) .

`propertyOrField`\
pro Rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , které představuje vlastnost nebo pole.

`pcelt`\
mimo Vrátí počet řetězců hodnot, které se mají zobrazit.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
