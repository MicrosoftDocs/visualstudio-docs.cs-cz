---
title: Kombinace testů pro scénář zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a52d660140416ce829493a733171cfcf64ebbe4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595927"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Úpravou kombinace testů určete, který webový výkon, jednotku a programové testy uživatelského rozhraní mají být zahrnuty do scénáře zátěžového testu.

Kombinace *testů* scénáře je kombinací výběru výkonnosti webu a testů jednotek, které jsou obsaženy ve scénáři a rozdělení těchto testů ve scénáři. Distribuce je nastavení, které můžete zadat pro pravděpodobnost, že se konkrétní test vybere pomocí virtuálního uživatele během spuštění zátěžového testu.

Po přidání sady testů do zátěžového testu funguje *kombinace testů* jako jiné možnosti kombinace. Virtuální uživatel náhodně vybere test na základě pravděpodobnosti, kterou jste zadali v kombinaci. Například pokud máte dva testy, každý 50% v kombinaci, nový virtuální uživatel zvolí spuštění prvního testu přibližně po poloviční dobu. V kombinaci 50/50, je-li jeden test dlouhý a druhý je krátký, větší zatížení přichází z dlouhého testu.

Po přidání testů do kombinace je můžete odebrat. Můžete také změnit rozdělení kombinace testů pomocí ovládacího prvku míchání. Ovládací prvek míchání umožňuje snadno upravit distribuci testů ve scénáři.

> [!NOTE]
> Distribuce je míra pravděpodobnosti, že během běhu zátěžového testu bude vybrán konkrétní test virtuálním uživatelem. Distribuce se vyjadřuje jako procento. Proto součet distribučních čísel pro všechny testy, které jsou obsaženy ve scénáři, je 100. Například pokud scénář obsahuje pouze jeden test, distribuce pro tento test je 100%.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Přidání nových testů do kombinace testů v existujícím scénáři

Když vytvoříte nový scénář pomocí **nového Průvodce zátěžovým testem**, můžete zadat testy výkonnosti webu a jednotky, které chcete přidat do kombinace testů v novém scénáři.

Pomocí **Editor zátěžového testu**můžete přidat další testy výkonu webu a testování částí na textovou kombinaci scénáře.

![Přidání testu do stávajícího zátěžového testu](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Přidání dalších testů do existujícího scénáře

1. Otevřete zátěžový test.

2. V **Editor zátěžového testu**klikněte pravým tlačítkem myši na existující scénář a zvolte možnost **Přidat testy**.

     Zobrazí se dialogové okno **Přidat testy** . Všechny webové testy webového výkonu, jednotky a programový test uživatelského rozhraní ve vašem řešení, které ještě nejsou ve vašem scénáři, jsou k dispozici pro přidání do scénáře.

3. V podokně **Dostupné testy** vyberte webový výkon, jednotku a programové testy uživatelského rozhraní, které chcete přidat. Kliknutím na šipku doprava přidejte testy do podokna **vybrané testy** .

4. Až skončíte s přidáváním testů, klikněte na **tlačítko OK**.

     Testy jsou přidány do kombinace testů. Nové distribuci je automaticky přiřazeno k testům v kombinaci testů.

5. (Volitelné) Upravte poměr ovládacího prvku k určení distribuci testů. Další informace najdete v tématu [o ovládacím prvku kombinace](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Odebrání testů ze scénáře
![Odebrání testu z existujícího zátěžového testu](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Odebrání testů ze scénáře

1. Otevřete zátěžový test.

2. V **Editor zátěžového testu**ve stromu zátěžového testu klikněte pravým tlačítkem myši na scénář, ze kterého chcete odebrat test, a vyberte možnost **Upravit kombinaci testů**. **Upravit kombinaci testů** se zobrazí dialogové okno.

3. V mřížce vyberte webový výkon, jednotku nebo programový test uživatelského rozhraní a pak zvolte možnost **Odebrat**.

    > [!NOTE]
    > Po odebrání testu upravte kombinaci testů na upřednostňovanou distribuci.

4. Po dokončení odebírání testů klikněte na **tlačítko OK**.

## <a name="EditingTestMixAboutMixControl"></a>O ovládacím prvku míchání
Ovládací prvek kombinace umožňuje upravit procento zatížení, která je distribuovaná mezi testy, typu prohlížeče nebo typy sítí ve scénáři testu zatížení. Procentní hodnoty se upravit posunutím jezdce. Úprava kombinace pro testy určuje pravděpodobnost, že virtuální uživatel spustí určitý test ve scénáři zátěžového testu.

Při přesunutí posuvníku procentuální hodnoty všechny dostupné položky změnit. Pokud máte více než dvě položky, velikost, přidat nebo odebrat rovnoměrně distribuovaných mezi ostatní položky. Je možné toto chování přepsat. Pokud vyberete zaškrtávací políčko ve sloupci zámek pro konkrétní položku, uzamknout specifikované procentuální hodnotou pro danou položku. Pak při přesunutí posuvníku, velikost, přidat nebo odebrat platí jenom pro všechny zbývající položky odemknout.

Tlačítko **rozmístit** se používá k přidělení procent rovnoměrně mezi všechny položky. Například pokud máte tři položky, výběrem **rozmístit** nastaví procentní hodnoty 34 33 a 33.

> [!WARNING]
> **Rozmístit** tlačítko přepíše všechny položky, které jsou zamknuté.

Je také možné zadat procentní hodnoty přímo do **%** sloupce namísto použití posuvníků. Pokud zadáte hodnotu v procentech přímo, nebude se automaticky upraví další položky.

> [!NOTE]
> Posuvníky jsou zakázané, pokud celkový počet nepřidá do 100 %, nebo pokud procentní hodnoty zadané do **%** sloupce jsou desetinná čísla.

Když ručně zadáte procentní hodnoty, by měl Ujistěte se, že součet všech položek je 100 %. Při ukládání kombinaci, nejsou-li součet 100 %, vyzve tak, aby přijímal procentní hodnoty, jak jsou, nebo se vrátit a upravte je tak. Pokud budete chtít nepřijmete, jak jsou, budou se poměrné přepočítání na 100 %.  Pokud máte dvě položky a je ručně nastaveno na 80 % až 40 %, nastaví se první položka % 66.67 (80 dělený 120) a nastaví se druhá položka % 33,33 (40 dělený 120).

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
