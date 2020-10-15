---
title: Vytvoření adaptéru diagnostických dat pro testování
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65d311ec522e5ba5b5c92193a8af3e53a9e9eb35
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099320"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Vytvoření adaptéru diagnostických dat pro shromažďování vlastních dat nebo ovlivnění testovacího počítače

Může být vhodné vytvořit vlastní adaptér diagnostiky dat ke sběru dat při spuštění testu nebo v průběhu testu ovlivnit testovací počítač. Může být například užitečné shromáždit soubory protokolu, které jsou vytvářeny v testované aplikaci, a připojit je k výsledkům testu, nebo spustit testy, když máte málo zbývajícího místa na disku. Pomocí rozhraní API poskytovaných v rámci Visual Studio Enterprise můžete napsat kód, který bude provádět úlohy v určitých bodech v rámci testovacího běhu. Lze například provádět úkoly při spuštění testovacího běhu, před spuštěním nebo po spuštění jednotlivých testů, a když se testovací běh dokončí.

::: moniker range="vs-2017"
Lze zadat výchozí vstup do vlastního adaptéru diagnostiky dat pomocí souboru konfiguračních nastavení. Lze například zadat informace o umístění souboru, který chcete shromáždit a připojit k výsledkům testu, nebo o tom, kolik by mělo na disku v systému zůstat místa. Tato data lze nakonfigurovat pro každé nastavení testu, které vytvoříte. Dá se zobrazit a upravit pomocí výchozího editoru, který je součástí Microsoft Test Manager, nebo můžete vytvořit vlastní uživatelský ovládací prvek, který chcete použít jako editor. Jakékoli změny provedené v konfiguraci adaptéru v editoru jsou uloženy s nastavením testu.
::: moniker-end

::: moniker range=">=vs-2019"
Lze zadat výchozí vstup do vlastního adaptéru diagnostiky dat pomocí souboru konfiguračních nastavení. Lze například zadat informace o umístění souboru, který chcete shromáždit a připojit k výsledkům testu, nebo o tom, kolik by mělo na disku v systému zůstat místa. Tato data lze nakonfigurovat pro každé nastavení testu, které vytvoříte. Můžete vytvořit vlastní uživatelský ovládací prvek, který chcete použít jako editor. Jakékoli změny provedené v konfiguraci adaptéru v editoru jsou uloženy s nastavením testu.
::: moniker-end

Pokud spouštíte testy ze sady Visual Studio, musíte nastavit, aby tato nastavení testu byla aktivní. Další informace o nastaveních testu naleznete v tématu [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Úlohy

Následující témata vám pomohou s vytvořením Adaptérů diagnostiky dat:

|Úlohy|Související témata|
|-|-----------------------|
|**Vytváření adaptéru diagnostických dat:** Adaptér diagnostických dat můžete vytvořit vytvořením knihovny tříd a následným použitím rozhraní API adaptéru diagnostických dat ke shromáždění informací, které chcete, nebo ovlivnění testovacího systému, který používáte ke spuštění testů.|-   [Postupy: vytvoření adaptéru diagnostických dat](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Výběr vlastního adaptéru diagnostických dat, který se má použít při spuštění testů:** Můžete vybrat adaptér diagnostických dat pro nastavení testu, aby se adaptér používal při spuštění testů.|-   [Shromažďovat diagnostická data při testování (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)<br />-   [Shromažďovat diagnostická data v ručních testech (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)|

## <a name="see-also"></a>Viz také

- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)