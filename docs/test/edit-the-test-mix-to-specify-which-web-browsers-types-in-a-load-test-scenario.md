---
title: Kombinace testů prohlížeče pro zátěžové testování
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114531"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Úprava kombinace testů a určení typů webových prohlížečů ve scénáři zátěžového testu

*Mix prohlížeče* poskytuje způsob, jak simulovat zatížení realističtější ve scénáři zátěžového testu. Zatížení je generováno pomocí heterogenní kombinace webových prohlížečů namísto jednoho webového prohlížeče. Můžete vytvořit bližší aproximaci webových prohlížečů, které budou použity s vašimi aplikacemi.

Mix prohlížeče určuje pravděpodobnost, že virtuální uživatel spouštějící určitý typ webového prohlížeče ve scénáři zátěžového testu. Při vytváření zátěžového testu můžete simulovat, že zatížení je generováno prostřednictvím více než jednoho webového prohlížeče. Přidáte-li typ webového prohlížeče do kombinace ze sady webových prohlížečů, které jsou k dispozici, je sada přidružených záhlaví pro vybraný webový prohlížeč přidána ke každému požadavku HTTP odeslaného testem výkonu webu.

Prohlížeč mix funguje stejně jako ostatní možnosti mixu. Typ webového prohlížeče je náhodně spojen s virtuálním uživatelem na základě kombinace prohlížeče. Testy tohoto uživatele jsou spuštěny v určitém webovém prohlížeči na základě pravděpodobnosti, kterou jste zadali v mixu.

Poté, co jste zadali kombinaci prohlížeče, můžete později přidat a odebrat typy webových prohlížečů do mixu. Můžete také změnit distribuci mix prohlížeče pomocí ovládacího prvku mix. Ovládací prvek mix umožňuje snadno upravit distribuci prohlížečů ve scénáři.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Přidání nových prohlížečů do scénáře

### <a name="to-add-new-browsers-to-a-scenario"></a>Přidání nových prohlížečů do scénáře

1. Zatímco v procesu zadávání prohlížeče mix pro scénář zvolte **Přidat**.

     Do mřížky je přidána nová položka prohlížeče.

    > [!NOTE]
    > Chcete-li zobrazit dialogové okno **Upravit kombinaci prohlížeče,** klepněte pravým tlačítkem myši na existující scénář a pak zvolte **Upravit kombinaci prohlížeče**.

2. Ve sloupci **Typ prohlížeče** zvolte šipku pro novou položku a zvolte požadovaný typ prohlížeče.

3. (Nepovinné) Nastavte ovládací prvek mix udáváte rozložení testu.

4. Po přidání prohlížečů zvolte **OK**.

## <a name="remove-browsers-from-a-scenario"></a>Odebrání prohlížečů ze scénáře

### <a name="to-remove-browsers-from-a-scenario"></a>Odebrání prohlížečů ze scénáře

1. Otevřete zátěžový test.

2. Klikněte pravým tlačítkem myši na scénář, ze kterého chcete odebrat prohlížeč, a pak zvolte **Upravit kombinaci prohlížeče**.

     Zobrazí se dialogové okno **Upravit kombinaci prohlížeče.**

3. Vyberte prohlížeč v mřížce a pak zvolte **Odebrat**.

4. (Nepovinné) Nastavte ovládací prvek mix udáváte rozložení testu.

5. Po dokončení odebírání prohlížečů zvolte **OK**.

## <a name="about-the-mix-control"></a>O ovládacím prvku mix

Ovládací prvek mix umožňuje upravit procento zatížení, které je distribuováno mezi testy, typy prohlížečů nebo typy sítí ve scénáři zátěžového testu. Procentuální hodnoty můžete upravit posunutím jezdců. Úprava kombinace pro typy prohlížečů určuje pravděpodobnost, že virtuální uživatel spouštějící určitý typ prohlížeče ve scénáři zátěžového testu.

Když posunete jezdec, změní se procentuální hodnoty všech dostupných položek. Pokud máte více než dvě položky, částka, kterou přidáte nebo odeberete, je rovnoměrně rozdělena mezi ostatní položky. Je možné přepsat toto chování. Pokud zaškrtnete políčko ve sloupci zámku pro určitou položku, uzamknete zadanou hodnotu procenta pro tuto položku. Když potom posunete jezdec, částka, kterou přidáte nebo odeberete, se použije pouze na všechny zbývající odemčené položky.

Tlačítko **Distribuovat** se používá k rozdělení procentuálních hodnot rovnoměrně mezi všechny položky. Pokud máte například tři položky, zvolte **Rozmístění,** nastaví tecesní hodnoty na 34, 33 a 33.

> [!WARNING]
> Tlačítko **Rozmístit** přepíše všechny položky, které jsou zamknuté.

Je také možné zadat procentuální **%** hodnoty přímo do sloupce namísto použití posuvníků. Pokud zadáte procentuální hodnotu přímo, ostatní položky se automaticky neupraví.

> [!NOTE]
> Posuvníky jsou zakázány, pokud součet nepřidá až 100 %, nebo pokud jsou procentuální hodnoty zadané do **%** sloupce desetinné čárky.

Při ručním zadávání procentuálních hodnot byste se měli ujistit, že součet všech položek je 100 %. Pokud při uložení směsi neobdržíte součet 100 %, budete vyzváni k přijetí procentuálních hodnot tak, jak jsou, nebo k jejich vrácení a úpravě. Pokud se rozhodnete je přijmout tak, jak jsou, budou poměrně 100%.  Pokud například máte dvě položky a ručně je nastavíte na 80 % a 40 %, bude první položka nastavena na 66,67 % (80 děleno 120) a druhá položka bude nastavena na 33,33 % (40 vydělených 120).

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
