---
title: Analýza aktivity virtuálních uživatelů pro zátěžové testy
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 0cac452a7fa4799c986df0f182643ed1b94afbe6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059519"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Postupy: analýza, co dělají virtuálních uživatelů během zátěžového testu pomocí graf aktivity virtuálního uživatele

Zobrazit aktivity virtuálního uživatele, který je spojen se zátěžovým testem pomocí **graf aktivity virtuálního uživatele**. Každý řádek v tabulce představuje jednotlivého virtuálního uživatele. **Graf aktivity virtuálního uživatele** zobrazuje přesně co jednotlivé virtuální uživatele se provádí během testu. Můžete vidět vzory aktivity uživatelů, vzory zátěže, korelovat Nezdařená nebo pomalá testy a zobrazují požadavky pomocí další aktivity virtuálního uživatele. **Graf aktivity virtuálního uživatele** je k dispozici pouze po dokončení zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující postupy ukazují, jak zobrazit **graf aktivity virtuálního uživatele**, jak zkoumat aktivita konkrétního uživatele a jak pomocí filtrování.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Chcete-li zobrazit graf aktivity virtuálního uživatele ve vašich výsledcích zátěžového testu

1.  Chcete-li zobrazit data virtuálního uživatele, je nutné nejprve nakonfigurovat **detaily o všech jednotlivých položkách** nastavení **úložiště podrobností časování** vlastnost, která je spojen se zátěžovým testem. Spusťte zátěžový test.

2.  Po zatížení testovacích běhů, zobrazuje souhrnnou stránku výsledků testu. Zvolte **podrobnosti uživatele** tlačítko na panelu nástrojů.

     -nebo-

     Otevřít zobrazení grafů výběrem **grafy** tlačítko na panelu nástrojů. Klikněte pravým tlačítkem na graf a potom vyberte **přejít na podrobnosti uživatele**.

     Pokud použijete tuto možnost, **graf aktivity virtuálního uživatele** bude automatické přiblížení část testu, který jste klikli pravým tlačítkem myši. Například, pokud ukazatel myši nachází na přibližně 30 druhý označit, zobrazení podrobností se zobrazí přibližně na značce 30 druhý v **přiblížení na dobu** nástroj v dolní části **graf aktivity virtuálního uživatele** .

     Dále můžete prozkoumat podrobnosti o aktivitě konkrétního uživatele v **graf aktivity virtuálního uživatele**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>K prozkoumání aktivita konkrétního uživatele v graf aktivity virtuálního uživatele

1. Použít funkce zvětšení na čas období nástroj v dolní části **graf aktivity virtuálního uživatele** vyberte oblast v grafu, ve které chcete prozkoumat podrobnosti o konkrétního uživatele.

2. Podržte ukazatel myši nad podrobností v grafu. Všimněte si, že tyto informace se zobrazí v popisu tlačítka:

   - **Id uživatele**

   - **Scénář**

   - **Test**

   - **Adresa URL** (nejsou zobrazeny v testu nebo transakce)

   - **Výsledek**

   - **Prohlížeč** (nejsou zobrazeny v testu nebo transakce)

   - **Sítě**

   - **Čas spuštění**

   - **Doba trvání**

   - **Agent**

   - **Protokol testu** (odkaz na protokol testu)

     > [!NOTE]
     > Jako pomoc při ladění aplikace, pokud se rozhodnete **protokol testu** odkaz, výsledek webového testu nebo přidružené k protokolu otevřít výsledek testu jednotek.

     Dále můžete pomocí filtrování a zvýraznění operace jsou dostupné v **graf aktivity virtuálního uživatele**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Použití možnosti filtrování v graf aktivity virtuálního uživatele

1. V **podrobné legendy**, pomocí rozevíracího seznamu vyberte buď **testovací**, **stránky**, nebo **transakce**.

    **Panel podrobné legendy**

    ![Panel podrobné legendy](../test/media/ltest_detailslegend.png)

2. Zaškrtněte nebo zrušte zaškrtnutí políček u chyby, protokoly, testy, vyhledávání a stránky aspx, které jsou spojeny se zátěžovým testem.

    **Graf aktivity virtuálního uživatele** odpovídajícím způsobem aktualizuje.

    **Graf aktivity virtuálního uživatele** umožňuje filtrovat testy, stránky a transakce na základě několika různých kritérií. Můžete odebrat určité testy ze zobrazení, nebo odebrání všech úspěšných testů nebo odebrání testy, které se nezdařilo s některým chybám. Můžete také odebrat všechny testy, které nemají protokoly.

    Například můžete vybrat **(zvýraznit chyby)** možnost, která se zobrazí všechny chyby v grafu zobrazí červeně. Můžete také vybrat **(zvýraznit výsledky s protokoly)** možnost, která se zobrazí všechny výsledky testů, které mají protokoly vybarvenými zeleně v grafu.

    **Filtrovat panel výsledků**

    ![Filtrovat panel výsledků](../test/media/ltest_filterresults.png)

3. V **filtrování výsledků**zaškrtněte nebo zrušte zaškrtnutí políček pro následující možnosti filtru:

   - **Zobrazit pouze výsledky s protokoly** zobrazí pouze výsledky, které mají protokolů testu k nim má přiřazené testů.

   - **Zobrazit úspěšné výsledky** úspěšné výsledky se zobrazí.

   - **Zobrazit výsledky s chybami** zobrazuje výsledky s chybami, které vám můžou pomoct při ladění.

     > [!NOTE]
     > Seznam typů chyb, které jsou uvedeny v části **zobrazit výsledky s chybami** uzel můžete zkoumat výběrem **tabulky** tlačítko **prohlížeče výsledků testu výkonnosti webu** nástrojů. Další informace najdete v tématu [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     **Graf aktivity virtuálního uživatele** odpovídajícím způsobem aktualizuje.

## <a name="see-also"></a>Viz také:

- [Analýza aktivity virtuálních uživatelů v podrobném zobrazení](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Návod: Izolace potíží s pomocí graf aktivity virtuálního uživatele](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)