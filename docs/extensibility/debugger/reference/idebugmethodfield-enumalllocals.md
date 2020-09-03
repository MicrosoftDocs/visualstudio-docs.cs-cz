---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727340"
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
