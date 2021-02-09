---
title: 'IDebugArrayObject:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9750b2982ad0b2d70375fe0519a9fd888bcac8a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870217"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Získá počet prvků v poli.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Parametry
`pdwElements`\
mimo Vrátí počet.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda vidí všechny prvky objektu Array jako jednorozměrné pole, a to i v případě, že je objekt Array multidimenzionální. Například pro dané pole `myarray[3][2][6]` by tato metoda vrátila 36 v `pdwElements` parametru. Použijte metodu [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) pro načtení jednotlivých prvků po jednom.

## <a name="see-also"></a>Viz také
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
