---
title: Kontrola výjimky – Visual Studio | Microsoft Docs
ms.date: 1/18/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75d044ed5ddaf4b7eb7a66bc09c8b3de3502a50f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350495"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Kontrola výjimky pomocí pomocníka výjimky 

Řešení potíží s výjimkami je běžný problém bez ohledu na vaši technologii ani úroveň odbornosti. Může se jednat o frustrujícíé prostředí, které zjistí, proč výjimky způsobují problémy v kódu. Když ladíte výjimku v aplikaci Visual Studio, chceme tuto frustrace zmenšit tím, že poskytnete relevantní informace o výjimce, které vám pomůžou rychleji ladit váš problém.

![Pomocník pro výjimky](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Pozastavit na výjimku
Při přerušení ladicího programu na výjimku se zobrazí ikona chyby výjimky na pravé straně tohoto řádku kódu. V blízkosti ikony výjimky se zobrazí pomocník bez modální výjimky.

![Pomocný Pomocník pro výjimky vedle řádku kódu](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Kontrola informací o výjimce
Můžete okamžitě přečíst typ výjimky a zprávu o výjimce v Pomocníkovi výjimky a zda byla výjimka vyvolána nebo Neošetřená. Kliknutím na odkaz **Zobrazit podrobnosti** můžete zkontrolovat a zobrazit vlastnosti objektu výjimky.

## <a name="analyze-null-references"></a>Analyzovat odkazy s hodnotou null
Od sady Visual Studio 2017 pro kód .NET i C/C++, když zaškrtnete `NullReferenceException` nebo `AccessViolation` , uvidíte informace o analýze null v Pomocníkovi výjimky. Analýza se zobrazí jako text pod zprávou výjimky. Na následujícím obrázku jsou informace zobrazeny jako "**s** byly null".

![Analýza výjimky null pro pomoc](media/debugger-exception-helper-default.png)


> [!NOTE]
> Analýza odkazu s hodnotou null ve spravovaném kódu vyžaduje rozhraní .NET verze 4.6.2. Pro Univerzální platforma Windows (UWP) a žádné jiné aplikace .NET Core se momentálně nepodporuje analýza null. Je k dispozici pouze při ladění kódu, který neobsahuje žádné optimalizace kódu JIT (just-in-time).

## <a name="configure-exception-settings"></a>Konfigurovat nastavení výjimek 
Můžete nakonfigurovat, aby ladicí program mohl přerušit, pokud je vyvolána výjimka aktuálního typu z oddílu **Nastavení výjimek** pomocníka výjimky. Pokud je ladicí program pozastaven při vyvolané výjimce, můžete použít zaškrtávací políčko k zakázání přerušení pro daný typ výjimky při vyvolání v budoucnosti. Pokud nechcete přerušit tuto konkrétní výjimku při vyvolání v tomto konkrétním modulu, zaznačte zaškrtávací políčko podle názvu modulu v části **s výjimkou případů, kdy je vyvolána z:** v okně **Nastavení výjimek** . 

## <a name="inspect-inner-exceptions"></a>Kontrola vnitřních výjimek 
Pokud má výjimka nějaké vnitřní výjimky ([InnerException](https://docs.microsoft.com/dotnet/api/system.exception.innerexception), můžete je zobrazit v Pomocníkovi výjimky. Je-li k dispozici více výjimek, můžete mezi nimi přecházet pomocí levé a pravé šipky zobrazené výše v zásobníku volání.

![Výjimka pomocníka s vnitřní výjimkou](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Zkontrolovat znovu vyvolané výjimky
V případech, kdy došlo k výjimce `thrown` pomocníka výjimky, zobrazuje zásobník volání z prvního okamžiku, kdy byla výjimka vyvolána. Pokud byla výjimka vyvolána víckrát, zobrazí se pouze zásobník volání z původní výjimky.

![Pomocný Pomocník s výjimkami a výjimkami](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Sdílení ladicí relace s Live Share
Z pomocníka pro výjimky můžete spustit relaci [Live Share](https://docs.microsoft.com/visualstudio/liveshare/) pomocí **Live Share spustit relaci...**. Kdokoli, kdo se připojí k relaci Live Share, uvidí pomocníka výjimky spolu s dalšími informacemi o ladění.
