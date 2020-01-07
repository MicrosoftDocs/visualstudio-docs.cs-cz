---
title: Vytváření sestav výkonnosti pro zátěžový Test pomocí aplikace Microsoft Excel
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8134d2652c1654a65ac303838bd1209a5d061bd0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589068"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Postupy: vytvoření sestavy zátěžových testů výkonu pomocí aplikace Microsoft Excel

Můžete generovat sestavy zátěžového testu aplikace Microsoft Excel, které jsou založeny na dvou nebo více výsledcích testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

K dispozici jsou dva typy sestav zátěžových testů:

- **Spustit porovnání** tím se vytvoří sadu sestav, které porovnávají data ze dvou výsledků zkoušek zatížení pomocí tabulek a sloupcových grafů.

- **Trend** lze generovat analýzu trendů na dvou nebo více výsledcích zátěžového testu. Výsledky se zobrazí spojnicových grafech, ale data jsou k dispozici v kontingenčních tabulkách.

> [!TIP]
> Sestavy aplikace Microsoft Word můžete vytvořit také ručně zkopírováním a vložením dat ze souhrnného zobrazení, zobrazení grafů a zobrazení tabulek. Zobrazit [postupy: ruční vytvoření sestavy výkonu zátěžového testu pomocí aplikace Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Některá sestava umožňuje sdílení dat o výkonu se zúčastněnými stranami a sdělení, zda celkový výkon a stav systému se zlepšuje nebo zhoršuje.

Definice sestav jsou uloženy v databázi zátěžového testu. Při uložení sestavy definice sestavy je uloženo v databázi a lze ji znovu použít později.

Excelový sešit můžete také sdílet se zúčastněnými stranami tak, aby zúčastněné strany není potřeba připojení k databázi pro zobrazení sestavy.

> [!NOTE]
> Můžete sdílet sešit aplikace Excel; jenom uživatelé, kteří mají na svém počítači nainstalovanou sadu Visual Studio však budou moci upravit některou z tabulek. Ostatní uživatelé neuvidí **sestava zátěžového testu** možnost **Office** pásu karet, ale budete moct zobrazit v sešitě.

Na následujícím obrázku je příklad sestavy, která zobrazuje korelaci mezi poklesem rychlosti transakce (Aktualizovat košík) a degenerací čítače (% procesoru). To ukazuje na možný problém v aplikačním kódu místo v databázové síti a je vhodným kandidátem pro diagnostiku pomocí služby Profiler technologie ASP.NET.

![Možný problém v kódu aplikace](../test/media/lt_excel.png)

Sestavy aplikace Excel mohou být generovány v **Analyzéru zátěžového testu**, s použitím **vytvořit sestavu aplikace Excel** tlačítko na panelu nástrojů nebo z aplikace Excel s použitím **sestava zátěžového testu** možnost **zátěžový Test** karty **Office** pásu karet.

> [!NOTE]
> Pokud chcete přidat komentáře k zátěžovému testu, se zobrazí v sestavě aplikace Excel.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Ke generování sestav porovnání zátěžových testů pomocí aplikace Excel

1. Před generováním sestavy, musíte nejprve spustit zátěžový test.

2. Sestavy zátěžového testu aplikace Excel můžete vytvořit dvěma způsoby:

   - Po dokončení zátěžového testu v **výsledky zátěžového testu** zvolte **vytvořit sestavu aplikace Excel** tlačítko na panelu nástrojů.

      > [!NOTE]
      > Pokud **vytvořit sestavu aplikace Excel** je tlačítko neaktivní v **prohlížeče výsledků testu výkonnosti webu** nástrojů, budete muset spustit aplikaci Microsoft Excel jeden čas, než je povolené. Při instalaci sady Visual Studio Enterprise, Visual Studio Enterprise zátěžového testu doplněk je zkopírován do počítače pro aplikaci Microsoft Excel. aplikace Microsoft Excel však musí být spuštěn na dokončení procesu instalace pro doplněk.

      Aplikace Microsoft Excel otevře s **generovat Průvodce vytvořením sestavy zátěžového testu**.

   **OR**

   1. Otevřete aplikaci Microsoft Excel, vyberte **zátěžový Test** kartu **Office** pásu karet a klikněte na tlačítko **sestava zátěžového testu**.

       **Generovat Průvodce vytvořením sestavy zátěžového testu** se zobrazí.

   2. V **vyberte databázi, která obsahuje testy zatížení** stránce v části **název serveru**, zadejte název serveru obsahující výsledky zátěžového testu.

   3. V rozevíracím seznamu **název databáze** vyberte databázi obsahující výsledky zátěžového testu.

3. V **jak chcete generovat sestavy** stránce ověřte, jestli **vytvoření sestavy** je vybranou a stiskněte tlačítko **Další**.

4. V **jaký typ sestavy chcete generovat** stránce ověřte, jestli **spustit porovnání** je vybranou a stiskněte tlačítko **Další**.

5. V **podrobnosti sestavy zátěžového testu Enter** stránky, zadejte název pro sestavu v **název sestavy**.

6. Vyberte test zatížení, kterou chcete generovat sestavu a zvolte **Další**.

7. V **zvolte běhy sestavy** stránce v části **vyberte jeden nebo více spuštění pro přidání do sestavy**vyberte dva výsledky zátěžových testů, které chcete v sestavě porovnat a zvolte **Další**.

   > [!NOTE]
   > Generovat můžete pouze sestavu porovnání na dvou výsledcích zátěžového testu. Pokud vyberete buď jeden výsledek zátěžového testu nebo více než dva výsledky zátěžových testů, zobrazí se zpráva s upozorněním.

8. V **vyberte čítače sestavy** stránce v části **vyberte jeden nebo více čítačů pro přidání do sestavy** rozevírací seznam čítačů je k dispozici pro přizpůsobení vaší sestavy. Vyberte čítače, které chcete porovnat ze dvou vybraných testových běhů v sestavě a zvolte **Dokončit**.

9. Sestava v sešitu Excel je vytvořen s následujícími kartami tabulky:

   - **Obsah** – zobrazí název sestavy zátěžového testu a poskytuje obsah s odkazy na různé karty v sestavě.

   - **Běží -** poskytuje podrobnosti o, na kterých se porovnávají dvě spuštění v sestavě.

   - **Porovnání testu -** obsahuje podrobnosti o pruhovém grafu regrese výkonu a zlepšení mezi dvěma porovnávanými běhy.

   - **Porovnání stránek -** poskytuje pruhový graf a procento výkonu porovnání dat mezi dvěma běhy na různých stránkách ve zkušebním běhu.

   - **Porovnání počítače -** obsahuje data z porovnání mezi dvěma spuštěními podle na počítačích, které byly použity.

   - **Chyba při porovnání -** porovnává typy chyb zaznamenaných mezi dvěma spuštěními a počet výskytů.

     > [!TIP]
     > Pro lepší sestavy jsou k dispozici v zátěžových testech a testech výkonnosti webu, které umožňují lepší sestavy několik vlastností. Požadavek na stránku má dvě vlastnosti, které jsou uvedeny v sestavách: cíl a název sestavy. Doba odezvy stránky se bude vykazovány vůči cíli a namísto adresy URL v sestavách se použije název výkazu. V nastavení běhu, pod spravovat sady čítačů zátěžového testu je vlastnost značky počítače zobrazí v sestavě názvů počítače. To je velmi užitečné pro popis role konkrétního stroje v sestavě.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Ke generování sestav trendů zátěžových testů pomocí aplikace Excel

1. Před generováním sestavy je třeba spustit test zatížení.

2. Sestavy zátěžového testu aplikace Excel můžete vytvořit dvěma způsoby:

   - Po dokončení zátěžového testu v **výsledky zátěžového testu** zvolte **vytvořit sestavu aplikace Excel** tlačítko na panelu nástrojů.

      > [!NOTE]
      > Pokud **vytvořit sestavu aplikace Excel** je tlačítko neaktivní v **prohlížeče výsledků testu výkonnosti webu** nástrojů, budete muset spustit aplikaci Microsoft Excel jeden čas, než je povolené. Při instalaci sady Visual Studio Enterprise, Visual Studio Enterprise zátěžového testu doplněk je zkopírován do počítače pro aplikaci Microsoft Excel. aplikace Microsoft Excel však musí být spuštěn na dokončení procesu instalace pro doplněk.

      Aplikace Microsoft Excel otevře s **generovat Průvodce vytvořením sestavy zátěžového testu**.

   **OR**

   1. Otevřete aplikaci Microsoft Excel, vyberte **zátěžový Test** kartu **Office** pásu karet a klikněte na tlačítko **sestava zátěžového testu**.

       **Generovat Průvodce vytvořením sestavy zátěžového testu** se zobrazí.

   2. V **vyberte databázi, která obsahuje testy zatížení** stránce v části **název serveru**, zadejte název serveru obsahující výsledky zátěžového testu.

   3. V rozevíracím seznamu **název databáze** vyberte databázi obsahující výsledky zátěžového testu.

3. V **jak chcete generovat sestavy** stránce ověřte, jestli **vytvoření sestavy** je vybranou a stiskněte tlačítko **Další**.

4. V **jaký typ sestavy chcete generovat** stránce ověřte, jestli **Trend** je vybranou a stiskněte tlačítko **Další**.

5. V **podrobnosti sestavy zátěžového testu Enter** stránky, zadejte název pro sestavu v **název sestavy**.

6. Vyberte test zatížení, kterou chcete generovat sestavu a zvolte **Další**.

7. V **zvolte běhy sestavy** stránce v části **vyberte jeden nebo více spuštění pro přidání do sestavy**, vyberte výsledky zátěžového testu, které chcete v sestavě porovnat a zvolte **Další**.

8. V **vyberte čítače sestavy** stránce v části **vyberte jeden nebo více čítačů pro přidání do sestavy**, rozevírací seznam čítačů je k dispozici pro přizpůsobení vaší sestavy. Vyberte čítače, které chcete porovnat pro analýzu trendů a zvolte **Dokončit**.

9. Sestava se vygeneruje s tabulkou obsah, který obsahuje odkazy na různé karty sešitu aplikace Excel generované v sestavě. Odkazy jsou založeny na čítačích vybraných pro sestavu trendů. Například pokud jste ponechali výchozí čítače vybrané v kroku 7, pak sestava vygeneruje údaje, které jsou uvedeny v samostatných kartách v aplikaci Excel pro každý čítač uvedený v kroku 7. Data, který je generován pro každý čítač jsou zobrazena v grafu ve stylu trendů.

   > [!TIP]
   > Pro lepší sestavy jsou k dispozici v zátěžových testech a testech výkonnosti webu, které umožňují lepší sestavy několik vlastností. Požadavek na stránku má dvě vlastnosti, které jsou uvedeny v sestavách: cíl a název sestavy. Doba odezvy stránky se bude vykazovány vůči cíli a namísto adresy URL v sestavách se použije název výkazu. V nastavení běhu, pod spravovat sady čítačů zátěžového testu je vlastnost značky počítače zobrazí v sestavě názvů počítače. To je velmi užitečné pro popis role konkrétního stroje v sestavě.

## <a name="net-security"></a>Zabezpečení .NET

Výsledky zátěžového testu a sestavy obsahují potenciálně citlivé informace, které se dají zneužít k útoku proti vašemu počítači nebo síti. Výsledky zátěžového testu a sestavy obsahují názvy počítačů a připojovací řetězce. Je třeba tomu věnovat pozornost při sdílení sestav zátěžových testů s ostatními.

## <a name="see-also"></a>Viz také:

- [Sestava zátěžové testy s výsledky pro porovnávání testů a analýzu trendů](../test/compare-load-test-results.md)
