---
title: 'IDebugArrayObject2:: GetBaseIndices | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925ce3a7bcce9f787e02c2bd2714f8b26d8cec26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736150"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Načte základní indexy (dolní meze) pro každý index s ohledem na počet rozměrů v poli.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

## <a name="parameters"></a>Parametry
`dwRank`\
pro Počet dimenzí (Rank) pole.

`dwIndices`\
mimo Základní indexy (dolní meze) pro pole

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Jako příklad by tato funkce vrátila ' 5 ' pro pole vytvořené následujícím kódem jazyka C#:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>Viz také
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
