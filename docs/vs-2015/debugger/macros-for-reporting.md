---
title: Makra pro vytváření sestav | Dokumentace Microsoftu
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
- vs.debug.macros
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc2a5226b3d6f512d2c2f89d9fef2a80eef34340
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758459"
---
# <a name="macros-for-reporting"></a>Makra pro vytváření sestav
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít **_RPTn**, a **_RPTFn** makra, definovaná v CRTDBG. H, chcete-li nahradit použití `printf` příkazy pro ladění. Tato makra automaticky zmizí ve svojí vydané verzi sestavení, když **_DEBUG** není definována, takže není nutné uvést v **#ifdef**s.  
  
|– Makro|Popis|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Vrací řetězec zprávy a 0 až čtyři argumenty. Pro _RPT1 prostřednictvím **_RPT4**, řetězec zprávy slouží jako řetězec stylu printf formátování pro argumenty.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|Stejné jako **_RPTn** , ale tato makra také výstup souboru název a číslo řádku kde se nachází makra.|  
  
 Vezměte v úvahu v následujícím příkladu:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Tento kód vracel hodnoty `someVar` a `otherVar` k **stdout**. Můžete použít následující volání do `_RPTF2` hlášení tyto hodnoty stejné a navíc souboru název a číslo řádku:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Pokud zjistíte, že konkrétní aplikaci potřebuje, ladění, které neposkytují součástí knihovny run-time C makra, můžete napsat makro navržené, aby vyhovovaly vašim požadavkům. Jedním ze souborů hlaviček, například můžete zahrnout kód jako následující definovat makro volá **ALERT_IF2**:  
  
```  
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
  
 Volání **ALERT_IF2** může provádět všechny funkce **printf** kód na začátku tohoto tématu:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Protože vlastní makra lze snadno změnit oznámit víc nebo míň informací do různých cílů (v závislosti na to, co je pohodlnější), tento přístup může být zvlášť užitečné, jak se vyvíjí vaše požadavky na ladění.  
  
## <a name="see-also"></a>Viz také  
 [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)



