---
title: 'IDebugProgram2:: GetENCUpdate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7e3dbb0fdc7ea7ca7560f62bc7da45e57b24383
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878900"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Tato metoda získá aktualizaci úpravy a pokračování (ENC) pro tento program. Vlastní modul ladění vždy vrátí `E_NOTIMPL` .

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
mimo Vrátí interní rozhraní, které lze použít k aktualizaci tohoto programu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

> [!NOTE]
> Vlastní ladicí stroj by měl vždycky vracet `E_NOTIMPL` .

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
