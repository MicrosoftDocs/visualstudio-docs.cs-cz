---
description: Tato metoda umožňuje dodavateli portů zobrazit upozornění předtím, než se uživatel připojí k nebezpečnému procesu.
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e6a586983d64e8be27b15a0514234d1a321e943
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166161"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Tato metoda umožňuje dodavateli portů zobrazit upozornění předtím, než se uživatel připojí k nebezpečnému procesu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Návratová hodnota
 Návratové hodnoty jsou následující:

- `S_OK`: Připojení k procesu je bezpečné a nezobrazuje se dialogové okno s upozorněním.

- `S_FALSE`: Připojení může být problém zabezpečení a zobrazí se dialogové okno s upozorněním.

- `FAILURE`: Připojení k procesu selhalo.

## <a name="see-also"></a>Viz také
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
