---
description: Vrátí identifikátor umístění kódu pro konkrétní kontext kódu.
title: 'IDebugDisassemblyStream2:: GetCodeLocationId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c1c3a6f7a9f2e2a0617f1322d17073a9dcc7c32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162924"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Vrátí identifikátor umístění kódu pro konkrétní kontext kódu.

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
pro Objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , který se má převést na identifikátor.

`puCodeLocationId` mimo Vrátí identifikátor umístění kódu. Viz poznámky.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí `E_CODE_CONTEXT_OUT_OF_SCOPE` , zda je kontext kódu platný, ale mimo obor.

## <a name="remarks"></a>Poznámky
 Identifikátor umístění kódu je specifický pro ladicí stroj (DE), který podporuje zpětný překlad. Tento identifikátor umístění se používá interně ke sledování pozic v kódu a obvykle je adresa nebo posun nějakého druhu. Jediným požadavkem je, že pokud je kontext kódu jednoho umístění menší než kontext kódu jiného umístění, pak odpovídající identifikátor umístění kódu prvního kontextu kódu musí být také menší než identifikátor umístění kódu druhého kontextu kódu.

 Chcete-li načíst kontext kódu pro identifikátor umístění kódu, zavolejte metodu [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .

## <a name="see-also"></a>Viz také
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
