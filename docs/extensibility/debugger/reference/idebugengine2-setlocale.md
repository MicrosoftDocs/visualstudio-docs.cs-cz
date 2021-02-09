---
title: 'IDebugEngine2:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e43d8d13f34b8477ab870c80842ff33eef72a7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878913"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Nastaví národní prostředí ladicího modulu (DE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>Parametry
`wLangID`\
pro Určuje národní prostředí jazyka. Například 1033 pro angličtinu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána správcem ladění relace (SDM) pro rozšíření nastavení národního prostředí rozhraní IDE, aby byly řetězce vracené nástrojem DE správně lokalizovány.

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
