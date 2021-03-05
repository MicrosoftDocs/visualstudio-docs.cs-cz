---
description: Zobrazí zadané dialogové okno, ve kterém může uživatel vybrat port.
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c07e95343521692d41d045a89a4038f5ff64e7b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142554"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Zobrazí zadané dialogové okno, ve kterém může uživatel vybrat port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Parametry
`hwndParentDialog`\
pro Popisovač pro nadřazené dialogové okno

`pbstrPortId`\
mimo Řetězec identifikátoru portu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Návratová hodnota `S_FALSE` (nebo návratová hodnota `S_OK` s `BSTR` nastavením na `NULL` ) značí, že uživatel kliknul na **Zrušit**.

## <a name="see-also"></a>Viz také
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
