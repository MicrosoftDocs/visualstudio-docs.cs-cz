---
title: IDebugStackFrame3::InterceptCurrentException | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 06d6c67724e6d8b66a34fc31412a1a925ba7c78c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934480"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Voláno rozhraním ladicího programu na aktuální rámec zásobníku, když chce zachytit aktuální výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Určuje různé akce. V současné době pouze [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) hodnotu `IEA_INTERCEPT` je podporován a musí být zadán.  
  
 `pqwCookie`  
 [out] Jedinečná hodnota identifikaci konkrétní výjimce.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; v opačném případě vrátí kód chyby.  
  
 Následují nejčastější vrátí chyba.  
  
|Chyba|Popis|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Nelze zachytit aktuální výjimku.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Aktuální rámec provádění ještě nebyl byla prohledána pro obslužnou rutinu.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Tato metoda není podporována pro tento rámec.|  
  
## <a name="remarks"></a>Poznámky  
 Když dojde k výjimce, ladicí program získá kontrolu v době běhu na klíčových místech během zpracování procesu výjimek. Během těchto klíčových momentů ladicí program můžete požádat o aktuální rámec zásobníku Pokud rámce chce zachytit výjimku. Tímto způsobem zachycené výjimky je v podstatě na průběžné obslužné rutiny výjimky pro blok zásobníku i v případě, že rámec zásobníku nemá obslužné rutiny výjimky (například bloku try/catch v kódu programu).  
  
 Pokud ladicí program se chce vědět, pokud by měl být zachycena výjimka, volá tuto metodu na aktuální objekt rámce zásobníku. Tato metoda je zodpovědná za zpracování všech podrobnosti o výjimce. Pokud [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) rozhraní není implementováno nebo `InterceptStackException` metoda vrátí všechny chyby, bude ladicí program pokračovat, obvykle zpracování výjimky.  
  
> [!NOTE]
>  Výjimky mohou být zachyceny pouze ve spravovaném kódu, to znamená, že při spuštění programu, který se právě ladí v .NET, dobu běhu. Samozřejmě můžete implementovat třetích stran jazyk implementátory `InterceptStackException` ve své vlastní ladicími stroji, pokud se tedy rozhodne.  
  
 Po dokončení zachycení [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) signalizován.  
  
## <a name="see-also"></a>Viz také  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)