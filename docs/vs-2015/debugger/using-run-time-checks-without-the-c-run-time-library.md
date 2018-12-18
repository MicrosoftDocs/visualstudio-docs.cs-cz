---
title: Použití za běhu bez běhové knihovny jazyka C kontroluje | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4929b569c8d40413e948a4b208e7800afb39acb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816772"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Použití kontrol za běhu bez běhové knihovny jazyka C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud jste programu bez knihovny run-time jazyka C, pomocí **: / NODEFAULTLIB**a chcete použít kontroly za běhu, je třeba propojit s RunTmChk.lib.  
  
 `_RTC_Initialize` Inicializuje programu pro kontroly za běhu. Pokud nepropojíte s knihovny run-time jazyka C, je nutné zkontrolovat pro zjištění, jestli je váš program kompilován s kontroly chyb za běhu před voláním `_RTC_Initialize`, následujícím způsobem:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Pokud nepropojíte s knihovny run-time jazyka C, musíte také definovat funkci s názvem `_CRT_RTC_INITW`. `_CRT_RTC_INITW` uživatelem definované funkce se nainstaluje jako výchozí zpráv o chybách funkce, následujícím způsobem:  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Po dokončení instalace výchozí zpráv o chybách funkce můžete nainstalovat další zpráv o chybách funkce s `_RTC_SetErrorFuncW`. Další informace najdete v tématu [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití nativních kontrol za běhu](../debugger/how-to-use-native-run-time-checks.md)





