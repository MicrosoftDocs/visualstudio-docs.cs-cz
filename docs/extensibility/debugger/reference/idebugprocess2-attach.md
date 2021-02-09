---
title: 'IDebugProcess2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 462b2299a658359e81fc3641e590b95ab183a24e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874175"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Připojí k procesu Správce ladění relace (SDM).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
pro Objekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , který se používá pro oznámení události ladění.

`rgguidSpecificEngines`\
pro Pole identifikátorů GUID ladicích modulů, které se mají použít k ladění programů spuštěných v procesu. Tento parametr může být hodnota null. Podrobnosti najdete v části poznámky.

`celtSpecificEngines`\
pro Počet ladicích modulů v `rgguidSpecificEngines` poli a velikost `rghrEngineAttach` pole.

`rghrEngineAttach`\
[in, out] Pole kódů HRESULT vrácených ladicími moduly. Velikost tohoto pole je uvedena v `celtSpecificEngines` parametru. Každý kód je obvykle buď `S_OK` nebo `S_ATTACH_DEFERRED` . Druhá označuje, že je DE aktuálně připojená k žádnému programu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. V následující tabulce jsou uvedeny další možné hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Zadaný proces je již k ladicímu programu připojen.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Během procesu připojení došlo k narušení zabezpečení.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Pracovní proces nelze připojit k ladicímu programu.|

## <a name="remarks"></a>Poznámky
 Připojení k procesu připojí model SDM ke všem programům spuštěným v tomto procesu, které lze ladit pomocí ladicích modulů (DE) určených v `rgguidSpecificEngines` poli. Nastavte `rgguidSpecificEngines` parametr na hodnotu null nebo zahrňte do `GUID_NULL` pole, které se připojí ke všem programům v procesu.

 Všechny události ladění, které se vyskytnou v procesu, se odesílají na daný objekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) . Tento `IDebugEventCallback2` objekt je k dispozici, když model SDM volá tuto metodu.

## <a name="see-also"></a>Viz také
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
