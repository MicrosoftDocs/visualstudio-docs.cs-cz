---
description: Načte zadaný proces spuštěný na portu.
title: 'IDebugPort2:: getprocess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f3cf42e4f1316951ee50d110fe79b1191e4dc8e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142853"
---
# <a name="idebugport2getprocess"></a>IDebugPort2::GetProcess
Načte zadaný proces spuštěný na portu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProcess( 
   AD_PROCESS_ID    ProcessId,
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess( 
   AD_PROCESS_ID      ProcessId,
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parametry
`ProcessId`\
pro Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , která určuje identifikátor procesu.

`ppProcess`\
mimo Vrátí objekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) představující proces.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
