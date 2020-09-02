---
title: Funkce zavěšení sestav | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a492a1db8b65cad74d02cec0f43bf0c81461730
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687513"
---
# <a name="report-hook-functions"></a>Sestava funkcí háku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkce zavěšení sestav, která se instaluje pomocí [_CrtSetReportHook](https://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), se volá pokaždé, když [_CrtDbgReport](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) vygeneruje sestavu ladění. Můžete ho využít mimo jiné k filtrování sestav, abyste se mohli zaměřit na konkrétní typy přidělení. Funkce zavěšení sestav by měla mít prototyp podobný následujícímu:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Ukazatel, který předáte **_CrtSetReportHook** , je typu **_CRT_REPORT_HOOK**, jak je definováno v souboru Crtdbg. Y  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Když knihovna run-time volá vaši funkci zavěšení, argument *nRptType* obsahuje kategorii sestavy (**_CRT_WARN**, **_CRT_ERROR**nebo **_CRT_ASSERT**), *szMsg* obsahuje ukazatel na plně sestavený řetězec zprávy sestavy a možnost *retval* určuje, zda `_CrtDbgReport` má pokračovat normální spuštění po vygenerování sestavy nebo spuštění ladicího programu. (Hodnota *retval* 0 pokračuje v provádění, hodnota 1 spustí ladicí program.)  
  
 Pokud se tato zpráva zachytí úplně, takže se nevyžaduje žádné další hlášení, měla by vrátit **hodnotu true**. Pokud vrátí **hodnotu false**, `_CrtDbgReport` bude zpráva normálně hlásit.  
  
## <a name="see-also"></a>Viz také  
 [Zápis funkce zavěšení ladění](../debugger/debug-hook-function-writing.md)   
 [Ukázka crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
