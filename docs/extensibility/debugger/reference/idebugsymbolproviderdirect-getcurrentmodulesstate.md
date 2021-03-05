---
description: Načte informace o skupině symbolů, které je poskytovatel symbolů členem.
title: 'IDebugSymbolProviderDirect:: GetCurrentModulesState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcc127bd3450f06a51ab0b04d61d52f4ee08e092
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149480"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
Načte informace o skupině symbolů, které je poskytovatel symbolů členem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCurrentModulesState(
    DWORD*          pState,
    unsigned long * count
);
```

```csharp
int GetCurrentModulesState(
    out uint pState,
    out uint count
);
```

## <a name="parameters"></a>Parametry
`pState`\
mimo Stav skupiny zprostředkovatel symbolů.

`count`\
mimo Počet modulů ve skupině.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Stav se změní pokaždé, když se do skupiny symbolů přidá nebo odebere modul. Proto lze tuto metodu použít k detekci, zda byla změněna skupina symbolů.

## <a name="see-also"></a>Viz také
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
