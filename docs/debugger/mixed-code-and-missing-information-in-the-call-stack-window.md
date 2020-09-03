---
title: Smíšený kód a chybějící informace v okně zásobník volání | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25fb7bc54899d8c9a079d3f2706065d690904540
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "73187534"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Smíšený kód a chybějící informace v okně Zásobník volání
Z důvodu rozdílů mezi zásobníky volání pro spravovaný a nativní kód nemůže ladicí program vždy zobrazit kompletní zásobník volání, když jsou typy kódu smíšeny. Pokud nativní kód volá spravovaný kód, můžete si všimnout následujících nedostatků v okně **zásobník volání** :

- V okně **zásobník volání** může chybět nativní rámec hned nad spravovaným kódem. Další informace naleznete v tématu [Postup: krokování ze spravovaného kódu, pokud v okně zásobník volání chybějí nativní rámce](how-to-use-the-call-stack-window.md).

- V případě aplikací se smíšeným režimem, které jsou spouštěny mimo ladicí program, může okno **zásobník volání** zobrazit pouze spravovaný kód a žádný z nativních snímků nebude viditelný.

  Oba případy jsou poměrně zřídka. Ve většině nativních volání spravovaného kódu se zásobníky volání zobrazují správně.

## <a name="see-also"></a>Viz také
- [Postupy: Použití okna Zásobník volání](../debugger/how-to-use-the-call-stack-window.md)