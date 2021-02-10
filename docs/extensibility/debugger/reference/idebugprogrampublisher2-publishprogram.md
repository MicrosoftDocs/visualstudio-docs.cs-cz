---
title: IDebugProgramPublisher2::P ublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d13154f172fdd92ea4a3d4c96321e884516a74c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959555"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Tato metoda vytvoří program dostupný pro moduly pro ladění (DEs) a správce ladění relace.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

## <a name="parameters"></a>Parametry
`Engines`\
pro Pole identifikátorů GUID pro algoritmus DEs, které lze spustit nebo připojit k tomuto programu.

`szFriendlyName`\
pro Popisný název programu (zobrazuje se v nabídkách nebo dialogových oknech prezentovaných uživateli).

`pDebuggeeInterface`\
[in] `IUnknown` rozhraní pro program (Tato hodnota se používá jako soubor cookie k jednoznačné identifikaci programu. Tato hodnota se používá k "zrušení publikování" programu).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Chcete-li program již nebude k dispozici pro ladění, zavolejte [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).

## <a name="see-also"></a>Viz také
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
