---
title: Poměr testů pro scénář testování zatížení
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3b3bd0ae4df657d7234a77413003b18d5db86138
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895987"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Úpravy poměru testů určit, které webového výkonu, jednotek a programové testy uživatelského rozhraní mají být zahrnuty do scénáře zátěžového testu

*Poměr testů* scénáře je kombinací výběr webového výkonu a testy jednotek, které jsou součástí scénáře a distribuce těchto testů ve scénáři. Distribuce je nastavení, které určíte pro pravděpodobnost, že určitého testu bude vybrán ve virtuálních uživatelů během spuštění testu zatížení.

Po přidání sady testů k zátěžovému testu *poměr testů* kombinovat funguje stejně jako jiné možnosti. Virtuálních uživatelů náhodně vybere test, založený na pravděpodobnost, že jste zadali v kombinaci. Například pokud máte dva testy, každý 50 procent v kombinaci, nový virtuální uživatel zvolí pro spuštění prvního testu přibližně polovinu času. V kombinaci rozdělení 50/50 Pokud jeden test je dlouhý a další je krátký, pochází větší zatížení z dlouhého testu.

Po přidání testy na kombinaci, můžete ho odebrat. Distribuce poměru testů můžete také změnit pomocí kombinace ovládacího prvku. Kombinace řízení umožňuje snadno upravit distribuci testů ve scénáři.

> [!NOTE]
> Distribuce je míru pravděpodobnosti, že určitého testu bude vybrán ve virtuálních uživatelů během spuštění testu zatížení. Distribuce je vyjádřený v procentech. Proto součet čísel distribuce pro všechny testy, které jsou obsaženy ve scénáři je 100. Například pokud scénář obsahuje pouze jeden test, distribuce pro tento test je 100 % jeho obsahu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Přidejte nové testy do kombinace testů v existující scénář

Když vytvoříte nový scénář s využitím **testování Průvodce novým zátěžovým**, můžete zadat testy webového výkonu a jednotky pro přidání do poměru testů nový scénář.

Můžete přidat další testy webového výkonu a jednotku s různými text scénáře pomocí **editoru zátěžových testů**.

![Přidání testu pro existující zátěžový test](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Chcete-li přidat další testy do existujícího scénáře

1.  Otevřete zátěžový test.

2.  V **editoru zátěžových testů**, klikněte pravým tlačítkem na existující scénář a pak zvolte **přidat testy**.

     **Přidat testy** se zobrazí dialogové okno. Webového výkonu, jednotek a programové testy uživatelského rozhraní v rámci vašeho řešení, které ještě nejsou ve vašem scénáři je možné přidat do scénáře.

3.  V **dostupné testy** podokně, vyberte webového výkonu, jednotek a programové testy uživatelského rozhraní, které chcete přidat. Klikněte na šipku doprava, chcete-li přidat testy **vybrané testy** podokně.

4.  Po dokončení přidávání testů, zvolte **OK**.

     Testy jsou přidány do kombinace testů. Nová distribuce se automaticky přiřadí testy v kombinaci testů.

5.  (Volitelné) Upravte poměr ovládacího prvku k určení distribuci testů. Další informace najdete v tématu [o ovládacím prvku kombinace](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

##  <a name="remove-tests-from-a-scenario"></a>Odebrat testy ze scénáře
 ![Odebrání testu z existujícího testu zatížení](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Chcete-li odebrat testy ze scénáře

1.  Otevřete zátěžový test.

2.  V **editoru zátěžového testu**, v zátěžového testování stromu, klikněte pravým tlačítkem na scénář, ze kterého chcete odebrat test a vyberte **upravit kombinaci testů**. **Upravit kombinaci testů** se zobrazí dialogové okno.

3.  Vyberte v mřížce webového výkonu, jednotek nebo programový test uživatelského rozhraní a klikněte na tlačítko **odebrat**.

    > [!NOTE]
    > Po odebrání test upravte kombinaci testů do upřednostňovaných distribučních.

4.  Po dokončení odebírání testů, zvolte **OK**.

##  <a name="EditingTestMixAboutMixControl"></a> O ovládacím prvku kombinace
 Ovládací prvek kombinace umožňuje upravit procento zatížení, která je distribuovaná mezi testy, typu prohlížeče nebo typy sítí ve scénáři testu zatížení. Procentní hodnoty se upravit posunutím jezdce. Úpravy poměru testů určuje pravděpodobnost, že virtuální uživatel spustí konkrétní test ve scénáři testu zatížení.

 Při přesunutí posuvníku procentuální hodnoty všechny dostupné položky změnit. Pokud máte více než dvě položky, velikost, přidat nebo odebrat rovnoměrně distribuovaných mezi ostatní položky. Je možné toto chování přepsat. Pokud vyberete zaškrtávací políčko ve sloupci zámek pro konkrétní položku, uzamknout specifikované procentuální hodnotou pro danou položku. Pak při přesunutí posuvníku, velikost, přidat nebo odebrat platí jenom pro všechny zbývající položky odemknout.

 **Rozmístit** tlačítko slouží k přidělení procenta rovnoměrně mezi všechny položky. Například pokud máte tři položky, výběrem **rozmístit** nastaví procentní hodnoty 34 33 a 33.

> [!WARNING]
> **Rozmístit** tlačítko přepíše všechny položky, které jsou zamknuté.


 Je také možné zadat procentní hodnoty přímo do **%** sloupce namísto použití posuvníků. Pokud zadáte hodnotu v procentech přímo, nebude se automaticky upraví další položky.

> [!NOTE]
> Posuvníky jsou zakázané, pokud celkový počet nepřidá do 100 %, nebo pokud procentní hodnoty zadané do **%** sloupce jsou desetinná čísla.


 Když ručně zadáte procentní hodnoty, by měl Ujistěte se, že součet všech položek je 100 %. Při ukládání kombinaci, nejsou-li součet 100 %, vyzve tak, aby přijímal procentní hodnoty, jak jsou, nebo se vrátit a upravte je tak. Pokud budete chtít nepřijmete, jak jsou, budou se poměrné přepočítání na 100 %.  Pokud máte dvě položky a je ručně nastaveno na 80 % až 40 %, nastaví se první položka % 66.67 (80 dělený 120) a nastaví se druhá položka % 33,33 (40 dělený 120).

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)