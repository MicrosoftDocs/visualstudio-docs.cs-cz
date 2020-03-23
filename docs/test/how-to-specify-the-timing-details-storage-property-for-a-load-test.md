---
title: Vlastnost úložiště podrobností časování pro nastavení spuštění zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbd3b2a7d7e56870a994af288f5887f1d86256af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591642"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Postup: Určení vlastnosti úložiště podrobností časování pro nastavení spuštění zátěžového testu

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovým testem**můžete pomocí **Editoru zátěžového testu** změnit nastavení tak, aby vyhovovalo vašim potřebám a cílům testování.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Hodnotu vlastnosti úložiště **podrobností časování** můžete upravit v okně **Vlastnosti.** Vlastnost **Podrobnosti časování storage** lze nastavit na některou z následujících možností:

- **Všechny jednotlivé detaily:** Shromažďuje a ukládá individuální časování dat pro každý test, transakce a stránky vydané během testu.

  > [!NOTE]
  > Chcete-li povolit informace o virtuálních uživatelských datech ve výsledcích zátěžového testu, musí být vybrána možnost **Všechny jednotlivé podrobnosti.** Další informace naleznete [v tématu Analýza aktivity virtuálního uživatele v zobrazení Podrobnosti](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Žádné:** Neshromažďuje žádné podrobnosti o jednotlivých časování. Průměrné hodnoty jsou však stále k dispozici.

- **Pouze statistiky:** Ukládá individuální časovací data, ale pouze jako data percentilu. To šetří vesmírné zdroje.

  **Důležité informace pro vlastnost úložiště Podrobnosti časování**

  Pokud je povolena vlastnost **Úložiště podrobností časování,** bude čas pro spuštění každého jednotlivého testu, transakce a stránky během zátěžového testu uložen v úložišti výsledků zátěžového testu. To umožňuje 90th a 95th percentil data, která mají být zobrazeny v **analyzátoru zátěžového testu** v **testech**, **transakce**a **stránky** tabulky.

  Pokud je povolena vlastnost **Úložiště podrobností časování,** nastavením jeho hodnoty na **StatisticsOnly** nebo **AllIndividualDetails**, jsou všechny jednotlivé testy, stránky a transakce časovány a data percentilu se vypočítá z jednotlivých dat časování. Rozdíl je, že s **StatisticsOnly** možnost, po vypočítat data percentilu, jednotlivé časování data jsou odstraněny z úložiště. To snižuje množství místa, které je požadováno v úložišti při použití podrobností časování. Však můžete chtít zpracovat data podrobností časování jinými způsoby pomocí nástrojů SQL, v takovém případě **AllIndividualDetails** možnost by měla být použita tak, aby data podrobností časování je k dispozici pro toto zpracování. Navíc pokud nastavíte vlastnost **AllIndividualDetails**, pak můžete analyzovat aktivitu virtuálního uživatele pomocí **grafu aktivity virtuálního uživatele** v **analyzátoru zátěžového testu** po dokončení zátěžového testu. Další informace naleznete [v tématu Analýza aktivity virtuálního uživatele v zobrazení Podrobnosti](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  Množství místa potřebného v úložišti výsledků zátěžového testu pro uložení dat podrobností časování může být velmi velké, zejména pro déle běžící zátěžové testy. Také čas pro uložení těchto dat v úložišti výsledků zátěžového testu na konci zátěžového testu je delší, protože tato data jsou uložena na agentech zátěžového testu, dokud zátěžový test nedokončí provádění, kdy jsou data uložena do úložiště. Vlastnost **Úložiště podrobností časování** je ve výchozím nastavení povolena. Pokud se jedná o problém pro testovací prostředí, můžete nastavit **úložiště podrobností časování** na **žádné**.

  Data podrobností časování jsou uložena v souboru *LoadTestItemResults.dat* během spuštění a po dokončení zátěžového testu jsou odeslána zpět do řadiče. Pro zátěžový test spuštěný po dlouhou dobu je velikost souboru velká. Pokud není dostatek místa na disku v počítači agenta, bude to problém.

  Pokud inovujete projekt z předchozí verze zátěžového testu sady Visual Studio, povolte úplnou kolekci podrobností následujícím postupem.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Konfigurace vlastnosti úložiště podrobností časování v zátěžovém testu

1. Otevřete zátěžový test v editoru zátěžového testu.

2. Rozbalte uzel **Spustit nastavení** v zátěžovém testu.

3. Zvolte nastavení spuštění, které chcete konfigurovat, například **Spustit Nastavení1[Active]**.

4. Otevřete okno **Vlastnosti.** V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

5. V kategorii **Výsledky** zvolte vlastnost **Úložiště podrobností časování** a vyberte **všechny jednotlivé podrobnosti**.

     Po konfiguraci nastavení **Všechny jednotlivé podrobnosti** pro vlastnost **Úložiště podrobností časování** můžete spustit zátěžový test a zobrazit **graf aktivity virtuálního uživatele**. Další informace naleznete v [tématu How to: Analyze what virtual users are doing during a load test](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Viz také

- [Analýza aktivity virtuálního uživatele v zobrazení Podrobnosti](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Návod: Použití grafu virtuální aktivity uživatele k odištit problémy](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
