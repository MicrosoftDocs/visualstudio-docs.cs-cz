---
description: Načte seznam cest kódu pro danou pozici ve zdrojovém souboru.
title: 'IDebugProgram2:: EnumCodePaths | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 057089c8c7b68fd1109c31bbfc0014f49a71368c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076040"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Načte seznam cest kódu pro danou pozici ve zdrojovém souboru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Parametry
`pszHint`\
pro Slovo pod kurzorem v zobrazení **zdroje** nebo zpětného **překladu** v integrovaném vývojovém prostředí (IDE)

`pStart`\
pro Objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) představující aktuální kontext kódu.

`pFrame`\
pro Objekt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) představující rámec zásobníku přidružený k aktuální zarážce.

`fSource`\
pro Nenulová ( `TRUE` ), pokud je v zobrazení **zdroje** , nebo nula (), pokud se nachází `FALSE` v zobrazení zpětného **překladu** .

`ppEnum`\
mimo Vrátí objekt [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) obsahující seznam cest kódu.

`ppSafety`\
mimo Vrátí objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , který představuje další kontext kódu, který se má nastavit jako zarážka pro případ, že se zvolená cesta k kódu přeskočí. K tomu může dojít v případě krátkodobého logického výrazu, například.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Cesta kódu popisuje název metody nebo funkce, která byla volána pro získání na aktuální bod při provádění programu. Seznam cest kódu představuje zásobník volání.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
