---
title: Atribut IDebugCustomAttribute::GetAttributeBytes | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 621ebf3949a273e06053ced67209aa052c25bce0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732799"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Získá informace o atributu jako objekt blob bajtů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Parametry
`ppBlob`\
[dovnitř, ven] Pole, které je vyplněno bajty atributu.

`pdwLen`\
[dovnitř, ven] Určuje maximální počet bajtů, které `ppBlob` mají být vráceny v poli, a vrátí počet bajtů skutečně zapsaných do pole.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Nastavte `ppBlob` parametr na hodnotu null, chcete-li vrátit počet dostupných bajtů atributů. Pak přidělit pole a předat `ppBlob` toto pole v pro parametr.

 Bajty atributu představují nezpracovaná data vlastního atributu.

## <a name="see-also"></a>Viz také
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
