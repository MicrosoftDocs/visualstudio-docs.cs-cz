---
title: Vytvoření adaptéru diagnostických dat pro testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2eadce12890e483f1b1c7aafccb61d9a6ee28e3a
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880296"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Vytvoření adaptéru diagnostických dat pro shromažďování vlastních dat nebo ovlivnění testovacího počítače

Může být vhodné vytvořit vlastní adaptér diagnostiky dat ke sběru dat při spuštění testu nebo v průběhu testu ovlivnit testovací počítač. Může být například užitečné shromáždit soubory protokolu, které jsou vytvářeny v testované aplikaci, a připojit je k výsledkům testu, nebo spustit testy, když máte málo zbývajícího místa na disku. Pomocí api k dispozici v sadě Visual Studio Enterprise, můžete napsat kód k provádění úkolů v určitých bodech v testovacím běhu. Lze například provádět úkoly při spuštění testovacího běhu, před spuštěním nebo po spuštění jednotlivých testů, a když se testovací běh dokončí.

::: moniker range="vs-2017"
Lze zadat výchozí vstup do vlastního adaptéru diagnostiky dat pomocí souboru konfiguračních nastavení. Lze například zadat informace o umístění souboru, který chcete shromáždit a připojit k výsledkům testu, nebo o tom, kolik by mělo na disku v systému zůstat místa. Tato data lze nakonfigurovat pro každé nastavení testu, které vytvoříte. Může být zobrazen a editován pomocí výchozího editoru dodávaného s Microsoft Test Manager nebo můžete vytvořit vlastní uživatelský ovládací prvek pro použití jako editor. Jakékoli změny provedené v konfiguraci adaptéru v editoru jsou uloženy s nastavením testu.
::: moniker-end

::: moniker range=">=vs-2019"
Lze zadat výchozí vstup do vlastního adaptéru diagnostiky dat pomocí souboru konfiguračních nastavení. Lze například zadat informace o umístění souboru, který chcete shromáždit a připojit k výsledkům testu, nebo o tom, kolik by mělo na disku v systému zůstat místa. Tato data lze nakonfigurovat pro každé nastavení testu, které vytvoříte. Můžete vytvořit vlastní uživatelský ovládací prvek pro použití jako editor. Jakékoli změny provedené v konfiguraci adaptéru v editoru jsou uloženy s nastavením testu.
::: moniker-end

Pokud spouštěte testy z aplikace Visual Studio, musíte nastavit tato nastavení testu tak, aby byla aktivní. Další informace o nastavení testu naleznete v [tématu Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Úkoly

Následující témata vám pomohou s vytvořením Adaptérů diagnostiky dat:

|Úkoly|Související témata|
|-|-----------------------|
|**Vytvoření adaptéru diagnostických dat:** Adaptér diagnostických dat vytvoříte vytvořením knihovny tříd a potom pomocí rozhraní API adaptéru diagnostických dat shromážděte požadované informace nebo ovlivněte testovací systém, který používáte ke spuštění testů.|-   [Postup: Vytvoření adaptéru diagnostických dat](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Výběr vlastního adaptéru diagnostických dat, který se má použít při spuštění testů:** Můžete vybrat, který adaptér diagnostických dat se má použít pro nastavení testu, aby se adaptér použil při spuštění testů.|-   [Shromažďování diagnostických dat během testování (plány testů Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [Shromažďování diagnostických dat v ručních testech (plány testů Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Viz také

- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
