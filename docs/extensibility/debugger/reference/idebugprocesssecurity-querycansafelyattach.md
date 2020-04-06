---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723209"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Tato metoda umožňuje dodavateli portu zobrazit upozornění před uživatelem připojí k nebezpečnému procesu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Návratová hodnota
 Vrácené hodnoty jsou následující:

- `S_OK`: Připojení k procesu je bezpečné a nezobrazí se žádné dialogové okno s upozorněním.

- `S_FALSE`: Připojení může být problém se zabezpečením a zobrazí se dialogové okno s upozorněním.

- `FAILURE`: Připojení ke zpracování se nezdaří.

## <a name="see-also"></a>Viz také
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
