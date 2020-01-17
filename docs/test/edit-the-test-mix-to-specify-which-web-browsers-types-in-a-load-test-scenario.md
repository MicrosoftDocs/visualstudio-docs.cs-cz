---
title: Prohlížeč poměru testů pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 394331ae06760e0547cfc2b5a37a6dcd357e3614
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114531"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Úpravy poměru testů určující typy webových prohlížečů ve scénáři zátěžového testu

*Kombinace prohlížečů* poskytuje způsob, jak simulovat zatížení více realisticky v případě zkušebního scénáře. Zatížení je generováno pomocí heterogenní kombinace prohlížečů místo jednoho jediného webového prohlížeče. Můžete vytvořit užší odhad prohlížečů, které budou použity s vašimi aplikacemi.

Kombinace prohlížečů určuje pravděpodobnost, že virtuální uživatel spustí typ konkrétní webové prohlížeče ve scénáři testu zatížení. Když vytvoříte zátěžový test, můžete simulovat, zatížení je generováno pomocí více než jeden webový prohlížeč. Když přidáte typ webového prohlížeče do kombinaci ze sady webových prohlížečů, které jsou k dispozici, sadu přidružená záhlaví pro vybraný webový prohlížeč se přidá do každého požadavku HTTP, který se odešle podle testu výkonnosti webu.

Kombinace prohlížečů funguje stejně jako jiné kombinace možností. Typ webového prohlížeče náhodně souvisí s virtuálního uživatele, založené na kombinaci prohlížečů. Spuštění testů daného uživatele na konkrétní webový prohlížeč, podle pravděpodobnost, že jste zadali v kombinaci.

Po zadání kombinace prohlížečů, můžete později přidat a odebrat typy webových prohlížečů na kombinaci. Distribuce kombinace prohlížečů můžete také změnit pomocí kombinace ovládacího prvku. Kombinace řízení umožňuje snadno upravit kombinace prohlížečů ve scénáři.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Přidat nové prohlížeče do scénáře

### <a name="to-add-new-browsers-to-a-scenario"></a>Chcete-li přidat nové prohlížeče do scénáře

1. Zatímco probíhá zadání kombinace prohlížečů pro scénáře vyberte **přidat**.

     Přidání nové položky prohlížeče do mřížky.

    > [!NOTE]
    > Chcete-li zobrazit **upravit poměr prohlížečů** dialogové okno, klikněte pravým tlačítkem na existující scénář a pak vyberte **upravit poměr prohlížečů**.

2. V **typ prohlížeče** sloupce, klikněte na šipku pro novou položku a zvolte typ požadované prohlížeče.

3. (Volitelné) Upravte poměr ovládacího prvku k určení distribuci testů.

4. Po dokončení přidávání prohlížečů, zvolte **OK**.

## <a name="remove-browsers-from-a-scenario"></a>Odebrání scénáři prohlížeče

### <a name="to-remove-browsers-from-a-scenario"></a>Chcete-li odebrat prohlížečů ze scénáře

1. Otevřete zátěžový test.

2. Klikněte pravým tlačítkem na scénář, ze kterého chcete odebrat prohlížeče a klikněte na tlačítko **upravit poměr prohlížečů**.

     **Upravit poměr prohlížečů** se zobrazí dialogové okno.

3. Vyberte prohlížeče v mřížce a potom zvolte **odebrat**.

4. (Volitelné) Upravte poměr ovládacího prvku k určení distribuci testů.

5. Po dokončení odebírání prohlížečů, zvolte **OK**.

## <a name="about-the-mix-control"></a>O ovládacím prvku kombinace

Ovládací prvek kombinace umožňuje upravit procento zatížení, která je distribuovaná mezi testy, typu prohlížeče nebo typy sítí ve scénáři testu zatížení. Procentní hodnoty se upravit posunutím jezdce. Úprava kombinaci pro typy prohlížečů určuje pravděpodobnost, že virtuální uživatel spustí typu určitého webového prohlížeče ve scénáři testu zatížení.

Při přesunutí posuvníku procentuální hodnoty všechny dostupné položky změnit. Pokud máte více než dvě položky, velikost, přidat nebo odebrat rovnoměrně distribuovaných mezi ostatní položky. Je možné toto chování přepsat. Pokud vyberete zaškrtávací políčko ve sloupci zámek pro konkrétní položku, uzamknout specifikované procentuální hodnotou pro danou položku. Pak při přesunutí posuvníku, velikost, přidat nebo odebrat platí jenom pro všechny zbývající položky odemknout.

**Rozmístit** tlačítko slouží k přidělení procentní hodnoty rovnoměrně mezi všechny položky. Například pokud máte tři položky, výběrem **rozmístit** nastaví procentní hodnoty 34 33 a 33.

> [!WARNING]
> **Rozmístit** tlačítko přepíše všechny položky, které jsou zamknuté.

Je také možné zadat procentní hodnoty přímo do **%** sloupce namísto použití posuvníků. Pokud zadáte hodnotu v procentech přímo, nebude se automaticky upraví další položky.

> [!NOTE]
> Posuvníky jsou zakázané, pokud celkový počet nepřidá do 100 %, nebo pokud procentní hodnoty zadané do **%** sloupce jsou desetinná čísla.

Když ručně zadáte procentní hodnoty, by měl Ujistěte se, že součet všech položek je 100 %. Při ukládání kombinaci, nejsou-li součet 100 %, vyzve tak, aby přijímal procentní hodnoty, jak jsou, nebo se vrátit a upravte je tak. Pokud budete chtít nepřijmete, jak jsou, budou se poměrné přepočítání na 100 %.  Pokud máte dvě položky a je ručně nastaveno na 80 % až 40 %, nastaví se první položka % 66.67 (80 dělený 120) a nastaví se druhá položka % 33,33 (40 dělený 120).

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
