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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113439"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Postupy: ruční vytvoření sestavy výkonu zátěžového testu pomocí aplikace Microsoft Word

Sestavy zátěžového testu aplikace Microsoft Word můžete vytvořit ručně zkopírováním a vložením dat ze souhrnného zobrazení výsledky zátěžového testu a zobrazení grafů. Při kopírování dat, která jsou uvedena v souhrnném zobrazení a zobrazení grafů, jsou tato data použita ve formátu HTML.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Můžete zkopírovat prostý text z tabulkového zobrazení a kopie obrazovek ze zobrazení podrobností o do aplikace Microsoft Word, ale není použit ve formátu HTML a bude vyžadovat další formátování a úpravy.

> [!TIP]
> Uspořádané sestavy aplikace Excel můžete také vygenerovat automaticky. Další informace najdete v tématu [postupy: vytvoření sestavy zátěžových testů výkonu pomocí pomocí aplikace Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Kopírování dat souhrnného zobrazení

1. V **výsledky zátěžového testu**, pokud se souhrnné zobrazení aktuálně nezobrazí, klikněte na tlačítko **souhrnu** na panelu nástrojů.

2. V souhrnném zobrazení klikněte pravým tlačítkem a vyberte **Vybrat vše**.

3. V souhrnném zobrazení klikněte pravým tlačítkem a vyberte **kopírování**. Tím zkopírujete data souhrnného zobrazení ve formátu HTML do schránky.

4. V aplikaci Microsoft Word vložte data souhrnného zobrazení do požadovaného umístění.

5. Nyní lze upravit, formátovat a mazat aspekty zkopírovaného obsahu podle potřeb vytváření sestav.

## <a name="copy-graph-view-data"></a>Kopírování dat zobrazení grafu

1. V **výsledky zátěžového testu**, pokud se rozhodnou grafy zobrazení není zobrazen, **grafy** na panelu nástrojů.

2. (Volitelné) Přibližte konkrétní graf, který chcete zkopírovat do dokumentu Microsoft Wordu, jak je znázorněno na následujícím obrázku. Další informace najdete v tématu [postupy: přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Ovládací prvek lupy grafu zobrazit](../test/media/ltest_zoomcontrol.png)

3. V grafu, který chcete zkopírovat do dokumentu aplikace Microsoft Word, klikněte pravým tlačítkem a vyberte **kopírování**.

4. V aplikaci Microsoft Word vložte graf a přidružená tabulková data do požadovaného umístění.

    > [!WARNING]
    > Graf nelze zkopírovat ze vzdálené plochy a vložit jej do jiného počítače, protože budou zkopírovány pouze informace o tabulce, která je přidružena ke grafu, a nikoli obraz grafu. Obraz grafu je uložen v dočasném adresáři v počítači, ze kterého byl zkopírován, a druhý počítač nemůže přes ukazatel přistoupit k tomuto adresáři.

## <a name="see-also"></a>Viz také:

- [Sestava zátěžové testy s výsledky pro porovnávání testů a analýzu trendů](../test/compare-load-test-results.md)
- [Postupy: vytvoření sestavy zátěžových testů výkonu pomocí aplikace Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
