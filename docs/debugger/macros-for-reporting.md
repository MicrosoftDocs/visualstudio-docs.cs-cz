---
title: Makra pro vytváření sestav | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b254323fac5d670cd44399cd8d22c9530c4510
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056599"
---
# <a name="macros-for-reporting"></a>Makra pro vytváření sestav
Pro ladění, můžete použít **_rptn –** a **_rptfn –** maker, definovaných v CRTDBG. H nahradit použití `printf` příkazy. Nemusíte je inclose **#ifdef**s, protože budou automaticky zmizí ve vaší verzi sestavení při **_DEBUG –** není definován.  
  
|– Makro|Popis|  
|-----------|-----------------|  
|**_RPT0 –**, **_RPT1 –**, **_RPT2 –**, **_RPT3 –**, **_RPT4 –**|Výstupy řetězec zprávy a nuly do čtyř argumentů. Pro _rpt1 – prostřednictvím **_rpt4 –**, řetězec zprávy slouží jako řetězec printf stylu formátování pro argumenty.|  
|**_RPTF0 –**, **_RPTF1 –**, **_RPTF2 –**, **_RPTF4 –**|Stejné jako **_rptn –**, ale tyto makra také výstupní soubor název a řádek číslo kde se nachází makro.|  
  
 Podívejte se na následující příklad:  
  
```cpp
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Tento kód výstupy hodnoty `someVar` a `otherVar` k **stdout**. Můžete použít následující volání `_RPTF2` ohlásí tyto stejné hodnoty a navíc v souboru název a číslo řádku:  
  
```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
Je možné, že konkrétní aplikaci potřebuje, ladění, které neposkytuje makra dodávaná s běhové knihovny jazyka C. Pro tyto případy můžete napsat makra navržená tak, aby vyhovovaly vašim požadavkům. V jednom z vaše soubory hlaviček, například můžete uvést kód jako následující příkaz pro definování makra názvem **ALERT_IF2**:  
  
```cpp
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Jednoho volání **ALERT_IF2** udělat všechny funkce **printf** kódu:  
  
```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Můžete snadno změnit vlastní makro nahlásit vyšší nebo nižší informace do různých umístění. Tento postup je zvlášť užitečné jako momentální požadavků na ladění.  
  
## <a name="see-also"></a>Viz také  
 [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)
