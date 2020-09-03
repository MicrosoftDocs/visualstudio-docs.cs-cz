---
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0a02169b37bba804034990ed5d972f973244769
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724887"
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
