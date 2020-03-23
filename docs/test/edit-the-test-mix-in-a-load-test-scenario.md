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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595927"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Upravte kombinaci testů a určete, který výkon webu, testy jednotky a kódovaného uživatelského rozhraní mají být zahrnuty do scénáře zátěžového testu

*Kombinace testů* scénáře je kombinací výběru výkonu webu a testování částí, které jsou obsaženy ve scénáři a distribuce těchto testů ve scénáři. Distribuce je nastavení, které můžete zadat pro pravděpodobnost, že konkrétní test bude vybrán virtuálním uživatelem během spuštění zátěžového testu.

Po přidání sady testů do zátěžového testu funguje *kombinace testů* stejně jako ostatní možnosti kombinace. Virtuální uživatel náhodně vybere test na základě pravděpodobnosti, kterou jste zadali v mixu. Například pokud máte dva testy, každý 50 procent v mixu, nový virtuální uživatel se rozhodne spustit první test přibližně polovinu času. V mixu 50/50, pokud je jeden test dlouhý a druhý krátký, větší zatížení pochází z dlouhého testu.

Po přidání testů do mixu je můžete odebrat. Můžete také změnit rozložení kombinace testů pomocí ovládacího prvku mix. Ovládací prvek mix umožňuje snadno upravit rozložení testů ve scénáři.

> [!NOTE]
> Distribuce je míra pravděpodobnosti, že konkrétní test bude vybrán virtuálním uživatelem během spuštění zátěžového testu. Rozdělení je vyjádřeno v procentech. Proto součet distribučních čísel pro všechny testy, které jsou obsaženy ve scénáři je 100. Například pokud scénář obsahuje pouze jeden test, distribuce pro tento test je 100 procent.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Přidání nových testů do kombinace testů v existujícím scénáři

Při vytváření nového scénáře pomocí **Průvodce novým zátěžového testu**můžete určit výkon webu a testy částí, které chcete přidat do kombinace testů nového scénáře.

Můžete přidat další webové výkon a testování částí do textové kombinace scénáře pomocí **Editoru zátěžového testu**.

![Přidání testu do existujícího zátěžového testu](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Přidání dalších testů do existujícího scénáře

1. Otevřete zátěžový test.

2. V **Editoru zátěžových testů**klepněte pravým tlačítkem myši na existující scénář a pak zvolte **Přidat testy**.

     Zobrazí se dialogové okno **Přidat testy.** Všechny testy výkonu webu, jednotky a kódované uživatelské rozhraní ve vašem řešení, které ještě nejsou ve vašem scénáři, jsou k dispozici pro přidání do scénáře.

3. V podokně **Dostupné testy** vyberte webové testy výkonu, jednotky a kódované uživatelské rozhraní, které chcete přidat. Zvolte šipku vpravo, chcete-li přidat testy do **podokna Vybrané testy.**

4. Po přidání testů zvolte **OK**.

     Testy se přidají do testovací směsi. Nové rozdělení je automaticky přiřazeno k testům v testovací směsi.

5. (Nepovinné) Nastavte ovládací prvek mix udáváte rozložení testu. Další informace naleznete [v tématu O ovládacím prvku mix](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Odebrání testů ze scénáře
![Odebrání testu z existujícího zátěžového testu](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Odebrání testů ze scénáře

1. Otevřete zátěžový test.

2. V **Editoru zátěžových testů**klikněte ve stromu zátěžového testu pravým tlačítkem myši na scénář, ze kterého chcete odebrat test, a vyberte **příkaz Upravit kombinaci testů**. Zobrazí se dialogové okno **Upravit kombinaci testů.**

3. Vyberte test výkonu webu, jednotky nebo kódovaného uživatelského prostředí v mřížce a pak zvolte **Odebrat**.

    > [!NOTE]
    > Po odebrání testu upravte kombinaci testů podle upřednostňovaného rozdělení.

4. Po dokončení odebrání testů zvolte **OK**.

## <a name="about-the-mix-control"></a><a name="EditingTestMixAboutMixControl"></a>O ovládacím prvku Mix
Ovládací prvek mix umožňuje upravit procento zatížení, které je distribuováno mezi testy, typy prohlížečů nebo typy sítí ve scénáři zátěžového testu. Procentuální hodnoty můžete upravit posunutím jezdců. Úprava kombinace pro testy určuje pravděpodobnost, že virtuální uživatel spouštějící určitý test ve scénáři zátěžového testu.

Když posunete jezdec, změní se procentuální hodnoty všech dostupných položek. Pokud máte více než dvě položky, částka, kterou přidáte nebo odeberete, je rovnoměrně rozdělena mezi ostatní položky. Je možné přepsat toto chování. Pokud zaškrtnete políčko ve sloupci zámku pro určitou položku, uzamknete zadanou hodnotu procenta pro tuto položku. Když potom posunete jezdec, částka, kterou přidáte nebo odeberete, se použije pouze na všechny zbývající odemčené položky.

Tlačítko **Distribuovat** se používá k rozdělení procent rovnoměrně mezi všechny položky. Pokud máte například tři položky, zvolte **Rozmístění,** nastaví tecesní hodnoty na 34, 33 a 33.

> [!WARNING]
> Tlačítko **Rozmístit** přepíše všechny položky, které jsou zamknuté.

Je také možné zadat procentuální **%** hodnoty přímo do sloupce namísto použití posuvníků. Pokud zadáte procentuální hodnotu přímo, ostatní položky se automaticky neupraví.

> [!NOTE]
> Posuvníky jsou zakázány, pokud součet nepřidá až 100 %, nebo pokud jsou procentuální hodnoty zadané do **%** sloupce desetinné čárky.

Při ručním zadávání procentuálních hodnot byste se měli ujistit, že součet všech položek je 100 %. Pokud při uložení směsi neobdržíte součet 100 %, budete vyzváni k přijetí procentuálních hodnot tak, jak jsou, nebo k jejich vrácení a úpravě. Pokud se rozhodnete je přijmout tak, jak jsou, budou poměrně 100%.  Pokud například máte dvě položky a ručně je nastavíte na 80 % a 40 %, bude první položka nastavena na 66,67 % (80 děleno 120) a druhá položka bude nastavena na 33,33 % (40 vydělených 120).

## <a name="see-also"></a>Viz také

- [Úpravy scénářů zátěžového testu](../test/edit-load-test-scenarios.md)
