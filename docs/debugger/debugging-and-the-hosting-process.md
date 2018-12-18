---
title: Ladění a proces hostování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59ef28f5724c12fd9897adbaa9125bafe26beb60
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468257"
---
# <a name="debugging-and-the-hosting-process"></a>Ladění a proces hostování
Hostující proces sady Visual Studio zlepšuje výkon ladicího programu a umožňuje nové funkce ladicího programu, jako je ladění částečným vztahem důvěryhodnosti a vyhodnocení výrazu v době návrhu. Pokud je potřeba, můžete zákaz procesu hostování. Následující části popisují některé rozdíly mezi ladění a nemusíte hostitelský proces.

> [!NOTE]
> V sadě Visual Studio 2017 možnost ladění pomocí hostitelský proces už je nepotřebujete a byl odebrán. Další informace najdete v tématu [ladění: Visual Studio 2017 cíle na rychlost až si alespoň Oblíbené úlohy](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Ladění částečným vztahem důvěryhodnosti a klikněte na tlačítko-jednou zabezpečení
 Ladění částečným vztahem důvěryhodnosti vyžaduje hostující proces. Pokud je hostitelský proces zakázat, částečným vztahem důvěryhodnosti ladění nebudou fungovat i v případě, že je zapnutá částečným vztahem důvěryhodnosti zabezpečení **zabezpečení** stránce **vlastnosti projektu**. Další informace najdete v tématu [postupy: ladění aplikace částečné důvěryhodnosti](../debugger/how-to-debug-a-partial-trust-application.md).

## <a name="design-time-expression-evaluation"></a>Vyhodnocení výrazu v době návrhu
 Výraz návrhu vždy používá hostitelský proces. Zakázání hostování v procesu **vlastnosti projektu** zakáže vyhodnocení výrazu v době návrhu pro projekty knihovny tříd. Vyhodnocení výrazu v době návrhu není zakázáno, pro ostatní typy projektů. Místo toho Visual Studio spustí skutečný program a použije ho k vyhodnocení doby návrhu bez hostitelský proces. Tento rozdíl může mít různé výsledky.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName rozdíly
 `AppDomain.CurrentDomain.FriendlyName` Vrátí odlišné výsledky v závislosti na tom, zda je povoleno hostitelský proces. Při volání `AppDomain.CurrentDomain.FriendlyName` s proces hostování povoleno, vrátí *app_name*`.vhost.exe`. Pokud při volání hostitelský proces zakázán, vrátí *app_name*`.exe`.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly(). Jméno a příjmení rozdíly
 `Assembly.GetCallingAssembly().FullName` Vrátí odlišné výsledky v závislosti na tom, zda je povoleno hostitelský proces. Při volání `Assembly.GetCallingAssembly().FullName` s proces hostování povoleno, vrátí `mscorlib`. Při volání `Assembly.GetCallingAssembly().FullName` se hostitelský proces zakázán, vrátí název aplikace.

## <a name="see-also"></a>Viz také:

- [Postupy: ladění aplikace s částečnou důvěryhodností](../debugger/how-to-debug-a-partial-trust-application.md)