---
title: Kombinace testů pro scénář zátěžového testu
description: Naučte se, jak upravit kombinaci testů scénáře, která je kombinací výběru výkonnosti webu a testování částí a distribuce těchto testů.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.openlocfilehash: 99cc7f629fe28bb241033113bdecca043d67f032
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926791"
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

Pomocí **Editor zátěžového testu** můžete přidat další testy výkonu webu a testování částí na textovou kombinaci scénáře.

![Přidání testu do stávajícího zátěžového testu](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Přidání dalších testů do existujícího scénáře

1. Otevřete zátěžový test.

2. V **Editor zátěžového testu** klikněte pravým tlačítkem myši na existující scénář a zvolte možnost **Přidat testy**.

     Zobrazí se dialogové okno **Přidat testy** . Všechny webové testy webového výkonu, jednotky a programový test uživatelského rozhraní ve vašem řešení, které ještě nejsou ve vašem scénáři, jsou k dispozici pro přidání do scénáře.

3. V podokně **Dostupné testy** vyberte webový výkon, jednotku a programové testy uživatelského rozhraní, které chcete přidat. Kliknutím na šipku doprava přidejte testy do podokna **vybrané testy** .

4. Až skončíte s přidáváním testů, klikněte na **tlačítko OK**.

     Testy jsou přidány do kombinace testů. Nové distribuci je automaticky přiřazeno k testům v kombinaci testů.

5. Volitelné Upravte ovládací prvek míchání pro určení distribuce testu. Další informace naleznete v tématu [o ovládacím prvku míchání](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Odebrání testů ze scénáře
![Odebrání testu z existujícího zátěžového testu](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Odebrání testů ze scénáře

1. Otevřete zátěžový test.

2. V **Editor zátěžového testu** ve stromu zátěžového testu klikněte pravým tlačítkem myši na scénář, ze kterého chcete odebrat test, a vyberte možnost **Upravit kombinaci testů**. Zobrazí se dialogové okno **Upravit kombinaci testů** .

3. V mřížce vyberte webový výkon, jednotku nebo programový test uživatelského rozhraní a pak zvolte možnost **Odebrat**.

    > [!NOTE]
    > Po odebrání testu upravte kombinaci testů na upřednostňovanou distribuci.

4. Po dokončení odebírání testů klikněte na **tlačítko OK**.

## <a name="about-the-mix-control"></a><a name="EditingTestMixAboutMixControl"></a> O ovládacím prvku míchání
Ovládací prvek mix umožňuje upravit procento zatížení, které je distribuováno mezi testy, typy prohlížečů nebo typy sítě ve scénáři zátěžového testu. Procentuální hodnoty upravíte přesunutím jezdců. Úprava kombinace pro testy určuje pravděpodobnost, že virtuální uživatel spustí určitý test ve scénáři zátěžového testu.

Při přesunutí posuvníku se změní procentuální hodnoty všech dostupných položek. Pokud máte více než dvě položky, je množství, které přidáváte nebo odebíráte, rozděleno rovnoměrně mezi ostatní položky. Toto chování je možné přepsat. Pokud zaškrtnete políčko ve sloupci uzamknout pro konkrétní položku, zamknete pro tuto položku zadanou procentuální hodnotu. Když přesunete posuvník, množství, které přidáte nebo odeberete, se použije jenom u zbývajících odemčených položek.

Tlačítko **rozmístit** se používá k přidělení procent rovnoměrně mezi všechny položky. Například pokud máte tři položky, volba **distribuovat** nastaví procentuální hodnoty na 34, 33 a 33.

> [!WARNING]
> Tlačítko **distribuovat** přepisuje všechny položky, které jsou zamčené.

Je také možné zadat hodnoty procent přímo do **%** sloupce místo pomocí posuvníků. Pokud zadáte hodnotu v procentech přímo, ostatní položky se automaticky neupraví.

> [!NOTE]
> Když celkový součet nepřidá až 100%, nebo když jsou procentuální hodnoty zadané do sloupce desetinná, jsou posuvníky zakázané **%** .

Když zadáte procentuální hodnoty ručně, měli byste se ujistit, že součet všech položek je 100%. Když uložíte směs, pokud součet není 100%, budete vyzváni, abyste přijali procentuální hodnoty tak, jak jsou, nebo se vrátíte a upravíte. Pokud se rozhodnete je přijmout, bude se poměrně 100%.  Pokud máte například dvě položky a ručně jste je nastavili na 80% a 40%, bude první položka nastavena na 66,67% (80 dělena 120) a druhá položka bude nastavena na 33,33% (40 dělený 120).

## <a name="see-also"></a>Viz také

- [Úpravy scénářů zátěžového testu](../test/edit-load-test-scenarios.md)
