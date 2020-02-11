---
title: Analýza aktivity virtuálních uživatelů pro zátěžové testy
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: jillre
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dda1f35a63d3f7788faf9a94f16888c8323529c4
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091714"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Postupy: analýza, co dělají virtuálních uživatelů během zátěžového testu pomocí graf aktivity virtuálního uživatele

Zobrazení aktivity virtuálního uživatele, která je přidružená k vašemu zátěžového testu, pomocí **grafu aktivity virtuálního uživatele**. Každý řádek v tabulce představuje jednotlivého virtuálního uživatele. **Graf aktivity virtuálního uživatele** zobrazuje přesně to, co každý virtuální uživatel vykonává během testu. Můžete vidět vzory aktivity uživatelů, vzory zátěže, korelovat Nezdařená nebo pomalá testy a zobrazují požadavky pomocí další aktivity virtuálního uživatele. **Graf aktivity virtuálního uživatele** je k dispozici až po skončení běhu zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Níže uvedené postupy ukazují, jak zobrazit **graf aktivity virtuálního uživatele**, jak prozkoumat aktivitu konkrétního uživatele a jak používat filtrování.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Chcete-li zobrazit graf aktivity virtuálního uživatele ve vašich výsledcích zátěžového testu

1. Chcete-li zobrazit data virtuálního uživatele, je třeba nejprve nakonfigurovat nastavení **všechny jednotlivé podrobnosti** pro vlastnost **úložiště podrobností časování** , která je spojena s vaším zátěžovým testem. Spusťte zátěžový test.

2. Po zatížení testovacích běhů, zobrazuje souhrnnou stránku výsledků testu. Na panelu nástrojů klikněte na tlačítko **Podrobnosti o uživateli** .

     -nebo-

     Otevřete zobrazení grafů tak, že na panelu nástrojů vyberete tlačítko **grafy** . Klikněte pravým tlačítkem na graf a vyberte **Přejít k podrobnostem o uživateli**.

     Pokud použijete tuto možnost, **graf aktivity virtuálního uživatele** se automaticky přiblíží k části testu, na kterou jste klepli pravým tlačítkem. Pokud je například ukazatel na pozici přibližně 30 sekund, zobrazí se v dolní části **grafu aktivity virtuálního uživatele**v zobrazení podrobností přibližně 30 sekundová značka.

     Dále můžete v **grafu aktivity virtuálního uživatele**použít možnost prozkoumat podrobnosti o aktivitě konkrétního uživatele.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>K prozkoumání aktivita konkrétního uživatele v graf aktivity virtuálního uživatele

1. Pomocí nástroje pro přiblížení do časového období v dolní části **grafu aktivity virtuálního uživatele** vyberte oblast v grafu, ve které chcete prozkoumat podrobnosti konkrétního uživatele.

2. Podržte ukazatel myši nad podrobností v grafu. Všimněte si, že tyto informace se zobrazí v popisu tlačítka:

   - **ID uživatele**

   - **Scénář**

   - **Test**

   - **Adresa URL** (nezobrazuje se v testu nebo v transakci)

   - **Zaznamenaný**

   - **Prohlížeč** (nezobrazuje se v testu nebo v transakci)

   - **Síť**

   - **Čas spuštění**

   - **Úkolu**

   - **Agent**

   - **Protokol testu** (odkaz na protokol testu)

     > [!NOTE]
     > Pro pomoc při ladění vaší aplikace, pokud zvolíte odkaz **protokol testu** , výsledek webového testu nebo výsledek testu jednotek přidružený k otevřenému protokolu.

     V dalším kroku můžete použít operace filtrování a zvýrazňování dostupné v **grafu aktivity virtuálního uživatele**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Použití možnosti filtrování v graf aktivity virtuálního uživatele

1. V **legendě podrobností**použijte rozevírací seznam a vyberte možnost **test**, **Stránka**nebo **transakce**.

    **Panel legendy podrobností**

    ![Panel podrobné legendy](../test/media/ltest_detailslegend.png)

2. Zaškrtněte nebo zrušte zaškrtnutí políček u chyby, protokoly, testy, vyhledávání a stránky aspx, které jsou spojeny se zátěžovým testem.

    **Graf aktivity virtuálního uživatele** se aktualizuje odpovídajícím způsobem.

    **Graf aktivity virtuálního uživatele** poskytuje možnost filtrovat testy, stránky a transakce na základě několika různých kritérií. Můžete odebrat určité testy ze zobrazení, nebo odebrání všech úspěšných testů nebo odebrání testy, které se nezdařilo s některým chybám. Můžete také odebrat všechny testy, které nemají protokoly.

    Můžete například vybrat možnost **(chyby zvýrazňování)** , která zobrazí všechny chyby v grafu barevně červenou. Můžete také vybrat možnost **(zvýraznit výsledky s protokoly)** , která zobrazí všechny výsledky testů, které mají v grafu červenou barvu.

    **Panel výsledků filtru**

    ![Filtrovat panel výsledků](../test/media/ltest_filterresults.png)

3. Ve **výsledcích filtru**zaškrtněte nebo zrušte zaškrtnutí políček pro následující možnosti filtru:

   - **Zobrazit pouze výsledky s protokoly** Zobrazí pouze výsledky testů, ke kterým jsou přidruženy protokoly testů.

   - **Zobrazit úspěšné výsledky** Zobrazí úspěšné výsledky.

   - **Zobrazit výsledky s chybami** Zobrazí výsledky s chybami, které mohou pomoci při ladění.

     > [!NOTE]
     > Seznam typů chyb, které jsou uvedeny pod uzlem **Zobrazit výsledky s chybami** , lze dále prozkoumat kliknutím na tlačítko **tabulky** na panelu nástrojů **nástroje Web Performance výsledky testů Viewer** . Další informace naleznete v tématu [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     **Graf aktivity virtuálního uživatele** se aktualizuje odpovídajícím způsobem.

## <a name="see-also"></a>Viz také

- [Analýza aktivity virtuálních uživatelů v zobrazení podrobností](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Návod: použití grafu aktivity virtuálního uživatele k izolaci problémů](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)