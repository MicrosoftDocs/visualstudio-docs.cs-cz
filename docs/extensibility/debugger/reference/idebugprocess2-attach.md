---
title: IDebugProcess2::Připojit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724190"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Připojí k procesu správce ladění relace (SDM).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
[v] Objekt [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) který se používá pro oznámení události ladění.

`rgguidSpecificEngines`\
[v] Pole identifikátorů GUID ladicích strojů, které mají být použity k ladění programů spuštěných v procesu. Tento parametr může být nulovou hodnotou. Podrobnosti najdete v části Poznámky.

`celtSpecificEngines`\
[v] Počet ladicích modulů `rgguidSpecificEngines` v poli a `rghrEngineAttach` velikost pole.

`rghrEngineAttach`\
[dovnitř, ven] Pole hresult kódy vrácené ladicí motory. Velikost tohoto pole je určena `celtSpecificEngines` v parametru. Každý kód je `S_OK` obvykle `S_ATTACH_DEFERRED`buď nebo . Ten označuje, že DE je aktuálně připojen k žádné programy.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. V následující tabulce jsou uvedeny další možné hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Zadaný proces je již připojen k ladicímu programu.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Během postupu připojení došlo k narušení zabezpečení.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Proces plochy nelze připojit k ladicímu programu.|

## <a name="remarks"></a>Poznámky
 Připojení k procesu připojí sdm ke všem programům spuštěným v tomto procesu, které mohou `rgguidSpecificEngines` být laděny ladicími moduly (DE) zadanými v poli. Nastavte `rgguidSpecificEngines` parametr na nulovou `GUID_NULL` hodnotu nebo zahrnout do pole připojit ke všem programům v procesu.

 Všechny ladicí události, ke kterým dochází v procesu jsou odesílány do daného objektu [IDebugCallBackback2.](../../../extensibility/debugger/reference/idebugeventcallback2.md) Tento `IDebugEventCallback2` objekt je k dispozici při volání SDM tuto metodu.

## <a name="see-also"></a>Viz také
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
