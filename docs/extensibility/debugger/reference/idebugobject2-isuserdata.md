---
title: IDebugObject2::-UserData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c53281ee144d3a1fa771fe4e77bba6bb418356e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953354"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Určuje, zda objekt představuje uživatelská data.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Parametry
`pfUser`\
mimo Vrátí nenulovou hodnotu ( `TRUE` ), pokud objekt představuje uživatelská data; nula ( `FALSE` ), pokud to není.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Uživatelská data jsou libovolný objekt, který je součástí modulu určeného jako JustMyCode (uživatelsky konfigurovatelné možnosti, které označí modul jako uživatelský kód, a proto je viditelný v trasování zásobníku).

## <a name="see-also"></a>Viz také
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
