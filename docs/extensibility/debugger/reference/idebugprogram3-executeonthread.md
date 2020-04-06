---
title: IDebugProgram3::ExecuteOnThread | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722657"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Spustí program ladicího programu. Vlákno je vrácena poskytnout ladicí program informace o tom, které vlákno uživatel je zobrazení při provádění programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametry
`pThread`\
[v] Objekt [IDebugThread2.](../../../extensibility/debugger/reference/idebugthread2.md)

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Ladicí program může pokračovat v provádění po zastavení třemi různými způsoby:

- Spouštět: Zrušte všechny předchozí kroky a spouštět až do další zarážky a tak dále.

- Krok: Zrušte všechny staré kroky a spouštět, dokud se nový krok nedokončí.

- Pokračovat: Spusťte znovu a nechte všechny staré kroky aktivní.

  Vlákno předané `ExecuteOnThread` do je užitečné při rozhodování, který krok zrušit. Pokud neznáte vlákno, spuštění spustit zruší všechny kroky. Se znalostí vlákna stačí zrušit krok v aktivním vlákně.

## <a name="see-also"></a>Viz také
- [Spuštění](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
