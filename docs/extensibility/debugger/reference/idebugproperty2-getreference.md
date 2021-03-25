---
description: Vrátí odkaz na hodnotu vlastnosti.
title: 'IDebugProperty2:: getReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc8a922ad29b7f6b3ecff57ee5df7ad0e7dded1d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064758"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Vrátí odkaz na hodnotu vlastnosti.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

## <a name="parameters"></a>Parametry
`ppRererence`\
mimo Vrátí objekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) představující odkaz na hodnotu vlastnosti.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . jinak vrátí kód chyby, obvykle `E_NOTIMPL` nebo `E_GETREFERENCE_NO_REFERENCE` .

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
