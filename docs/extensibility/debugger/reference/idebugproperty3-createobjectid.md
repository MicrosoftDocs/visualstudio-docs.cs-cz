---
description: Vytvoří jedinečné ID pro tuto vlastnost, aby bylo zajištěno, že je mezi všemi ostatními vlastnostmi jedinečné.
title: 'IDebugProperty3:: CreateObjectID | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e82e11d83c77131e47d815529813484d2869cdc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171436"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Vytvoří jedinečné ID pro tuto vlastnost, aby bylo zajištěno, že je mezi všemi ostatními vlastnostmi jedinečné.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána, když správce ladění relace chce ověřit, zda je tato vlastnost jednoznačně identifikována mezi všemi ostatními vlastnostmi. Ladicí stroj (DE) tuto metodu podporuje, pokud nejsou vlastnosti, se kterými pracuje, již jednoznačně identifikovány. Pokud DE nepodporuje tuto metodu, vrátí `E_NOTIMPL` .

 Jakékoli jedinečné ID, které bylo vytvořeno pomocí, `CreateObjectID` je zničeno při volání metody [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) ; to také signalizuje nutnost jednoznačně identifikovat tuto vlastnost.

> [!NOTE]
> Neexistuje žádná metoda pro načtení tohoto jedinečného ID, takže metoda DE může v případě volání metody dělat jakékoli jedinečné identifikátory `CreateObjectID` .

## <a name="see-also"></a>Viz také
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
