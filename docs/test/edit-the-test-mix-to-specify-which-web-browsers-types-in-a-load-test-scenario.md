---
title: Kombinace testů prohlížeče pro zátěžové testování
description: Naučte se, jak upravit kombinaci prohlížečů, která vám dává možnost simulovat ve scénáři zátěžového testu realističtější zatížení.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.openlocfilehash: 3b68bbfbca83219b10e56bf1cc3794bbb43231ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926765"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Upravit poměr testů pro určení typů webových prohlížečů ve scénáři zátěžového testu

*Kombinace prohlížečů* nabízí způsob, jak simulovat zatížení realističtější v rámci scénáře zátěžového testu. Zatížení je generováno pomocí heterogenní kombinace webových prohlížečů místo jednoho jediného webového prohlížeče. Vytvoříte užší přibližný odhad webových prohlížečů, které budou použity s vašimi aplikacemi.

Kombinace prohlížečů určuje pravděpodobnost, že virtuální uživatel spustí určitý typ webového prohlížeče v rámci scénáře zátěžového testu. Při vytváření zátěžového testu může být vhodné simulovat, že se zatížení generuje prostřednictvím více než jednoho webového prohlížeče. Když do směsi přidáte typ webového prohlížeče ze sady webových prohlížečů, které jsou k dispozici, přidají se do každého požadavku HTTP, který odešle test výkonnosti webu, sadu přidružených hlaviček pro vybraný webový prohlížeč.

Kombinace prohlížečů funguje podobně jako další možnosti kombinace. Typ webového prohlížeče je náhodně přidružen k virtuálnímu uživateli na základě kombinace prohlížečů. Testy tohoto uživatele se spouštějí v konkrétním webovém prohlížeči na základě pravděpodobnosti, kterou jste zadali v kombinaci.

Po zadání kombinace prohlížečů můžete později do kombinace přidat a odebrat typy webového prohlížeče. Můžete také změnit rozdělení kombinace prohlížečů pomocí ovládacího prvku míchání. Ovládací prvek míchání umožňuje snadno upravit distribuci prohlížečů ve scénáři.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Přidání nových prohlížečů do scénáře

### <a name="to-add-new-browsers-to-a-scenario"></a>Přidání nových prohlížečů do scénáře

1. Když v procesu zadávání kombinace prohlížečů pro scénář zvolíte **Přidat**.

     Do mřížky se přidá nová položka prohlížeče.

    > [!NOTE]
    > Chcete-li zobrazit dialogové okno **Upravit kombinaci prohlížečů** , klikněte pravým tlačítkem myši na existující scénář a zvolte možnost **Upravit kombinaci prohlížečů**.

2. Ve sloupci **typ prohlížeče** klikněte na šipku pro novou položku a vyberte požadovaný typ prohlížeče.

3. Volitelné Upravte ovládací prvek míchání pro určení distribuce testu.

4. Až skončíte s přidáváním prohlížečů, klikněte na **tlačítko OK**.

## <a name="remove-browsers-from-a-scenario"></a>Odebrání prohlížečů ze scénáře

### <a name="to-remove-browsers-from-a-scenario"></a>Odebrání prohlížečů ze scénáře

1. Otevřete zátěžový test.

2. Klikněte pravým tlačítkem na scénář, ze kterého chcete odebrat prohlížeč, a pak zvolte **Upravit kombinaci prohlížečů**.

     Zobrazí se dialogové okno **Upravit kombinaci prohlížečů** .

3. V mřížce vyberte prohlížeč a pak zvolte **Odebrat**.

4. Volitelné Upravte ovládací prvek míchání pro určení distribuce testu.

5. Po dokončení odebírání prohlížečů klikněte na **tlačítko OK**.

## <a name="about-the-mix-control"></a>O ovládacím prvku míchání

Ovládací prvek mix umožňuje upravit procento zatížení, které je distribuováno mezi testy, typy prohlížečů nebo typy sítě ve scénáři zátěžového testu. Procentuální hodnoty upravíte přesunutím jezdců. Úprava kombinace typů prohlížečů určuje pravděpodobnost, že virtuální uživatel spustí určitý typ prohlížeče v rámci scénáře zátěžového testu.

Při přesunutí posuvníku se změní procentuální hodnoty všech dostupných položek. Pokud máte více než dvě položky, je množství, které přidáváte nebo odebíráte, rozděleno rovnoměrně mezi ostatní položky. Toto chování je možné přepsat. Pokud zaškrtnete políčko ve sloupci uzamknout pro konkrétní položku, zamknete pro tuto položku zadanou procentuální hodnotu. Když přesunete posuvník, množství, které přidáte nebo odeberete, se použije jenom u zbývajících odemčených položek.

Tlačítko **rozmístit** se používá k přidělení procentuálních hodnot rovnoměrně mezi všechny položky. Například pokud máte tři položky, volba **distribuovat** nastaví procentuální hodnoty na 34, 33 a 33.

> [!WARNING]
> Tlačítko **distribuovat** přepisuje všechny položky, které jsou zamčené.

Je také možné zadat hodnoty procent přímo do **%** sloupce místo pomocí posuvníků. Pokud zadáte hodnotu v procentech přímo, ostatní položky se automaticky neupraví.

> [!NOTE]
> Když celkový součet nepřidá až 100%, nebo když jsou procentuální hodnoty zadané do sloupce desetinná, jsou posuvníky zakázané **%** .

Když zadáte procentuální hodnoty ručně, měli byste se ujistit, že součet všech položek je 100%. Když uložíte směs, pokud součet není 100%, budete vyzváni, abyste přijali procentuální hodnoty tak, jak jsou, nebo se vrátíte a upravíte. Pokud se rozhodnete je přijmout, bude se poměrně 100%.  Pokud máte například dvě položky a ručně jste je nastavili na 80% a 40%, bude první položka nastavena na 66,67% (80 dělena 120) a druhá položka bude nastavena na 33,33% (40 dělený 120).

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
