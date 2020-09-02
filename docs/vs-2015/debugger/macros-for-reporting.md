---
title: Makra pro vytváření sestav | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: e4aee33d571f95e24a359fa2bc7e12ae8d64eae0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431625"
---
# <a name="macros-for-reporting"></a>Makra pro vytváření sestav
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít **_RPTn**a **_RPTFn** makra definovaná v souboru Crtdbg. H, chcete-li nahradit použití `printf` příkazů pro ladění. Tato makra v sestavení vydaných verzí automaticky zmizí, když **_DEBUG** není definován, takže je nemusíte sestavovat v **#ifdef**s.  
  
|Podokně|Popis|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3** **_RPT4**|Vytvoří výstup řetězce zprávy a 0 až čtyř argumentů. Pro _RPT1 přes **_RPT4**řetězec zprávy slouží jako formátovací řetězec ve stylu printf pro argumenty.|  
|**_RPTF0**, **_RPTF1**, **_RPTF2** **_RPTF4**|Stejné jako **_RPTn** , ale tato makra také výstupují název souboru a číslo řádku, kde je makro umístěno.|  
  
 Uvažujte následující příklad:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Tento kód vytvoří výstup hodnot z `someVar` a `otherVar` do **stdout**. Následující volání můžete použít k `_RPTF2` ohlášení stejných hodnot a kromě toho název souboru a číslo řádku:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Pokud zjistíte, že určitá aplikace potřebuje ladění sestav, které makra dodaná s knihovnou run-time jazyka C neposkytují, můžete napsat makro navržené konkrétně tak, aby vyhovovalo vašim požadavkům. V jednom z vašich hlavičkových souborů můžete například zahrnout kód podobný následujícímu pro definování makra s názvem **ALERT_IF2**:  
  
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
  
 Jedno volání **ALERT_IF2** může na začátku tohoto tématu provádět všechny funkce kódu **printf** :  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Vzhledem k tomu, že vlastní makro lze snadno změnit tak, aby nahlásilo více nebo méně informací do různých cílů (v závislosti na tom, co je pohodlnější), může být tento přístup zvláště užitečný, když se vyvíjí vaše požadavky na ladění.  
  
## <a name="see-also"></a>Viz také  
 [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)
