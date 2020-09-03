---
title: IDebugProcessEx2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7379436ae0da57d7f8c47ce8484c810a53a0a453
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723355"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Tato metoda informuje o procesu, že relace již neprovádí ladění procesu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametry
`pSession`\
pro Hodnota, která jedinečně identifikuje relaci pro odpojování tohoto procesu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Předané rozhraní `pSession` je považováno za soubor cookie, což je hodnota, která jednoznačně identifikuje Správce ladění relace, který byl původně připojen k tomuto procesu; žádná z metod v zadaném rozhraní není funkční.

## <a name="see-also"></a>Viz také
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
