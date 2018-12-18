---
title: Funkce háku sestavy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97d39a171d812915a1cf3c1c6450c73098067949
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284195"
---
# <a name="report-hook-functions"></a>Sestava funkcí háku
Funkce háku sestavy, nainstalovat pomocí [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), je volána pokaždé, když [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) generuje sestavu ladění. Můžete použít, mimo jiné pro filtrování sestav a zaměřte se na konkrétní typy přidělení. Funkce háku sestavy by měl mít prototyp vypadat asi takto:  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Ukazatel, který můžete předat **_CrtSetReportHook** je typu **_crt_report_hook –**, jak jsou definovány v CRTDBG. V:  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Při volání funkce háku, knihovny run-time *nRptType* argument obsahuje kategorie sestavy (**_CRT_WARN**, **_CRT_ERROR**, nebo **_CRT _ASSERT**), *szMsg* obsahuje ukazatel na řetězec zprávy sestaveném sestavy a *retVal* Určuje, zda `_CrtDbgReport` by měla pokračovat normální spuštění Po vygenerování sestavy nebo spuštění ladicího programu. (A *retVal* nulová hodnota pokračuje v provádění kódu, spustí ladicí program hodnotu 1.)  
  
 Pokud volání má na starosti dotyčný zpráva úplně, tak, aby další vykazování se nevyžaduje, měla by vrátit **TRUE**. Vrátí-li **FALSE**, `_CrtDbgReport` bude sestava zprávy normálně.  
  
## <a name="see-also"></a>Viz také  
 [Zápis funkce háku ladění](../debugger/debug-hook-function-writing.md)   
 [Ukázka crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
