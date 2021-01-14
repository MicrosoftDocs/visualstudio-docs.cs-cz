---
title: Funkce zavěšení sestav | Microsoft Docs
description: Kontrola funkcí zavěšení sestav v aplikaci Visual Studio. Funkce zavěšení sestav, která se instaluje pomocí _CrtSetReportHook, se volá pokaždé, když _CrtDbgReport vygeneruje sestavu ladění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dea558d2f125c1e64f46bb4fbf738434eda2394
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205616"
---
# <a name="report-hook-functions"></a>Sestava funkcí háku
Funkce zavěšení sestav, která se instaluje pomocí [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), se volá pokaždé, když [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) vygeneruje sestavu ladění. Můžete ho využít mimo jiné k filtrování sestav, abyste se mohli zaměřit na konkrétní typy přidělení. Funkce zavěšení sestav by měla mít prototyp podobný následujícímu:

```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);
```

 Ukazatel, který předáte **_CrtSetReportHook** , je typu **_CRT_REPORT_HOOK**, jak je definováno v souboru Crtdbg. Y

```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);
```

 Když knihovna run-time volá vaši funkci zavěšení, argument *nRptType* obsahuje kategorii sestavy (**_CRT_WARN**, **_CRT_ERROR** nebo **_CRT_ASSERT**), *szMsg* obsahuje ukazatel na plně sestavený řetězec zprávy sestavy a možnost *retval* určuje, zda `_CrtDbgReport` má pokračovat normální spuštění po vygenerování sestavy nebo spuštění ladicího programu. (Hodnota *retval* 0 pokračuje v provádění, hodnota 1 spustí ladicí program.)

 Pokud se tato zpráva zachytí úplně, takže se nevyžaduje žádné další hlášení, měla by vrátit **hodnotu true**. Pokud vrátí **hodnotu false**, `_CrtDbgReport` bude zpráva normálně hlásit.

## <a name="see-also"></a>Viz také
- [Zápis funkce zavěšení ladění](../debugger/debug-hook-function-writing.md)
- [Ukázka crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
