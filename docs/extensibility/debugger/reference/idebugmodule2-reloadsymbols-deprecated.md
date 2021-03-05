---
description: Zastaralé. Znovu načte symboly pro tento modul.
title: 'IDebugModule2:: ReloadSymbols_Deprecated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d07f80a3dccef666c0608d79505816f73ff52013
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150520"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
Zastaralé. NEPOUŽÍVEJTE. Znovu načte symboly pro tento modul.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Parametry
`pszUrlToSymbols`\
pro Cesta k úložišti symbolů.

`pbstrDebugMessage`\
mimo Vrátí informační zprávu, například stav nebo chybovou zprávu, která se zobrazí vpravo od názvu modulu v okně moduly.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Ladicí stroj by měl vždycky vracet `E_FAIL` .

## <a name="remarks"></a>Poznámky
 Tato metoda už není podporovaná. Místo toho Implementujte metodu [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) .

## <a name="see-also"></a>Viz také
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
