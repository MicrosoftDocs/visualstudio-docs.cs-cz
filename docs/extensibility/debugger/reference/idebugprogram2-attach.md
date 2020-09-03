---
title: 'IDebugProgram2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d0b182ba7a873816e3a7aa32d39beb2c63cc5ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723135"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Připojí se k programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
pro Objekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , který se má použít pro oznámení události ladění.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. V následující tabulce jsou uvedeny některé možné kódy chyb.

|Hodnota|Popis|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Zadaný program je již k ladicímu programu připojen.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Během procesu připojení došlo k narušení zabezpečení.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Desktopový program nelze připojit k ladicímu programu.|

## <a name="remarks"></a>Poznámky
 Ladicí stroj (DE) nikdy nevolá tuto metodu, aby se připojil k programu. Pokud je v adresním prostoru programu DE spuštěn, je volána metoda [Attach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Pokud je DE spuštěna v adresním prostoru Správce ladění relace (SDM), je volána metoda [připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
