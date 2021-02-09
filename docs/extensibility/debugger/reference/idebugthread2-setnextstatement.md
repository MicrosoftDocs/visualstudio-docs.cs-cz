---
title: 'IDebugThread2:: SetNextStatement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c8a7aff8c6e902b20c5569e2553aececae835ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893708"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Nastaví ukazatel na aktuální instrukci na daný kontext kódu.

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
Vyhrazeno pro budoucí použití; Nastavte na hodnotu null.

`pCodeContext`\
pro Objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , který popisuje umístění kódu, který má být spuštěn, a jeho kontext.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. V následující tabulce jsou uvedeny další možné hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Následující příkaz nemůže být v bloku zásobníku hlubší v zásobníku snímků.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Následující příkaz není přidružen k žádnému snímku v zásobníku.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Některé ladicí moduly nemůžou po výjimce nastavit další příkaz.|

## <a name="remarks"></a>Poznámky
 Ukazatel na instrukci označuje další instrukci nebo příkaz, který se má provést. Tato metoda slouží k opakování řádku zdrojového kódu nebo k vynucení spuštění v jiné funkci, například.

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
