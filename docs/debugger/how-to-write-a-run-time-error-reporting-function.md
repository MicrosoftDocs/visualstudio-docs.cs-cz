---
title: Zápis funkce zasílání zpráv o chybách za běhu | Microsoft Docs
description: Podívejte se na příklady psaní vlastních funkcí zasílání zpráv o chybách za běhu v aplikaci Visual Studio. Musí mít stejnou deklaraci jako _CrtDbgReportW a vracet hodnotu 1.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23f5234cb0184de14f7506fd540004a200a65a4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925353"
---
# <a name="how-to-write-a-run-time-error-reporting-function-c"></a>Postupy: zápis funkce zasílání zpráv o chybách Run-Time (C++)
Vlastní funkce vytváření sestav pro běhové chyby musí mít stejnou deklaraci jako `_CrtDbgReportW` . Měl by vrátit hodnotu 1 ladicímu programu.

Následující příklad ukazuje, jak definovat vlastní funkci generování sestav.

## <a name="example-1"></a>Příklad 1

```cpp
#include <stdio.h>
int errorhandler = 0;
void configureMyErrorFunc(int i)
{
    errorhandler = i;
}

int MyErrorFunc(int errorType, const wchar_t *filename,
                int linenumber, const wchar_t *moduleName,
                const wchar_t *format, ...)
{
    switch (errorhandler)
    {
    case 0:
    case 1:
        wprintf(L"Error type %d at %s line %d in %s",
                errorType, filename, linenumber, moduleName);
        break;
    case 2:
    case 3:
        fprintf(stderr, "Error type");
        break;
    }

    return 1;
}
```

## <a name="example-2"></a>Příklad 2
Následující příklad ukazuje komplexnější vlastní funkci generování sestav. V tomto příkladu příkaz switch zpracovává různé typy chyb, jak jsou definovány `reportType` parametrem `_CrtDbgReportW` . Protože nahrazujete `_CrtDbgReportW` , nemůžete použít `_CrtSetReportMode` . Vaše funkce musí zpracovat výstup. První argument proměnné v této funkci přebírá běhové číslo chyby. Další informace najdete v tématu [_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype).

```cpp
#include <windows.h>
#include <stdarg.h>
#include <rtcapi.h>
#include <malloc.h>
#pragma runtime_checks("", off)
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,
                      const wchar_t *module, const wchar_t *format, ...)
{
    // Prevent re-entrance.
    static long running = 0;
    while (InterlockedExchange(&running, 1))
        Sleep(0);
    // Now, disable all RTC failures.
    int numErrors = _RTC_NumErrors();
    int *errors=(int*)_alloca(numErrors);
    for (int i = 0; i < numErrors; i++)
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);

    // First, get the rtc error number from the var-arg list.
    va_list vl;
    va_start(vl, format);
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);
    va_end(vl);

    wchar_t buf[512];
    const char *err = _RTC_GetErrDesc(rtc_errnum);
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",
        err,
        line,
        file ? file : L"Unknown",
        module ? module : L"Unknown");
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;
    // Now, restore the RTC errortypes.
    for(int i = 0; i < numErrors; i++)
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);
    running = 0;
    return res;
}
#pragma runtime_checks("", restore)
```

## <a name="example-3"></a>Příklad 3
Použijte `_RTC_SetErrorFuncW` k instalaci vlastní funkce místo `_CrtDbgReportW` . Další informace najdete v tématu [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw). `_RTC_SetErrorFuncW`Návratová hodnota je předchozí funkce vytváření sestav, kterou můžete v případě potřeby uložit a obnovit.

```cpp
#include <rtcapi.h>
int main()
{
    _RTC_error_fnW oldfunction, newfunc;
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);
    // Run some code.
    newfunc = _RTC_SetErrorFuncW(oldfunction);
    // newfunc == &MyErrorFunc;
    // Run some more code.
}
```

## <a name="see-also"></a>Viz také
[Nativní Run-Time kontroluje přizpůsobení.](../debugger/native-run-time-checks-customization.md)
