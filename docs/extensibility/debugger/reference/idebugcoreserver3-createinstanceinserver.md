---
title: IDebugCoreServer3::CreateInstanceInServer | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2346bb76fe604265a309a51f48b734fc6f2ab8d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733015"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Vytvoří instanci ladicího modulu na serveru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
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
[v] Cesta k dll, který implementuje CLSID zadaný v parametru. `clsidObject` Pokud je `NULL`to , `CoCreateInstance` pak com funkce je volána.

`wLangId`\
[v] Národní prostředí ladicího modulu. To může být 0, pokud [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) metoda by neměla být volána.

`clsidObject`\
[v] CLSID ladicího modulu k vytvoření.

`riid`\
[v] ID rozhraní konkrétní rozhraní načíst z objektu třídy.

`ppvObject`\
[out] `IUnknown` rozhraní z instanciovaného objektu. Přetypovací nebo zařazovací tento objekt na požadované rozhraní.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
