---
title: 'IDebugThread2:: CanSetNextStatement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4232c25bfe9acd7f17c88c28aa4211a9c62175f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718858"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Určuje, zda lze pro daný rámec zásobníku nastavit ukazatel na aktuální instrukci.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanSetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int CanSetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parametry
`pStackFrame`\
Vyhrazeno pro budoucí použití; Nastavte na hodnotu null. Pokud je tato hodnota null, použijte aktuální rámec zásobníku.

`pCodeContext`\
pro Objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , který popisuje umístění kódu, který má být spuštěn, a jeho kontext.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud tato metoda vrátí hodnotu `S_OK` , zavolejte metodu [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) , která ve skutečnosti nastaví další příkaz.

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
