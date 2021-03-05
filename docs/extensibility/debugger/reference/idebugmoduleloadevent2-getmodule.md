---
description: Načte modul, který je načítán nebo uvolněn.
title: 'IDebugModuleLoadEvent2:: GetModule | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e44268dcf4ab79e99bd1bdf5a996ae18762e139
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149831"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Načte modul, který je načítán nebo uvolněn.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Parametry
`pModule`\
mimo Vrátí objekt [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , který představuje modul, který je načítán nebo uvolňován.

`pbstrDebugMessage`\
[in, out] Vrátí volitelnou zprávu popisující tuto událost. Pokud má tento parametr hodnotu null, nepožaduje se žádná zpráva.

`pbLoad`\
[in, out] Nenulová ( `TRUE` ), pokud se modul načítá a je nula ( `FALSE` ), pokud se modul uvolňuje. Pokud má tento parametr hodnotu null, není požadován žádný stav.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
