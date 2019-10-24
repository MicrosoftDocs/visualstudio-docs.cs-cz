---
title: Pokračování v provádění po výjimce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7be214a950c8cc93d986f97834a848bd9ab824e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745651"
---
# <a name="continuing-execution-after-an-exception"></a>Pokračování v provádění po výjimce
Pokud ladicí program přeruší provádění z důvodu výjimky, ve výchozím nastavení se zobrazí **Pomocník pro výjimky**. Pokud jste zakázali **pomocníka výjimky** v dialogovém okně **Možnosti** , zobrazí se **Pomocník pro výjimky** (C# nebo Visual Basic) nebo dialogové okno **výjimky** (C++).

 Po zobrazení **pomocníka výjimky** se můžete pokusit opravit problém, který způsobil výjimku.

## <a name="managed-and-native-code"></a>Spravovaný a nativní kód
 Ve spravovaném a nativním kódu můžete pokračovat v provádění ve stejném vlákně po neošetřené výjimce. **Pomocné rutina výjimky** odvíjí zásobník volání do bodu, kde byla vyvolána výjimka.

## <a name="mixed-code"></a>Smíšený kód
 Pokud při ladění smíšeného nativního a spravovaného kódu dojde k neošetřené výjimce, omezení operačního systému zabrání odvinutí zásobníku volání. Pokud se pokusíte převinout zásobník volání pomocí místní nabídky, zobrazí se chybová zpráva s vysvětlením, že ladicí program nemůže provést zpětnou akci před neošetřenou výjimkou při ladění smíšeného kódu.

## <a name="see-also"></a>Viz také:

- [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)