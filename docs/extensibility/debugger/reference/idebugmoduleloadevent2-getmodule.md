---
title: IDebugModuleLoadEvent2::GetModule | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b90547709e5524ce005b0598b0b8d482cfecf173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726722"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Získá modul, který je právě načten nebo uvolněn.

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
[out] Vrátí objekt [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) který představuje modul, který je načítání nebo uvolnění.

`pbstrDebugMessage`\
[dovnitř, ven] Vrátí volitelnou zprávu popisující tuto událost. Pokud je tento parametr nulovou hodnotou, není požadována žádná zpráva.

`pbLoad`\
[dovnitř, ven] Nenulová`TRUE`( ), pokud se`FALSE`modul načítá, a nula ( ), pokud se modul vykládá. Pokud je tento parametr nulovou hodnotou, není požadován žádný stav.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
