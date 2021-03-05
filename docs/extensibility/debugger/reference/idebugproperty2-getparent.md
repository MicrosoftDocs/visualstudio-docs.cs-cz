---
description: Získá nadřazenou vlastnost vlastnosti.
title: 'IDebugProperty2:: GetParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ae5557734ab59a2e71a67404a50519d72ca1ec0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166824"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
Získá nadřazenou vlastnost vlastnosti.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetParent ( 
   IDebugProperty2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugProperty2 ppParent
);
```

## <a name="parameters"></a>Parametry
`ppParent`\
mimo Vrátí objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , který představuje nadřazenou vlastnost.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . jinak vrátí kód chyby. Vrátí `S_GETPARENT_NO_PARENT` , pokud není k dispozici žádný nadřazený objekt.

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
