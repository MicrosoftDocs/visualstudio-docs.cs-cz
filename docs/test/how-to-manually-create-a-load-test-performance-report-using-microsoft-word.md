---
title: Vytvořit sestavu výkonu zátěžového testu pomocí Microsoft Wordu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 715086a2c0d9196680dd1f332ee9b5122e144e5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653481"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Postupy: Ruční vytvoření sestavy výkonu zátěžového testu pomocí Microsoft Wordu

Sestavy zátěžového testu aplikace Microsoft Word lze vytvořit ručně zkopírováním a vložením dat ze souhrnného zobrazení a zobrazení grafů pro zatížení Výsledky testů. Při kopírování dat, která jsou uvedena v souhrnném zobrazení a zobrazení grafů, jsou tato data použita ve formátu HTML.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Prostý text můžete zkopírovat ze zobrazení tabulky a snímky obrazovky z zobrazení podrobností do aplikace Microsoft Word, ale nepoužívá se ve formátu HTML a bude vyžadovat další formátování a úpravy.

> [!TIP]
> Můžete také automaticky vygenerovat seřazené sestavy aplikace Microsoft Excel. Další informace najdete v tématu [Postupy: vytváření sestav výkonu zátěžových testů pomocí aplikace Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Kopírovat data souhrnného zobrazení

1. Pokud se zobrazení souhrnu v okně **Load výsledky testů**aktuálně nezobrazuje, klikněte na panelu nástrojů na možnost **Souhrn** .

2. V souhrnném zobrazení klikněte pravým tlačítkem a vyberte **Vybrat vše**.

3. V souhrnném zobrazení klikněte pravým tlačítkem myši a vyberte možnost **Kopírovat**. Tím zkopírujete data souhrnného zobrazení ve formátu HTML do schránky.

4. V aplikaci Microsoft Word vložte data souhrnného zobrazení do požadovaného umístění.

5. Nyní lze upravit, formátovat a mazat aspekty zkopírovaného obsahu podle potřeb vytváření sestav.

## <a name="copy-graph-view-data"></a>Kopírovat data zobrazení grafu

1. Pokud se v **výsledky testů zatížení**nezobrazuje zobrazení grafů, vyberte na panelu nástrojů možnost **grafy** .

2. Volitelné Přiblížte se ke konkrétnímu grafu, který chcete zkopírovat do dokumentu Microsoft Wordu, jak je znázorněno na následujícím obrázku. Další informace najdete v tématu [Postup: přiblížení v oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Ovládací prvek zvětšení zobrazení grafu](../test/media/ltest_zoomcontrol.png)

3. V grafu, který chcete zkopírovat do dokumentu Microsoft Wordu, klikněte pravým tlačítkem myši a vyberte možnost **Kopírovat**.

4. V aplikaci Microsoft Word vložte graf a přidružená data tabulky do požadovaného umístění.

    > [!WARNING]
    > Graf nelze zkopírovat ze vzdálené plochy a vložit jej do jiného počítače, protože budou zkopírovány pouze informace o tabulce, která je přidružena ke grafu, a nikoli obraz grafu. Obraz grafu je uložen v dočasném adresáři v počítači, ze kterého byl zkopírován, a druhý počítač nemůže přes ukazatel přistoupit k tomuto adresáři.

## <a name="see-also"></a>Viz také:

- [Výsledky testů zatížení sestav pro porovnání testů nebo analýzy trendů](../test/compare-load-test-results.md)
- [Postupy: vytváření sestav výkonu zátěžového testu pomocí aplikace Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)