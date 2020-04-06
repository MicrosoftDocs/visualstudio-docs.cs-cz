---
title: IDebugProgram2::GetENCUpdate | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e90ff9f8a7a80913aec72b9fe2bb6fe470013d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722836"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Tato metoda získá upravit a pokračovat (ENC) aktualizace pro tento program. Vlastní ladicí modul `E_NOTIMPL`vždy vrátí .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Parametry
`ppUpdate`\
[out] Vrátí interní rozhraní, které lze použít k aktualizaci tohoto programu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

> [!NOTE]
> Vlastní ladicí modul `E_NOTIMPL`by měl vždy vrátit .

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
