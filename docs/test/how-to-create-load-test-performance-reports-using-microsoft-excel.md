---
title: Vytváření sestav o výkonu zátěžového testu pomocí aplikace Microsoft Excel
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a94a44d0a826cbda1d50b212f61bef86ad29f05c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287815"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Postupy: vytváření sestav výkonu zátěžového testu pomocí aplikace Microsoft Excel

Můžete generovat sestavy zátěžového testu v aplikaci Microsoft Excel, které jsou založeny na dvou nebo více výsledcích testů.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

K dispozici jsou dva typy sestav zátěžových testů:

- **Spustit porovnání** Tím se vytvoří sada sestav, které porovnávají data ze dvou výsledků zátěžového testu pomocí tabulek a pruhových grafů.

- **Trend** Analýzu trendů můžete generovat na dvou nebo více výsledcích zátěžového testu. Výsledky se zobrazují pomocí spojnicových grafů, ale data jsou k dispozici v kontingenčních tabulkách.

> [!TIP]
> Můžete také ručně vytvořit sestavy aplikace Microsoft Word, a to zkopírováním a vložením dat ze souhrnného zobrazení, zobrazení grafů a zobrazení tabulek. Viz [Postupy: Ruční vytvoření sestavy výkonu zátěžového testu pomocí Microsoft Wordu](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Každá sestava se dá použít ke sdílení dat o výkonu se zúčastněnými stranami a vyjadřuje, jestli celkový výkon a stav systému je lepší nebo horší.

Definice sestav jsou uloženy v databázi zátěžového testu. Při uložení sestavy je definice sestavy uložena v databázi a lze ji znovu použít později.

Sešit aplikace Excel lze také sdílet se zúčastněnými stranami, aby se zúčastněné strany nemuseli připojovat k databázi, aby se zobrazila sestava.

> [!NOTE]
> Můžete sdílet excelový sešit; pouze uživatelé, kteří mají v počítači nainstalovánu sadu Visual Studio, budou moci upravovat jakékoli tabulky. Ostatní uživatelé neuvidí možnost **Sestava zátěžového testu** na pásu karet **Office** , ale budou moci sešit zobrazit.

Na následujícím obrázku je příklad sestavy, která zobrazuje korelaci mezi odmítnutím rychlosti transakce (aktualizační vozík) a degenerací čítače (% Processor). To ukazuje na potenciální problém v kódu aplikace místo databáze nebo sítě a je dobrým kandidátem na diagnostiku pomocí profileru ASP.NET.

![Možný problém v kódu aplikace](../test/media/lt_excel.png)

Sestavy aplikace Excel lze buď vygenerovat v **analyzátoru zátěžového testu**, pomocí tlačítka **vytvořit sestavu aplikace Excel** na panelu nástrojů nebo z aplikace Excel pomocí možnosti **Sestava zátěžového** testu na kartě **test zátěže** na pásu karet **Office** .

> [!NOTE]
> Pokud přidáte komentáře do zátěžového testu, zobrazí se v sestavě aplikace Excel.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Generování sestav porovnání zátěžových testů pomocí aplikace Excel

1. Před vygenerováním sestavy je třeba nejprve spustit zátěžový test.

2. Sestavy zátěžového testu v aplikaci Excel můžete vytvořit dvěma způsoby:

   - Po dokončení zátěžového testu na stránce **načíst výsledky testů** klikněte na tlačítko **vytvořit sestavu aplikace Excel** na panelu nástrojů.

      > [!NOTE]
      > Pokud je tlačítko **vytvořit sestavu aplikace Excel** na panelu nástrojů **webového výkonu výsledky testů Viewer** neaktivní, může být nutné spustit aplikaci Microsoft Excel jednou předtím, než bude povolena. Je-li nainstalován Visual Studio Enterprise, je doplněk zátěžového testu Visual Studio Enterprise zkopírován do vašeho počítače pro aplikaci Microsoft Excel. je však třeba spustit aplikaci Microsoft Excel, aby bylo možné dokončit proces instalace doplňku.

      Otevře se aplikace Microsoft Excel s **Průvodcem vytvořením sestavy zátěžového testu**.

   **ANI**

   1. Otevřete aplikaci Microsoft Excel, na pásu karet **Office** vyberte kartu **zátěžový test** a pak zvolte možnost **Sestava zátěžového testu**.

       Zobrazí se **Průvodce vytvořením sestavy zátěžového testu** .

   2. Na stránce **Vyberte databázi, která obsahuje testy zatížení** v části **název serveru**zadejte název serveru obsahujícího výsledky zátěžového testu.

   3. V rozevíracím seznamu **název databáze** vyberte databázi obsahující výsledky zátěžového testu.

3. V části **jak chcete generovat stránku sestavy** ověřte, zda je vybrána možnost **vytvořit sestavu** a klikněte na tlačítko **Další**.

4. Na stránce **jaký typ sestavy chcete generovat** ověřte, zda je zaškrtnuto políčko **Spustit porovnání** a klikněte na tlačítko **Další**.

5. Na stránce **zadat podrobnosti sestavy zátěžového testu** zadejte název sestavy do **pole název sestavy**.

6. Vyberte zátěžový test, pro který chcete vytvořit sestavu, a klikněte na tlačítko **Další**.

7. Na stránce **Vyberte běhy pro sestavu** v části **vybrat jedno nebo více spuštění pro přidání do sestavy**vyberte dva výsledky zátěžových testů, které chcete v sestavě porovnat, a klikněte na tlačítko **Další**.

   > [!NOTE]
   > Můžete vygenerovat pouze sestavu porovnání dvou výsledků zátěžového testu. Pokud vyberete buď jeden výsledek zátěžového testu, nebo více než dva výsledky zátěžového testu, zobrazí se varovná zpráva.

8. Na stránce **Vybrat čítače pro sestavu** v části **Vyberte jeden nebo více čítačů, které chcete přidat do sestavy** je k dispozici rozšiřitelný seznam čítačů pro přizpůsobení sestavy. Vyberte čítače, které chcete porovnat ze dvou vybraných testovacích běhů v sestavě a klikněte na tlačítko **Dokončit**.

9. Sestava excelového sešitu je vygenerována s následujícími kartami tabulky:

   - **Obsah** – zobrazí název sestavy zátěžového testu a poskytuje obsah s odkazy na různé karty v sestavě.

   - **Spuštění –** Poskytuje podrobnosti o tom, které dva běhy jsou v sestavě porovnány.

   - **Porovnání testů –** Poskytuje informace o pruhovém grafu pro regrese výkonu a vylepšení mezi dvěma běhy porovnání.

   - **Porovnání stránky –** Poskytuje pruhový graf a procentuální srovnávací data o výkonu mezi dvěma běhy na různých stránkách v rámci testovacích běhů.

   - **Porovnání počítačů –** Poskytuje srovnávací data mezi dvěma spuštěními na základě používaných počítačů.

   - **Porovnání chyb –** Porovná typy chyb zjištěné mezi dvěma spuštěními a počtem výskytů.

     > [!TIP]
     > Pro lepší sestavy jsou k dispozici v zátěžových testech a testech webového výkonu, které umožňují bohatší sestavování. Požadavek na stránku má dvě vlastnosti, které jsou uvedeny v sestavách: cíl a název sestavy. Časy odezvy stránky budou hlášeny proti cíli a místo adresy URL v sestavách bude použit název pro vytváření sestav. V nastaveních běhu zátěžového testu v části spravovat sady čítačů je vlastnost značky počítače uvedena v poli sestavy názvy počítačů. To je velmi užitečné pro popis role konkrétního počítače v sestavě.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Generování sestav trendů zátěžového testu pomocí aplikace Excel

1. Před vygenerováním sestavy je nutné spustit zátěžový test.

2. Sestavy zátěžového testu v aplikaci Excel můžete vytvořit dvěma způsoby:

   - Po dokončení zátěžového testu na stránce **načíst výsledky testů** klikněte na tlačítko **vytvořit sestavu aplikace Excel** na panelu nástrojů.

      > [!NOTE]
      > Pokud je tlačítko **vytvořit sestavu aplikace Excel** na panelu nástrojů **webového výkonu výsledky testů Viewer** neaktivní, může být nutné spustit aplikaci Microsoft Excel jednou předtím, než bude povolena. Je-li nainstalován Visual Studio Enterprise, je doplněk zátěžového testu Visual Studio Enterprise zkopírován do vašeho počítače pro aplikaci Microsoft Excel. je však třeba spustit aplikaci Microsoft Excel, aby bylo možné dokončit proces instalace doplňku.

      Otevře se aplikace Microsoft Excel s **Průvodcem vytvořením sestavy zátěžového testu**.

   **ANI**

   1. Otevřete aplikaci Microsoft Excel, na pásu karet **Office** vyberte kartu **zátěžový test** a pak zvolte možnost **Sestava zátěžového testu**.

       Zobrazí se **Průvodce vytvořením sestavy zátěžového testu** .

   2. Na stránce **Vyberte databázi, která obsahuje testy zatížení** v části **název serveru**zadejte název serveru obsahujícího výsledky zátěžového testu.

   3. V rozevíracím seznamu **název databáze** vyberte databázi obsahující výsledky zátěžového testu.

3. V části **jak chcete generovat stránku sestavy** ověřte, zda je vybrána možnost **vytvořit sestavu** a klikněte na tlačítko **Další**.

4. Na stránce **jaký typ sestavy chcete generovat** ověřte, zda je vybrána možnost **trend** a klikněte na tlačítko **Další**.

5. Na stránce **zadat podrobnosti sestavy zátěžového testu** zadejte název sestavy do **pole název sestavy**.

6. Vyberte zátěžový test, pro který chcete vytvořit sestavu, a klikněte na tlačítko **Další**.

7. Na stránce **Vyberte běhy pro sestavu** v části **vybrat jedno nebo více spuštění pro přidání do sestavy**vyberte výsledky zátěžového testu, které chcete v sestavě porovnat, a klikněte na tlačítko **Další**.

8. Na stránce **Vybrat čítače pro sestavu** v části **Vyberte jeden nebo více čítačů, které chcete přidat do sestavy**, je k dispozici rozevírací seznam čítačů pro přizpůsobení sestavy. Vyberte čítače, které chcete porovnat pro analýzu trendů, a klikněte na tlačítko **Dokončit**.

9. Sestava se vygeneruje pomocí obsahu, který obsahuje odkazy na různé karty excelového sešitu generované v sestavě. Odkazy jsou založené na čítačích vybraných pro sestavu trendů. Pokud jste například opustili výchozí čítače vybrané v kroku 7, sestava vygeneruje data, která se zobrazí v samostatných kartách v aplikaci Excel pro každý čítač uvedený v kroku 7. Data generovaná pro jednotlivé čítače jsou prezentována v grafech ve stylu trendu.

   > [!TIP]
   > Pro lepší sestavy jsou k dispozici v zátěžových testech a testech webového výkonu, které umožňují bohatší sestavování. Požadavek na stránku má dvě vlastnosti, které jsou uvedeny v sestavách: cíl a název sestavy. Časy odezvy stránky budou hlášeny proti cíli a místo adresy URL v sestavách bude použit název pro vytváření sestav. V nastaveních běhu zátěžového testu v části spravovat sady čítačů je vlastnost značky počítače uvedena v poli sestavy názvy počítačů. To je velmi užitečné pro popis role konkrétního počítače v sestavě.

## <a name="net-security"></a>Zabezpečení .NET

Výsledky zátěžového testu a sestavy obsahují potenciálně citlivé informace, které mohou být použity k vytvoření útoku proti vašemu počítači nebo síti. Výsledky a sestavy zátěžového testu obsahují názvy počítačů a připojovací řetězce. Měli byste si být vědomi toho, že při sdílení sestav zátěžových testů s ostatními uživateli.

## <a name="see-also"></a>Viz také

- [Výsledky testů zatížení sestav pro porovnání testů nebo analýzy trendů](../test/compare-load-test-results.md)
