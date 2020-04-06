---
title: IDebugThread2::SetNextStatement | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b390e5c021fa069ae3fb09eef1978caaf9cc8ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718650"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Nastaví aktuální ukazatel instrukce na kontext daného kódu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parametry
`pStackFrame`\
Vyhrazeno pro budoucí použití; nastavena na hodnotu null.

`pCodeContext`\
[v] Objekt [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) který popisuje umístění kódu, které má být spuštěno, a jeho kontext.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. V následující tabulce jsou uvedeny další možné hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Další příkaz nemůže být v rámci zásobníku hlouběji v zásobníku rámce.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Další příkaz není přidružen k žádnému rámci v zásobníku.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Některé ladicí moduly nemohou po výjimce nastavit další příkaz.|

## <a name="remarks"></a>Poznámky
 Ukazatel instrukce označuje další instrukce nebo příkaz ke spuštění. Tato metoda se používá k opakování řádku zdrojového kódu nebo vynutit spuštění pokračovat v jiné funkci, například.

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
