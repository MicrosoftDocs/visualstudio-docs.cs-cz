---
title: 'IDebugField:: GetTypeInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f74cc24d7698c3d83991c7f338bd2ef155ee1ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869788"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Tato metoda získá informace nezávislé na typu symbolu nebo typu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>Parametry
`pTypeInfo`\
mimo Vrátí informace o typu v zadané struktuře [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Informace nezávislé na typu by zahrnovaly například doménu AppDomain, modul a třídu obsahující symbol.

## <a name="see-also"></a>Viz také
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
