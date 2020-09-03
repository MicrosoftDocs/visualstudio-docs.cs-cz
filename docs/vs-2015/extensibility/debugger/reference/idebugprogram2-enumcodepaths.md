---
title: 'IDebugProgram2:: EnumCodePaths | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4d34b1b6519407e02d4340a5108ef03cece12b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202765"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Načte seznam cest kódu pro danou pozici ve zdrojovém souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 `pszHint`  
 pro Slovo pod kurzorem v zobrazení **zdroje** nebo zpětného **překladu** v integrovaném vývojovém prostředí (IDE)  
  
 `pStart`  
 pro Objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) představující aktuální kontext kódu.  
  
 `pFrame`  
 pro Objekt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) představující rámec zásobníku přidružený k aktuální zarážce.  
  
 `fSource`  
 pro Nenulová ( `TRUE` ), pokud je v zobrazení **zdroje** , nebo nula (), pokud se nachází `FALSE` v zobrazení zpětného **překladu** .  
  
 `ppEnum`  
 mimo Vrátí objekt [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) obsahující seznam cest kódu.  
  
 `ppSafety`  
 mimo Vrátí objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , který představuje další kontext kódu, který se má nastavit jako zarážka pro případ, že se zvolená cesta k kódu přeskočí. K tomu může dojít v případě krátkodobého logického výrazu, například.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Cesta kódu popisuje název metody nebo funkce, která byla volána pro získání na aktuální bod při provádění programu. Seznam cest kódu představuje zásobník volání.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
