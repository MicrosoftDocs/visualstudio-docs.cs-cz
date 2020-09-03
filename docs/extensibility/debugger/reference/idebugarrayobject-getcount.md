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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736208"
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
