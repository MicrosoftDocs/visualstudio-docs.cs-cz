---
description: Odpojí ladicí program od tohoto procesu odpojením všech programů v procesu.
title: IDebugProcess2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5775ee9ffc3fa3c4151df999b64ba1160da6f7c3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166278"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Odpojí ladicí program od tohoto procesu odpojením všech programů v procesu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Všechny programy a proces jsou nadále spuštěny, ale již nejsou součástí ladicí relace. Po dokončení operace odpojení nebudou odeslány žádné další události ladění pro tento proces (a jeho programy).

## <a name="see-also"></a>Viz také
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
