---
description: Získá typ třídy vlastního atributu.
title: 'IDebugCustomAttribute:: GetAttributeTypeField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0d0cfdfcdb49c934d9f4c0288f66a52e3e48f49
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088091"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
Získá typ třídy vlastního atributu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAttributeTypeField( 
   IDebugClassField** ppCAType
);
```

```csharp
int GetAttributeTypeField(
   out IDebugClassField ppCAType
);
```

## <a name="parameters"></a>Parametry
`ppCAType`\
mimo Vrátí objekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) , který představuje třídu, jejíž vlastní atribut je instance.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Vlastní atribut je vždy třída. Tato metoda poskytuje přístup k objektu [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) , který tuto třídu popisuje.

## <a name="see-also"></a>Viz také
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
