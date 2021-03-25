---
description: Tato metoda porovnává toto pole se zadaným polem pro rovnost.
title: 'IDebugField:: Equals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58673703fa0e585095c9a82fe2c7a4bc3e14827c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077106"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Tato metoda porovnává toto pole se zadaným polem pro rovnost.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Parametry
`pField`\
pro Pole, které se má porovnat s tímto polem

## <a name="return-value"></a>Návratová hodnota
 Pokud jsou pole stejná, vrátí `S_OK` . Pokud jsou pole odlišná, vrátí hodnotu `S_FALSE.` v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
