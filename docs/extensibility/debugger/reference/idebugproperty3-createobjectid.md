---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721170"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Vytvoří jedinečné ID pro tuto vlastnost, aby bylo zajištěno, že je mezi všemi ostatními vlastnostmi jedinečné.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
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
