---
title: Vytvoření adaptéru diagnostiky dat pro účely testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91e5f9b3cee9cdfc2ca85c39c701b87028ad949a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585203"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Vytvoření adaptéru diagnostických dat pro shromáždění vlastních dat nebo ovlivnění testovacího počítače

Může být vhodné vytvořit vlastní adaptér diagnostiky dat ke sběru dat při spuštění testu nebo v průběhu testu ovlivnit testovací počítač. Může být například užitečné shromáždit soubory protokolu, které jsou vytvářeny v testované aplikaci, a připojit je k výsledkům testu, nebo spustit testy, když máte málo zbývajícího místa na disku. Pomocí rozhraní API poskytnutého v sadě Visual Studio Enterprise, můžete napsat kód k provádění úkolů v určitých bodech testovacího běhu. Lze například provádět úkoly při spuštění testovacího běhu, před spuštěním nebo po spuštění jednotlivých testů, a když se testovací běh dokončí.

Lze zadat výchozí vstup do vlastního adaptéru diagnostiky dat pomocí souboru konfiguračních nastavení. Lze například zadat informace o umístění souboru, který chcete shromáždit a připojit k výsledkům testu, nebo o tom, kolik by mělo na disku v systému zůstat místa. Tato data lze nakonfigurovat pro každé nastavení testu, které vytvoříte. Je možné zobrazit a upravené pomocí výchozího editoru, opatřeného Microsoft Test Manager nebo je můžete vytvořit vlastní uživatelský ovládací prvek použít jej jako editor. Jakékoli změny provedené v konfiguraci adaptéru v editoru jsou uloženy s nastavením testu.

Pokud používáte testy ze sady Visual Studio, musíte nastavit tyto jako aktivní nastavení testu. Další informace o nastaveních testu naleznete v tématu [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Tasks

Následující témata vám pomohou s vytvořením Adaptérů diagnostiky dat:

|Tasks|Související témata|
|-|-----------------------|
|**Vytvoření adaptéru diagnostiky dat:** vytvořit adaptér diagnostických dat vytvořením knihovny tříd a pak použít API adaptéru diagnostiky dat ke shromažďování informací, že chcete nebo ovlivnění testovacího systému, který používáte ke spuštění testů.|-   [Postupy: vytvoření adaptéru diagnostických dat](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Výběr vlastního adaptéru diagnostiky dat pro použití jsou spuštěny:** adaptéru diagnostických dat, pro který má použít pro nastavení testu, můžete vybrat tak, aby adaptér se používá při spuštění testů.|-   [Shromažďování diagnostických dat při testování (Azure testovací plány)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [Shromažďování diagnostických dat v manuálních testů (Azure testovací plány)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Viz také:

- [Shromažďování diagnostických údajů pomocí nastavení testů](../test/collect-diagnostic-information-using-test-settings.md)
