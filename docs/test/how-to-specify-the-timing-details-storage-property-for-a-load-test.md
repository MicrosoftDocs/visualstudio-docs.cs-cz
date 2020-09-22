---
title: Vlastnost úložiště podrobností časování (nastavení běhu zátěžového testu)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 132c55b4cd6f716d8983358064f749eabeb9ba88
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810559"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Postupy: určení vlastnosti úložiště podrobností časování pro nastavení běhu zátěžového testu

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**můžete pomocí **Editor zátěžového testu** změnit nastavení tak, aby vyhovovalo vašim požadavkům na testování a cílům.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Hodnotu vlastnosti **úložiště podrobnosti časování** nastavení běhu můžete upravit v okně **vlastnosti** . Vlastnost **úložiště podrobností časování** lze nastavit na některou z následujících možností:

- **Podrobnosti o všech jednotlivých uživatelích:** Shromažďuje a ukládá data jednotlivých časování pro každý test, transakci a stránku vydanou v průběhu testu.

  > [!NOTE]
  > Aby bylo možné ve výsledcích zátěžového testu povolit informace o virtuálním uživatelském uživateli, je nutné vybrat možnost **všechny jednotlivé podrobnosti** . Další informace najdete v tématu [Analýza aktivity virtuálních uživatelů v zobrazení podrobností](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Žádné:** Neshromažďuje žádné podrobnosti o jednotlivých časováních. Průměrné hodnoty jsou však stále k dispozici.

- **Pouze statistiky:** Ukládá data jednotlivých časování, ale pouze jako data percentilu. Tím ušetříte prostředky prostoru.

  **Požadavky na vlastnost úložiště podrobností časování**

  Pokud je povolena vlastnost **úložiště podrobností časování** , pak bude čas pro spuštění každého jednotlivého testu, transakce a stránky během zátěžového testu uložen v úložišti výsledků zátěžového testu. To umožňuje zobrazení dat 90 a 95. percentilu v **analyzátoru zátěžového testu** v tabulkách **testy**, **transakce**a **stránky** .

  Pokud je vlastnost **úložiště podrobností časování** povolena, nastavením její hodnoty na buď **StatisticsOnly** nebo **AllIndividualDetails**, všechny jednotlivé testy, stránky a transakce budou časované a data percentilu se vypočítají z jednotlivých časových údajů. Rozdíl je v tom, že s možností **StatisticsOnly** po výpočtu dat percentilu se jednotlivá data časování odstraní z úložiště. Tím se sníží množství místa, které je nutné v úložišti, pokud jsou použity podrobnosti časování. Můžete však chtít zpracovat podrobná data časování jiným způsobem pomocí nástrojů SQL. v takovém případě by měla být použita možnost **AllIndividualDetails** , aby byly k dispozici podrobná data časování pro toto zpracování. Kromě toho, pokud nastavíte vlastnost na **AllIndividualDetails**, pak můžete analyzovat aktivitu virtuálního uživatele pomocí **grafu aktivity virtuálního uživatele** v **analyzátoru zátěžového testu** po dokončení zátěžového testu. Další informace najdete v tématu [Analýza aktivity virtuálních uživatelů v zobrazení podrobností](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  Množství místa potřebné v úložišti výsledků zátěžového testu pro uložení dat s podrobnosti časování může být velmi velké, zejména pro delší spuštěné zátěžové testy. Také čas pro ukládání těchto dat do úložiště výsledků zátěžového testu na konci zátěžového testu je delší, protože tato data jsou uložena v agentech zátěžového testu, dokud zátěžový test neskončí, a v takovém čase jsou data uložena do úložiště. Vlastnost **úložiště podrobností časování** je ve výchozím nastavení povolená. Pokud se jedná o problém vašeho testovacího prostředí, možná budete chtít nastavit **úložiště podrobností časování** na **žádné**.

  Data časového údaje časování jsou ukládána v souboru *LoadTestItemResults. dat* během běhu a jsou odeslána zpět do kontroleru po dokončení zátěžového testu. Pro zátěžový test, který běží po dlouhou dobu, je velikost souboru velká. Pokud na počítači agenta není dostatek místa na disku, bude se jednat o problém.

  Pokud upgradujete projekt z předchozí verze zátěžového testu sady Visual Studio, použijte následující postup, chcete-li povolit úplnou kolekci podrobností.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Konfigurace vlastnosti úložiště podrobností časování v rámci zátěžového testu

1. Otevřete zátěžový test v Editoru zátěžového testu.

2. Rozbalte uzel **nastavení spuštění** v rámci zátěžového testu.

3. Vyberte nastavení spuštění, která chcete konfigurovat, například **Spusťte Settings1 [aktivní]**.

4. Otevřete okno **vlastnosti** . V nabídce **zobrazení** vyberte **okno Vlastnosti**.

5. V kategorii **výsledky** zvolte vlastnost **úložiště podrobnosti časování** a vyberte **všechny jednotlivé podrobnosti**.

     Po nakonfigurování nastavení **všechny jednotlivé podrobnosti** pro vlastnost **úložiště podrobností časování** můžete spustit zátěžový test a zobrazit **graf aktivity virtuálního uživatele**. Další informace naleznete v tématu [How to: Analyzujte virtuální uživatele v průběhu zátěžového testu](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Viz také

- [Analýza aktivity virtuálních uživatelů v zobrazení podrobností](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Návod: použití grafu aktivity virtuálního uživatele k izolaci problémů](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
