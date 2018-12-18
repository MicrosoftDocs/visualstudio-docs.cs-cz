---
title: Co je ladění?
description: Vysvětlení, co to znamená, že dovolují ladit aplikaci
ms.custom: debug-experiments
ms.date: 10/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f0aa6cbe09f902ef69e1fd5cb3a2d9712cabf28
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821445"
---
# <a name="what-is-debugging"></a>Co je ladění?

Ladicí program sady Visual Studio je mocný nástroj. Předtím, než vám ukážeme, jak ji používat, chceme mluvit o některé podmínky, jako *ladicí program*, *ladění*, a *režimu ladění*. Tímto způsobem, když později mluvíme o nacházením a odstraňováním chyb, jsme budete mluvit o stejnou věc.

## <a name="debugger-vs-debugging"></a>Ladicí program a ladění

Termín *ladění* může znamenat spoustu různých věcí, ale většina doslova znamená odebrání chyb z uživatelského kódu. Nyní existuje mnoho způsobů, jak to provést. Například můžete ladit naskenováním kódu hledá překlepy nebo pomocí nástroje code analyzer. Pomocí profileru výkonu může být ladění kódu. Nebo může být ladění pomocí *ladicí program*.

Ladicí program je velmi specializované vývojářský nástroj, který připojí k vaší běžící aplikaci a umožňuje vám umožní zkontrolovat váš kód. V dokumentaci k ladění pro Visual Studio to je obvykle co myslíme, když říkáme "ladění".

## <a name="debug-mode-vs-running-your-app"></a>Režim a vaše aplikace běžela ladění

Při prvním spuštění aplikace v sadě Visual Studio, můžete ho začít stisknutím tlačítka zelenou šipku ![spustit ladění](../debugger/media/dbg-tour-start-debugging.png "spustit ladění") na panelu nástrojů (nebo **F5**). Ve výchozím nastavení **ladění** hodnota se zobrazí v rozevíracím seznamu vlevo. Pokud jste ještě sadu Visual Studio, tím můžete nechat dojem, že něco, co můžete dělat s spuštění ladění vaší aplikace má vaše aplikace – které nemá – ale toto jsou v podstatě dvě značně odlišný úkol.

![Vyberte sestavení pro ladění](../debugger/media/what-is-debugging-debug-build.png)

A **ladění** hodnota určuje konfiguraci ladění. Při spuštění aplikace (stisknutím klávesy na zelenou šipku nebo **F5**) v konfiguraci ladění, spusťte aplikaci *režimu ladění*, což znamená, že spustíte aplikaci s připojen jiný ladicí program. To umožňuje kompletní sadu funkcí ladění, které vám umožní vám pomůže najít chyby v aplikaci.

Pokud máte otevřen projekt, zvolte rozevírací selektor, kde říká **ladění** a zvolte **vydání** místo.

![Vyberte sestavení pro vydání](../debugger/media/what-is-debugging-release-build.png)

Po přepnutí tohoto nastavení změnit projekt z konfigurace ladění na konfiguraci release. Projekty aplikace Visual Studio mají samostatné verze a ladění konfigurace pro váš program. Vytváření verzí ladění pro ladění a verze vydání pro konečnou distribuci vydání. Sestavení pro vydání je optimalizován pro výkon, ale je lepší pro ladění sestavení pro ladění.

## <a name="when-to-use-a-debugger"></a>Kdy použít ladicí program

Ladicí program je to důležitý nástroj, můžete najít a opravit chyby ve svých aplikacích. Však má kontextu a je potřeba využívat všechny nástroje k vaší na jedno použití k vám pomůže rychle eliminovat chyby. Právo "nástroje" v některých případech může být způsobem lépe kódování. Podle studijního, kdy se má použít ladicí program nebo nějaký jiný nástroj, bude také zjistěte, jak použít ladicí program efektivněji. Pokud už znáte, budete potřebovat další informace o ladicím programu, přečtěte si téma [ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md). V opačném případě přejděte na odkaz v **další kroky**.

## <a name="next-steps"></a>Další kroky

V tomto článku jste se seznámili s několika koncepty obecné ladění. V dalším kroku můžete začít ladění pomocí sady Visual Studio a tom, jak psát kód s méně chyb. Tento článek ukazuje C# příklady kódu, ale konceptů platí pro všechny jazyky podporované v aplikaci Visual Studio.

> [!div class="nextstepaction"]
> [Oprava chyb napsáním lépe C# kódu](../debugger/write-better-code-with-visual-studio.md)
