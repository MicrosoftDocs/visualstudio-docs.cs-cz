---
title: IDebugExceptionEvent2::P assToDebuggee | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecc7eb3830522cdee0022f4193482daab3780230
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150401"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, zda má být výjimka předána do programu laděného v případě, že spuštění pokračuje nebo zda by měla být výjimka zahozena.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fPass`  
 pro Nenulová ( `TRUE` ), pokud by měla být výjimka předána do programu laděného v případě, že spuštění pokračuje, nebo nula ( `FALSE` ), pokud by výjimka měla být zahozena.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Volání této metody ve skutečnosti nezpůsobí spuštění žádného kódu v laděném programu. Volání je pouze k nastavení stavu pro další spuštění kódu. Například volání metody [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) mohou vracet `S_OK` s [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` pole je nastaveno na `EXCEPTION_STOP_SECOND_CHANCE` .  
  
 Rozhraní IDE může přijmout událost [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) a volat metodu [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) . Ladicí stroj (DE) by měl mít výchozí chování pro zpracování případu, pokud metoda není `PassToDebuggee` volána.  
  
## <a name="see-also"></a>Viz také  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Pokračovat](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
