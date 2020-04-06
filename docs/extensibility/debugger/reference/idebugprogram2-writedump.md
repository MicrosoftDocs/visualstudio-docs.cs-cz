---
title: IDebugProgram2::WriteDump | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722734"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Zapíše výpis do souboru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Parametry
`DumpType`\
[v] Hodnota z [výčtu DUMPTYPE,](../../../extensibility/debugger/reference/dumptype.md) který určuje typ výpisu, například krátké nebo dlouhé.

`pszDumpUrl`\
[v] Adresa URL pro zápis výpisu. Obvykle se jedná o formu `file://c:\path\filename.ext`, ale může se jedná o libovolnou platnou adresu URL.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Výpis programu by obvykle zahrnovat aktuální rámec zásobníku, zásobníku sám, seznam podprocesů spuštěných v programu a případně všechny paměti, které program vlastní.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
