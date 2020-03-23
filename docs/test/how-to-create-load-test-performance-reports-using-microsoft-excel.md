---
title: Vytváření sestav výkonu zátěžového testu pomocí aplikace Microsoft Excel
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589068"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Postup: Vytvoření sestav výkonu zátěžového testu pomocí aplikace Microsoft Excel

Můžete generovat sestavy zátěžových testů aplikace Microsoft Excel, které jsou založeny na dvou nebo více výsledcích testů.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

K dispozici jsou dva typy protokolů zátěžových testů:

- **Spustit porovnání** Tím se vytvoří sada sestav, která porovnává data ze dvou výsledků zátěžového testu pomocí tabulek a pruhových grafů.

- **Trend** Můžete generovat analýzu trendů na dva nebo více výsledků zátěžového testu. Výsledky jsou zobrazeny pomocí spojnicových grafů, ale data jsou k dispozici v kontingenčních tabulkách.

> [!TIP]
> Sestavy aplikace Microsoft Word můžete také vytvořit ručně zkopírováním a vložením dat ze souhrnného zobrazení, zobrazení grafů a zobrazení tabulek. Přečtěte [si postup: Ruční vytvoření sestavy výkonu zátěžového testu pomocí aplikace Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Obě sestavy lze použít ke sdílení údajů o výkonu se zúčastněnými stranami a sdělit, zda celkový výkon a stav systému je stále lepší nebo horší.

Definice sestavy jsou uloženy v databázi zátěžového testu. Při uložení sestavy je definice sestavy uložena v databázi a lze ji později znovu použít.

Sešit aplikace Excel lze také sdílet se zúčastněnými stranami, aby se zúčastněné strany nemusely připojovat k databázi, aby se sestava zoána zoařila.

> [!NOTE]
> Můžete sdílet excelový sešit. Pouze uživatelé, kteří mají v počítači nainstalovanou aplikaci Visual Studio, však budou moci upravovat některou z tabulek. Ostatní uživatelé neuvidí možnost **Sestavy zátěžového testu** na pásu karet **Office,** ale budou moci zobrazit sešit.

Následující obrázek je příkladem sestavy, která ukazuje korelaci mezi poklesem rychlosti transakce (update cart) a degenerací čítače (% procesoru). To ukazuje na potenciální problém v kódu aplikace, namísto databáze nebo sítě a je vhodné diagnostikovat pomocí ASP.NET Profiler.

![Potenciální problém v kódu aplikace](../test/media/lt_excel.png)

Sestavy aplikace Excel lze generovat buď v **analyzátoru zátěžového testu**, pomocí tlačítka **Vytvořit excelovou sestavu** na panelu nástrojů nebo z aplikace Excel pomocí možnosti **Sestavy zátěžového testu** na kartě **Zátěžový test** na pásu karet **Office.**

> [!NOTE]
> Pokud přidáte komentáře k zátěžovému testu, zobrazí se v sestavě aplikace Excel.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Generování sestav porovnání zátěžových testů pomocí aplikace Excel

1. Před generováním sestavy je nutné nejprve spustit zátěžový test.

2. Sestavy zátěžových testů aplikace Excel můžete vytvářet dvěma způsoby:

   - Po dokončení zátěžového testu zvolte na stránce **Výsledky zátěžového testu** na panelu nástrojů tlačítko **Vytvořit sestavu aplikace Excel.**

      > [!NOTE]
      > Pokud je na panelu nástrojů **Prohlížeč výsledků testu výkonu webu** zakázáno tlačítko Vytvořit **sestavu aplikace Excel,** bude pravděpodobně nutné spustit aplikaci Microsoft Excel jednou, než bude povolena. Při instalaci sady Visual Studio Enterprise se doplněk zátěžového testu sady Visual Studio Enterprise zkopíruje do počítače pro aplikaci Microsoft Excel. Aplikace Microsoft Excel však musí být spuštěna k dokončení procesu instalace doplňku.

      Aplikace Microsoft Excel se otevře pomocí **Průvodce generováním sestavy zátěžového testu**.

   **Nebo**

   1. Otevřete Microsoft Excel, na pásu karet **Office** vyberte kartu **Zátěžový test** a pak zvolte **Sestava zátěžového testu**.

       Zobrazí **se Průvodce generováním sestavy zátěžového testu.**

   2. Na **stránce Select database, která obsahuje zátěžové testy,** zadejte v části **Název serveru**název serveru obsahujícívýsledky zátěžového testu.

   3. V rozevíracím seznamu **Název databáze** vyberte databázi obsahující výsledky zátěžového testu.

3. Na stránce **Jak chcete generovat sestavu** ověřte, zda je **vybraná volba Vytvořit sestavu,** a zvolte **Další**.

4. Na stránce **Jaký typ sestavy chcete generovat,** ověřte, zda je vybráno porovnání **spustit,** a zvolte **Další**.

5. Na stránce **Podrobnosti sestavy zátěžového testu** zadejte název sestavy do pole **Název sestavy**.

6. Vyberte zátěžový test, pro který chcete sestavu vygenerovat, a zvolte **Další**.

7. Na stránce **Vybrat spuštění sestavy** vyberte v části **Vyberte jeden nebo více spuštění, které chcete přidat do sestavy**, vyberte v sestavě dva výsledky zátěžového testu, které chcete porovnat, a zvolte **Další**.

   > [!NOTE]
   > Můžete vygenerovat pouze zprávu o porovnání dvou výsledků zátěžového testu. Pokud vyberete jeden výsledek zátěžového testu nebo více než dva výsledky zátěžového testu, zobrazí se varovná zpráva.

8. Na stránce **Vybrat čítače pro sestavu** je v části **Vyberte jeden nebo více čítačů, které chcete přidat do sestavy,** k dispozici rozbalitelný seznam čítačů pro přizpůsobení sestavy. Vyberte čítače, které chcete porovnat ze dvou vybraných testovacích běhů v sestavě, a zvolte **Dokončit**.

9. Sešit aplikace Excel je generován pomocí následujících karet tabulky:

   - **Obsah -** Zobrazí název sestavy zátěžového testu a obsahuje obsah s odkazy na různé karty v sestavě.

   - **Běží -** Obsahuje podrobnosti o tom, které dvě spuštění jsou porovnávány v sestavě.

   - **Porovnání testů -** Poskytuje podrobnosti sloupcového grafu o regrese výkonu a vylepšení mezi dvěma spuštění miporovnávány.

   - **Porovnání stránek -** Poskytuje sloupcový graf a procentuální porovnání výkonu mezi dvěma spuštěními na různých stránkách v testovacích běhech.

   - **Porovnání strojů -** Poskytuje data porovnání mezi dvěma spuštění na základě počítačů, které byly použity.

   - **Porovnání chyb -** Porovná typy chyb zjištěné mezi dvěma spuštěními a počtem výskytů.

     > [!TIP]
     > Pro lepší sestavy několik vlastností jsou k dispozici v zátěžové testy a testy výkonu webu, které umožňují bohatší sestavy. Požadavek na stránku má dvě vlastnosti, které jsou uvedeny v sestavách: Cíl a Název sestavy. Doba odezvy stránky bude vykázána proti cíli a místo adresy URL v přehledech bude použit název sestavy. V nastavení spuštění zátěžového testu se v části Spravovat sady čítačů zobrazí vlastnost Počítačové značky v názvech počítačů sestavy. To je velmi užitečné k popisu role konkrétního počítače v sestavě.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Generování sestav trendů zátěžového testu pomocí aplikace Excel

1. Před generováním sestavy je nutné spustit zátěžový test.

2. Sestavy zátěžových testů aplikace Excel můžete vytvářet dvěma způsoby:

   - Po dokončení zátěžového testu zvolte na stránce **Výsledky zátěžového testu** na panelu nástrojů tlačítko **Vytvořit sestavu aplikace Excel.**

      > [!NOTE]
      > Pokud je na panelu nástrojů **Prohlížeč výsledků testu výkonu webu** zakázáno tlačítko Vytvořit **sestavu aplikace Excel,** bude pravděpodobně nutné spustit aplikaci Microsoft Excel jednou, než bude povolena. Při instalaci sady Visual Studio Enterprise se doplněk zátěžového testu sady Visual Studio Enterprise zkopíruje do počítače pro aplikaci Microsoft Excel. Aplikace Microsoft Excel však musí být spuštěna k dokončení procesu instalace doplňku.

      Aplikace Microsoft Excel se otevře pomocí **Průvodce generováním sestavy zátěžového testu**.

   **Nebo**

   1. Otevřete Microsoft Excel, na pásu karet **Office** vyberte kartu **Zátěžový test** a pak zvolte **Sestava zátěžového testu**.

       Zobrazí **se Průvodce generováním sestavy zátěžového testu.**

   2. Na **stránce Select database, která obsahuje zátěžové testy,** zadejte v části **Název serveru**název serveru obsahujícívýsledky zátěžového testu.

   3. V rozevíracím seznamu **Název databáze** vyberte databázi obsahující výsledky zátěžového testu.

3. Na stránce **Jak chcete generovat sestavu** ověřte, zda je **vybraná volba Vytvořit sestavu,** a zvolte **Další**.

4. Na stránce **Jaký typ sestavy chcete generovat,** ověřte, zda je vybraná volba **Trend,** a zvolte **Další**.

5. Na stránce **Podrobnosti sestavy zátěžového testu** zadejte název sestavy do pole **Název sestavy**.

6. Vyberte zátěžový test, pro který chcete sestavu vygenerovat, a zvolte **Další**.

7. Na stránce **Vybrat spuštění sestavy** vyberte v části **Vyberte jeden nebo více spuštění, které chcete přidat do sestavy**, vyberte výsledky zátěžového testu, které chcete v sestavě porovnat, a zvolte **Další**.

8. Na stránce **Vybrat čítače pro sestavu** je v části **Vyberte jeden nebo více čítačů, které chcete přidat do sestavy**, k dispozici rozbalitelný seznam čítačů pro přizpůsobení sestavy. Vyberte čítače, které chcete porovnat pro analýzu trendů, a zvolte **Dokončit**.

9. Sestava je generována s obsahem, který obsahuje odkazy na různé karty sešitu aplikace Excel vygenerované v sestavě. Odkazy jsou založeny na čítačích vybraných pro sestavu trendů. Pokud jste například nechali výchozí čítače vybrané v kroku 7, sestava vygeneruje data, která jsou uvedena v samostatných kartách v aplikaci Excel pro každý čítač uvedený v kroku 7. Data, která jsou generována pro každý čítač je uveden v grafech stylu trendu.

   > [!TIP]
   > Pro lepší sestavy několik vlastností jsou k dispozici v zátěžové testy a testy výkonu webu, které umožňují bohatší sestavy. Požadavek na stránku má dvě vlastnosti, které jsou uvedeny v sestavách: Cíl a Název sestavy. Doba odezvy stránky bude vykázána proti cíli a místo adresy URL v přehledech bude použit název sestavy. V nastavení spuštění zátěžového testu se v části Spravovat sady čítačů zobrazí vlastnost Počítačové značky v názvech počítačů sestavy. To je velmi užitečné k popisu role konkrétního počítače v sestavě.

## <a name="net-security"></a>Zabezpečení .NET

Výsledky zátěžových testů a sestavy obsahují potenciálně citlivé informace, které mohou být použity k vytvoření útoku proti počítači nebo síti. Načíst výsledky testu a sestavy obsahují názvy počítačů a připojovací řetězce. Měli byste si to být vědomi, když sdílíte sestavy zátěžových testů s jinými lidmi.

## <a name="see-also"></a>Viz také

- [Vykazovat výsledky zatěžovacích testů pro porovnání testů nebo analýzu trendů](../test/compare-load-test-results.md)
