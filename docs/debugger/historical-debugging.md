---
title: Historické ladění | Microsoft Docs
description: Vyřešte potíže s aplikací tak, že zkontrolujete její stav při přesunu zpět a vpřed po jejím spuštění. IntelliTrace shromažďuje informace o této funkci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38166f777153206ad4b862ac473226aecdff4147
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398542"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Historické ladění (C#, Visual Basic, C++)

Historické ladění je režim ladění, který závisí na informacích shromažďovaných pomocí IntelliTrace. Umožňuje přesunout zpět a vpřed v průběhu provádění aplikace a zkontrolovat její stav.

 IntelliTrace můžete použít v edici Visual Studio Enterprise (ale ne v edicích Professional nebo Community).

## <a name="why-use-historical-debugging"></a>Proč používat historické ladění?

 Nastavení zarážek pro hledání chyb může být místo toho Affair nebo neúspěšný. Nastavte zarážku blízko na místo v kódu, kde máte podezření, že se jedná o chybu, potom spusťte aplikaci v ladicím programu a doufáme, že se zarážka spustí, a že místo, kde se přerušení provádění může odhalit zdroj chyby. V opačném případě budete muset zkusit nastavit zarážku někde jinde v kódu a znovu spustit ladicí program, který provede testovací kroky před a nad, dokud problém nezjistíte.

 ![Nastavení zarážky](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 Můžete použít IntelliTrace a historické ladění pro pohyb v aplikaci a zkontrolovat její stav (zásobník volání a místní proměnné) bez nutnosti nastavovat zarážky, znovu spustit ladění a opakovat kroky testu. To vám může ušetřit spoustu času, zejména v případě, že se chyba nachází hluboko v testovacím scénáři, který trvá dlouhou dobu.

## <a name="how-do-i-start-using-historical-debugging"></a>Návody začít používat historické ladění?

IntelliTrace je ve výchozím nastavení zapnuté. Stačí, abyste se rozhodli, které události a volání funkcí vás zajímají, a jestli chcete zobrazit snímky celého stavu aplikace. Další informace o tom, jak definovat, co chcete vyhledat, najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md). Podpora funkcí se liší podle jazyka a typu aplikace.

- Pokud chcete zobrazit snímky s historickým laděním, přečtěte si téma [Kontrola předchozích stavů aplikace pomocí IntelliTrace](../debugger/view-historical-application-state.md) .
- Informace o tom, jak kontrolovat proměnné a procházet kód, najdete v tématu [Kontrola aplikace pomocí historických ladění](../debugger/historical-debugging-inspect-app.md) .
- Další informace o ladění s událostmi IntelliTrace naleznete v tématu [Návod: použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md).