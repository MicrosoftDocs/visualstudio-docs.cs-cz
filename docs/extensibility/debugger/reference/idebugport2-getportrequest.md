---
title: IDebugPort2::GetPortRequest | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48d39ea10e8425d5449444514489ac4b73c0a3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725330"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Získá popis portu, který byl dříve použit k vytvoření portu (pokud je k dispozici).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Parametry
`ppRequest`\
[out] Vrátí objekt [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) představující požadavek, který byl použit k vytvoření portu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.  Vrátí, `E_PORT_NO_REQUEST` pokud port nebyl vytvořen pomocí požadavku na port [IDebugPortRequest2.](../../../extensibility/debugger/reference/idebugportrequest2.md)

## <a name="see-also"></a>Viz také
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
