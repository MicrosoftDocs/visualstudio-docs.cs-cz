---
title: IDebugProperty3::CreateObjectID | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721170"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Vytvoří jedinečné ID pro tuto vlastnost, aby bylo zajištěno, že je jedinečné mezi všemi ostatními vlastnostmi.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána, když správce ladění relace chce ujistěte se, že tato vlastnost je jednoznačně identifikován mezi všechny ostatní vlastnosti. Ladicí modul (DE) podporuje tuto metodu, pokud vlastnosti, které se zabývá již jednoznačně identifikovány. Pokud DE nepodporuje tuto metodu, vrátí `E_NOTIMPL`.

 Jakékoli jedinečné ID `CreateObjectID` vytvořené s je zničen, když je volána metoda [DestroyObjectID;](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) to také signalizuje konec potřeby jedinečně identifikovat tuto vlastnost.

> [!NOTE]
> Neexistuje žádná metoda pro načtení tohoto jedinečného ID, takže DE může `CreateObjectID` dělat, co chce pro jedinečné ID při volání metody.

## <a name="see-also"></a>Viz také
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
