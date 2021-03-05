---
description: Nastaví hodnotu vlastnosti z daného řetězce.
title: 'IDebugProperty2:: SetValueAsString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b86de71cd6df3e028697518de8c6faccad7e2336
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166720"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Nastaví hodnotu vlastnosti z daného řetězce.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parametry
`pszValue`\
pro Řetězec obsahující hodnotu, kterou chcete nastavit.

`nRadix`\
pro Číselná soustava, která se má použít při interpretaci libovolných číselných informací. To může být 0 pro pokus o určení základu automaticky.

`dwTimeout`\
pro Určuje maximální dobu v milisekundách, po kterou se má čekat, než se vrátí z této metody. Použijte `INFINITE` k čekání na neomezenou dobu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . jinak vrátí kód chyby. V následující tabulce jsou uvedeny další možné hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Řetězec nelze převést na hodnotu vlastnosti nebo hodnotu vlastnosti nelze nastavit.|
|`E_SETVALUE_VALUE_IS_READONLY`|Vlastnost je určena jen pro čtení.|

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
