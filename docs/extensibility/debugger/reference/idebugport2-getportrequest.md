---
title: 'IDebugPort2:: GetPortRequest | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2694a0ee6e134a5f822c0f84284d96b7ce57ef93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907892"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Získá popis portu, který byl dříve použit k vytvoření portu (je-li k dispozici).

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
mimo Vrátí objekt [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) představující požadavek, který byl použit k vytvoření portu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  Vrátí `E_PORT_NO_REQUEST` , zda nebyl port vytvořen pomocí požadavku [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) portu.

## <a name="see-also"></a>Viz také
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
