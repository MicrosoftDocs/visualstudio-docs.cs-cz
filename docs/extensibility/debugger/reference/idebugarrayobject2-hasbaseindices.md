---
title: 'IDebugArrayObject2:: HasBaseIndices | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- HasBaseIndices
- IDebugArrayObject2::HasBaseIndices
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48250b3328310c3f1cb1c84c8fe1a9c61c534cad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736141"
---
# <a name="idebugarrayobject2hasbaseindices"></a>IDebugArrayObject2::HasBaseIndices
Určuje, zda je v poli definováno základní indexy (dolní meze).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT HasBaseIndices (
   BOOL* pfHasBaseIndices
);
```

```csharp
int HasBaseIndices (
   out bool pfHasBaseIndices
);
```

## <a name="parameters"></a>Parametry
`pfHasBaseIndices`\
mimo TRUE pro určení, že pole má základní indexy (dolní meze); v opačném případě FALSE.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.
