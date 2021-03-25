---
description: Vytvoří instanci ladicího stroje na serveru.
title: 'IDebugCoreServer3:: CreateInstanceInServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3511e67300725dc46e6d0e3978b2cb034b92d84e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058687"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Vytvoří instanci ladicího stroje na serveru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parametry
`szDll`\
pro Cesta ke knihovně DLL, která implementuje identifikátor CLSID zadaný v `clsidObject` parametru. V takovém případě `NULL` `CoCreateInstance` se zavolá funkce com.

`wLangId`\
pro Národní prostředí ladicího stroje. To může být 0, pokud by se metoda [setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) neměla volat.

`clsidObject`\
pro Identifikátor CLSID ladicího stroje, který se má vytvořit

`riid`\
pro ID rozhraní konkrétního rozhraní, které se má načíst z objektu třídy.

`ppvObject`\
[out] `IUnknown` rozhraní z vytvořeného objektu. Přetypování nebo zařazení tohoto objektu na požadované rozhraní.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
