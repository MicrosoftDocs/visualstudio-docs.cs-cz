---
description: Získá prvek pole.
title: 'IDebugArrayObject:: GetElement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43659e8dfbd86f800105cbfa35fa3b3a13c099cf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094377"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Získá prvek pole.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Parametry
`dwIndex`\
pro Index elementu.

`ppElement`\
mimo Vrátí rozhraní [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , které představuje element.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda vidí všechny prvky objektu Array jako jednorozměrné pole, a to i v případě, že je objekt Array multidimenzionální. Například pro dané pole `myarray[3][2][6]` a `dwIndex` parametr 20 by tato metoda vrátila prvek z `myarray[1][1][2]` a `dwIndex` parametr 21 by vrátil prvek z `myarray[1][1][3]` . Použijte metodu [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) k určení celkového počtu prvků v poli.

## <a name="see-also"></a>Viz také
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
