---
title: IDebugDisassemblyStream2::GetCodeLocationId | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32be70e11776177a0e68f09689c2262497703ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732251"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Vrátí identifikátor umístění kódu pro určitý kontext kódu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>Parametry
`pCodeContext`\
[v] Objekt [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) který má být převeden na identifikátor.

`puCodeLocationId`[out] Vrátí identifikátor umístění kódu. Viz Poznámky.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `E_CODE_CONTEXT_OUT_OF_SCOPE` pokud kontext kódu je platný, ale mimo obor.

## <a name="remarks"></a>Poznámky
 Identifikátor umístění kódu je specifický pro ladicí modul (DE), který podporuje demontáž. Tento identifikátor umístění je používán interně DE ke sledování pozic v kódu a je obvykle adresa nebo posun nějakého druhu. Jediným požadavkem je, že pokud kontext kódu jednoho umístění je menší než kontext kódu jiného umístění, pak odpovídající identifikátor umístění kódu prvního kontextu kódu musí být také menší než identifikátor umístění kódu druhého kontextu kódu.

 Chcete-li načíst kontext kódu identifikátoru umístění kódu, zavolejte metodu [GetCodeContext.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

## <a name="see-also"></a>Viz také
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
