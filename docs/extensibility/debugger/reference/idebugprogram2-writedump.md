---
description: Zapíše výpis do souboru.
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8eca50eb6e828841a247ed51d7f73f61cb63e0e9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084425"
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
pro Hodnota z výčtu [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) , která určuje typ výpisu, například short nebo Long.

`pszDumpUrl`\
pro Adresa URL pro zápis výpisu paměti. Obvykle je to ve formě `file://c:\path\filename.ext` , ale může to být jakákoli platná adresa URL.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Výpis programu by obvykle zahrnoval aktuální rámec zásobníku, samotný zásobník, seznam vláken spuštěných v programu a případně jakoukoli paměť, kterou program vlastní.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
