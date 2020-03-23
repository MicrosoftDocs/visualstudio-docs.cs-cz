---
title: Vytvoření sestavy výkonu zátěžového testu pomocí aplikace Microsoft Word
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3deee8d35f06e50dbe22001e8a2fa81b41563e0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113439"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Postup: Ruční vytvoření sestavy výkonu zátěžového testu pomocí aplikace Microsoft Word

Sestavy zátěžových testů aplikace Microsoft Word můžete vytvořit ručně zkopírováním a vložením dat ze souhrnného zobrazení výsledků zátěžového testu a zobrazení grafů. Při kopírování dat, která jsou uvedena v souhrnném zobrazení a zobrazení grafů, jsou tato data použita ve formátu HTML.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Prostý text můžete kopírovat ze zobrazení tabulek a snímků obrazovky ze zobrazení podrobností do aplikace Microsoft Word, ale není použit ve formátu HTML a bude vyžadovat další formátování a úpravy.

> [!TIP]
> Můžete také automaticky generovat uspořádané sestavy aplikace Microsoft Excel. Další informace naleznete v [tématu Postup: Vytvoření sestav výkonu zátěžového testu pomocí aplikace Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Kopírovat data souhrnného zobrazení

1. Pokud **se**souhrnné zobrazení aktuálně nezobrazuje v panelu nástrojů , klikněte na souhrnný panel **na Souhrn.**

2. V souhrnném zobrazení klepněte pravým tlačítkem myši a vyberte **vybrat vše**.

3. V souhrnném zobrazení klepněte pravým tlačítkem myši a vyberte **příkaz Kopírovat**. Tím zkopírujete data souhrnného zobrazení ve formátu HTML do schránky.

4. V aplikaci Microsoft Word vložte data souhrnného zobrazení do požadovaného umístění.

5. Nyní lze upravit, formátovat a mazat aspekty zkopírovaného obsahu podle potřeb vytváření sestav.

## <a name="copy-graph-view-data"></a>Kopírování dat zobrazení grafu

1. Pokud se v zobrazení zátěžových testů aktuálně nezobrazuje zobrazení **zátěžových testů,** zvolte **Grafy** na panelu nástrojů.

2. (Nepovinné) Přibližte konkrétní graf, který chcete zkopírovat do dokumentu aplikace Microsoft Word, jak je znázorněno na následujícím obrázku. Další informace naleznete [v tématu Postup: Přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Ovládací prvek zvětšení zobrazení grafu](../test/media/ltest_zoomcontrol.png)

3. V grafu, který chcete zkopírovat do dokumentu aplikace Microsoft Word, klepněte pravým tlačítkem myši a vyberte příkaz **Kopírovat**.

4. V aplikaci Microsoft Word vložte graf a přidružená data tabulky do požadovaného umístění.

    > [!WARNING]
    > Graf nelze zkopírovat ze vzdálené plochy a vložit jej do jiného počítače, protože budou zkopírovány pouze informace o tabulce, která je přidružena ke grafu, a nikoli obraz grafu. Obraz grafu je uložen v dočasném adresáři v počítači, ze kterého byl zkopírován, a druhý počítač nemůže přes ukazatel přistoupit k tomuto adresáři.

## <a name="see-also"></a>Viz také

- [Vykazovat výsledky zatěžovacích testů pro porovnání testů nebo analýzu trendů](../test/compare-load-test-results.md)
- [Postup: Vytvoření sestav výkonu zátěžového testu pomocí aplikace Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
