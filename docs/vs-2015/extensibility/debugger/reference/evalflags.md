---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e6ee00402c13b2a79e4e6757a127211eda9c3c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149390"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje příznaky, které řídí vyhodnocení výrazu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Členové  
 EVAL_RETURNVALUE  
 Určuje, že návratová hodnota, pokud je vyhodnocena.  
  
 EVAL_NOSIDEEFFECTS  
 Určuje, že vedlejší účinky nejsou povoleny.  
  
 EVAL_ALLOWBPS  
 Určuje zastavení u zarážek.  
  
 EVAL_ALLOWERRORREPORT  
 Určuje zasílání zpráv o chybách do hostitele, který má být povolen. Primárně se používá pro vyhodnocení výrazu ve skriptu v aplikaci Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Vynutí vyhodnocení funkcí jako adres namísto vyvolání funkce.  
  
 EVAL_NOFUNCEVAL  
 Zabraňuje vyhodnocování funkce. Zvažte například `int` token ve výrazu `myExpression(int) + 10` . Tato funkce se může správně vyhodnotit jako adresa, ale ne jako hodnota.  
  
 EVAL_NOEVENTS  
 Příznak označující, že události, ke kterým dojde během vyhodnocení výrazu, by neměly být odesílány do Správce ladění relace (SDM) nebo do rozhraní IDE.  
  
## <a name="remarks"></a>Poznámky  
 Tyto příznaky jsou předány jako argument metodám [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) a [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .  
  
 Tyto příznaky mohou být kombinovány s bitovým nebo.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
