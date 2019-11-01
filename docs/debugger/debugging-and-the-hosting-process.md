---
title: Ladění a proces hostování | Microsoft Docs
ms.date: 08/01/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77df2eae643b658e915662e0f50f6a376141d27
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188469"
---
# <a name="debugging-and-the-hosting-process"></a>Ladění a proces hostování
Proces hostování sady Visual Studio vylepšuje výkon ladicího programu a umožňuje nové funkce ladicího programu, jako je například ladění částečného vztahu důvěryhodnosti a vyhodnocení výrazu v době návrhu. V případě potřeby můžete hostitelský proces zakázat. Následující části popisují některé rozdíly mezi laděním s a bez hostujícího procesu.

> [!NOTE]
> Od sady Visual Studio 2017 není možnost ladění pomocí hostitelského procesu nadále potřebná a byla odebrána. Další informace naleznete v tématu [ladění: Visual Studio 2017 směřuje k urychlení nejméně oblíbené úlohy](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Ladění s částečným vztahem důvěryhodnosti a zabezpečení po kliknutí
 Ladění s částečným vztahem důvěryhodnosti vyžaduje hostující proces. Pokud zakážete hostující proces, ladění s částečným vztahem důvěryhodnosti nebude fungovat ani v případě, že je na stránce **zabezpečení** **vlastností projektu**povoleno zabezpečení s částečnou důvěryhodností. Další informace najdete v tématu [Postup: ladění aplikace s částečnou důvěryhodností](debugger-security.md).

## <a name="design-time-expression-evaluation"></a>Vyhodnocení výrazu pro dobu návrhu
 Výraz při návrhu vždy používá hostitelský proces. Zakázání hostitelského procesu ve **vlastnostech projektu** zakáže vyhodnocení výrazu v době návrhu pro projekty knihovny tříd. Pro jiné typy projektů není vyhodnocení výrazu v době návrhu zakázáno. Místo toho Visual Studio spustí skutečný spustitelný soubor a použije ho pro vyhodnocení v době návrhu bez hostujícího procesu. Tento rozdíl může způsobit odlišné výsledky.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Rozdíly v AppDomain. CurrentDomain. FriendlyName
 `AppDomain.CurrentDomain.FriendlyName` vrátí různé výsledky v závislosti na tom, zda je proces hostování povolen. Pokud zavoláte `AppDomain.CurrentDomain.FriendlyName` s povoleným hostitelským procesem, vrátí *app_name*`.vhost.exe`. Pokud je zavoláte, je hostitelský proces zakázán, vrátí *app_name*`.exe`.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly. GetCallingAssembly (). Nafullname rozdíly
 `Assembly.GetCallingAssembly().FullName` vrátí různé výsledky v závislosti na tom, zda je proces hostování povolen. Pokud zavoláte `Assembly.GetCallingAssembly().FullName` s povoleným hostitelským procesem, vrátí `mscorlib`. Pokud zavoláte `Assembly.GetCallingAssembly().FullName` s hostitelským procesem zakázán, vrátí název aplikace.

## <a name="see-also"></a>Viz také:

- [Postupy: Ladění aplikace s částečnou důvěryhodností](debugger-security.md)