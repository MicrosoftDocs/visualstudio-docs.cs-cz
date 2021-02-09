---
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 265c77acdb15069c1fcd7f33d93d4ff74a528eca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896146"
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
