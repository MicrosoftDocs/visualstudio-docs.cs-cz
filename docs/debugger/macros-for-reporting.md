---
title: Makra pro vytváření sestav | Microsoft Docs
description: Přečtěte si o makrech ladění _RPTn a _RPTFn poskytovaných v souboru Crtdbg. H a o vytváření vlastních ladicích maker.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1920b4eddcbffa5cd51d548ade9af3a3a2f208d0
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903789"
---
# <a name="macros-for-reporting"></a>Makra pro vytváření sestav
Pro ladění můžete použít makra **_RPTn** a **_RPTFn** , která jsou definována v souboru Crtdbg. H, chcete-li nahradit použití `printf` příkazů. Nemusíte je nastavovat v **#ifdef** s, protože v buildu pro vydání automaticky zmizí, pokud není definován **_DEBUG** .

|Podokně|Popis|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3** **_RPT4**|Vytvoří výstup řetězce zprávy a 0 až čtyř argumentů. Pro **_RPT1** přes **_RPT4** řetězec zprávy slouží jako formátovací řetězec ve stylu printf pro argumenty.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF3** **_RPTF4**|Stejné jako **_RPTn**, ale tato makra také výstupují název souboru a číslo řádku, kde je makro umístěno.|

 Uvažujte následující příklad:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Tento kód vytvoří výstup hodnot z `someVar` a `otherVar` do **stdout**. Následující volání můžete použít k `_RPTF2` ohlášení stejných hodnot a kromě toho název souboru a číslo řádku:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Může se stát, že určitá aplikace potřebuje ladit hlášení, že makra dodaná pomocí knihovny run-time jazyka C neposkytují. V těchto případech můžete napsat makro navržené konkrétně pro splnění vlastních požadavků. V jednom z vašich hlavičkových souborů můžete například zahrnout kód podobný následujícímu pro definování makra s názvem **ALERT_IF2**:

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

 Jedno volání **ALERT_IF2** může provádět všechny funkce kódu **printf** :

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Můžete snadno změnit vlastní makro a ohlásit více nebo méně informací do různých míst. Tento přístup je užitečný hlavně v případě, že se vyvíjí vaše požadavky na ladění.

## <a name="see-also"></a>Viz také
- [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)
