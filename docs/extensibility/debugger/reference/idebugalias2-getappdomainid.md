---
title: 'IDebugAlias2:: GetAppDomainId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca8f2311b58fc7e73f9eb4f4c14f993c88b9a62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736413"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Načte identifikátor pro doménu aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Parametry
`pappDomainId`\
mimo Vrátí identifikátor domény aplikace.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Identifikátor domény aplikace se změní pokaždé, když se aplikace restartuje a vytvoří se nová doména aplikace.

## <a name="see-also"></a>Viz také
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
