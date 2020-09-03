---
title: 'IDebugCustomAttribute:: GetAttributeTypeField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51341b3c9b351307d2662538cc3a6797c58b62f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732779"
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
