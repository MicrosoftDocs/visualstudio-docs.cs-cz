---
description: Nastaví poskytovatele služby.
title: 'IDebugPortPicker:: SetSite | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a442c438f233187265c90e724f57e8681b95556
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072256"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Nastaví poskytovatele služby.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>Parametry
`pSP`\
pro Odkaz na rozhraní poskytovatele služeb

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda bude volána před voláním jakékoli jiné metody.

## <a name="see-also"></a>Viz také
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
