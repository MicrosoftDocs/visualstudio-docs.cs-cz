---
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa404f713a8982177cb28c48ddc83f332e5c5e56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899004"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Vrátí identifikátory GUID pro všechny možné moduly ladění (DE), které mohou ladit tento program.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Parametry
`celtBuffer`\
pro Počet identifikátorů DE GUID, které se mají vrátit. To také určuje maximální velikost `rgguidEngines` pole.

`rgguidEngines`\
[in, out] Pole identifikátoru GUID, které se mají vyplnit.

`pceltEngines`\
mimo Vrátí skutečný počet identifikátorů DE GUID, které jsou vráceny.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` nebo [C#] 0x8007007A, pokud vyrovnávací paměť není dostatečně velká.

## <a name="remarks"></a>Poznámky
 Aby bylo možné zjistit, kolik modulů existuje, zavolejte tuto metodu jednou s `celtBuffer` parametrem nastaveným na hodnotu 0 a `rgguidEngines` parametr nastavte na hodnotu null. Vrátí `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A pro C#) a `pceltEngines` parametr vrátí potřebnou velikost vyrovnávací paměti.

## <a name="see-also"></a>Viz také
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
