---
description: Získá pole nebo proměnnou (pokud existuje), která může zálohovat vlastnost reprezentovanou tímto objektem.
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 210381e034ccae8ab9662b77c47970af2affa095
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053799"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Získá pole nebo proměnnou (pokud existuje), která může zálohovat vlastnost reprezentovanou tímto objektem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parametry
`ppObject`\
mimo Objekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) popisující pole zálohování.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Objekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) reprezentuje vlastnost třídy spravovaného kódu, to znamená metodu s přístupovým objektem Get nebo set. Tyto vlastnosti obecně vyžadují, aby proměnná obsahovala hodnotu, která je zpracována vlastností. Tato proměnná je označována jako pole pro zálohování. Pokud není k dispozici žádné pole pro daný objekt, je nutné vrátit hodnotu null: někteří volající nemůžou věnovat pozornost návratové hodnotě, ale místo toho budou chtít zjistit, jestli se v nevrátila hodnota null `ppObject` .

## <a name="see-also"></a>Viz také
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
