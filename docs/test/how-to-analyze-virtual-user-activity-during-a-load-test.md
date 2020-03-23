---
title: Analyzovat aktivitu virtuálního uživatele pro zátěžové testy
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c997f27e65a8e3992239fac78d52b0b4f19670c3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169401"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Postup: Analýza toho, co virtuální uživatelé dělají během zátěžového testu pomocí grafu aktivity virtuálního uživatele

Zobrazení aktivity virtuálního uživatele, která je přidružena k zátěžovému testu, pomocí **grafu aktivity virtuálního uživatele**. Každý řádek v grafu představuje jednotlivého virtuálního uživatele. **Graf aktivity virtuálního uživatele** zobrazuje přesně to, co každý virtuální uživatel prováděl během testu. Můžete zobrazit vzory aktivity uživatele, vzory zatížení, korelovat neúspěšné nebo pomalé testy a zobrazit požadavky s jinými aktivitami virtuálního uživatele. **Graf aktivity virtuálního uživatele** je k dispozici pouze po dokončení zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Níže uvedené postupy ukazují, jak zobrazit **virtuální graf aktivity uživatele**, jak prozkoumat aktivitu konkrétního uživatele a jak používat filtrování.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Zobrazení grafu aktivity virtuálního uživatele ve výsledcích zátěžového testu

1. Chcete-li zobrazit virtuální uživatelská data, musíte nejprve nakonfigurovat nastavení **Všechny jednotlivé podrobnosti** pro vlastnost **Úložiště podrobností časování,** která je přidružena k zátěžovému testu. Potom spusťte zátěžový test.

2. Po spuštění zátěžového testu se zobrazí stránka souhrnu výsledků testu. Zvolte tlačítko **Podrobnosti uživatele** na panelu nástrojů.

     -nebo-

     Otevřete zobrazení Grafy výběrem tlačítka **Grafy** na panelu nástrojů. Klepněte pravým tlačítkem myši na graf a vyberte **možnost Přejít na podrobnosti uživatele**.

     Pokud použijete tuto možnost, **virtuální graf aktivity uživatele** se automaticky zvětšuje na část testu, na kterou jste klepnuli pravým tlačítkem myši. Pokud je například ukazatel umístěn přibližně na značce 30 sekund, zobrazí se v detailním zobrazení přibližně na 30sekundové značce v nástroji **Lupa na časové období** v dolní části **grafu aktivity virtuálního uživatele**.

     Dále můžete použít prozkoumat podrobnosti o aktivitě konkrétního uživatele v **grafu aktivity virtuálního uživatele**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Chcete-li prozkoumat aktivitu konkrétního uživatele v grafu aktivity virtuálního uživatele

1. Pomocí nástroje Lupa na časové období v dolní části **grafu aktivity virtuálního uživatele** vyberte oblast v grafu, ve které chcete prozkoumat podrobnosti o konkrétním uživateli.

2. Najeďte myší na detail v grafu. Všimněte si, že v tipu nástroje jsou zobrazeny následující informace:

   - **ID uživatele**

   - **Scénář**

   - **Test**

   - **URL** (Nezobrazuje se v testu nebo transakci)

   - **Výsledek**

   - **Prohlížeč** (Nezobrazuje se v testu nebo transakci)

   - **Síť**

   - **Čas zahájení**

   - **Doba trvání**

   - **Agent**

   - **Protokol testu** (odkaz na testovací protokol)

     > [!NOTE]
     > Chcete-li pomoci při ladění aplikace, pokud zvolíte odkaz **Protokol test,** výsledek webového testu nebo výsledek testu částí spojené s protokolu otevřít.

     Dále můžete použít operace filtrování a zvýraznění, které jsou k dispozici v **grafu aktivity virtuálního uživatele**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Použití možností filtrování v grafu aktivity virtuálního uživatele

1. V **legendě podrobností**vyberte pomocí rozevíracího seznamu **buď test**, **stránku**nebo **transakci**.

    **Panel Legenda detailů**

    ![Panel Legenda podrobností](../test/media/ltest_detailslegend.png)

2. Zaškrtněte nebo zrušte zaškrtnutí políček pro stránky chyb, protokolů, testů, vyhledávání a aspx, které jsou přidruženy k zátěžovému testu.

    **Graf aktivity virtuálního uživatele se** odpovídajícím způsobem aktualizuje.

    **Virtuální graf aktivity uživatele** poskytuje možnost odfiltrovat testy, stránky a transakce na základě několika různých kritérií. Můžete odebrat určité testy ze zobrazení nebo odebrat všechny úspěšné testy nebo odebrat testy, které se nezdařily s určitými chybami. Můžete také odebrat všechny testy, které nemají protokoly.

    Můžete například vybrat možnost **(Zvýraznit chyby),** která zobrazí všechny chyby v grafu červeně. Můžete také vybrat **(Zvýraznit výsledky pomocí protokolů),** která zobrazí všechny výsledky testů, které mají v grafu zelené protokoly.

    **Panel výsledků filtru**

    ![Panel výsledků filtru](../test/media/ltest_filterresults.png)

3. Ve **výsledcích filtru**zaškrtněte nebo zrušte zaškrtnutí políček u následujících možností filtru:

   - **Zobrazit pouze výsledky s protokoly** Zobrazí pouze výsledky testů, které mají protokoly testů s nimi spojené.

   - **Zobrazit úspěšné výsledky** Zobrazí úspěšné výsledky.

   - **Zobrazit výsledky s chybami** Zobrazí výsledky s chybami, které mohou pomoci při ladění.

     > [!NOTE]
     > Seznam typů chyb, které jsou uvedeny v uzlu **Zobrazit výsledky s chybami,** lze dále prozkoumat výběrem tlačítka **Tabulky** v panelu nástrojů Prohlížeč výsledků testu **výkonu webu.** Další informace naleznete [v tématu Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     **Graf aktivity virtuálního uživatele se** odpovídajícím způsobem aktualizuje.

## <a name="see-also"></a>Viz také

- [Analýza aktivity virtuálního uživatele v zobrazení Podrobnosti](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Návod: Použití grafu aktivity virtuálního uživatele k odištit problémy](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)