---
title: IDebugProgram2::EnumCodePaths | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a6ee294a94c59209cd50513a91664d27a7f94bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720615"
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
 [in] Slova pod kurzorem **zdroj** nebo **zpětný překlad** zobrazení v rozhraní IDE.  
  
 `pStart`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objekt představující aktuální kontext kódu.  
  
 `pFrame`  
 [in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objekt představující rámec zásobníku přidružené k aktuální zarážku.  
  
 `fSource`  
 [in] Nenulová (`TRUE`) při použití ve **zdroj** zobrazení, nebo nula (`FALSE`) při použití ve **zpětný překlad** zobrazení.  
  
 `ppEnum`  
 [out] Vrátí [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) objekt, který obsahuje seznam cest kódu.  
  
 `ppSafety`  
 [out] Vrátí [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objekt představující objekt context dalšího kódu nastavit jako zarážku v případě, že zvolený kódu cesta se přeskočí. To může nastat například v případě zkratována logický výraz.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Cesta kódu popisuje název metody nebo funkce, která se volá za účelem získání aktuální bod provádění programu. Seznam cest kódu představuje zásobník volání.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

