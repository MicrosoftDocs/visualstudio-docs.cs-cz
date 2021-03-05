---
description: Vytvoří enumerátor pro všechny místní proměnné metody, včetně těch, které jsou generovány interně kompilátorem.
title: 'IDebugMethodField:: EnumAllLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38f14ba2d520974b9f8f567c7840737ed2763080
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172165"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Vytvoří enumerátor pro všechny místní proměnné metody, včetně těch, které jsou generovány interně kompilátorem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
pro Objekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) představující adresu ladění v rámci metody, ukazující na konkrétní obor nebo kontext.

`ppLocals`\
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam všech národních prostředí v zadaném rozsahu. v opačném případě vrátí hodnotu null, která neindikuje žádné místní hodnoty.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud nejsou k dispozici žádné místní hodnoty. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Jsou vyhodnoceny pouze proměnné definované v rámci bloku, který obsahuje danou adresu pro ladění. Tato metoda zahrnuje všechny lokální hodnoty generované kompilátorem. Pokud jsou všechny potřeby definovány místně ve zdroji, zavolejte metodu [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) .

 Metoda může obsahovat více kontextů nebo bloků oborů.

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
