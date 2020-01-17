---
title: Určení typů virtuálních sítí ve scénáři zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, adding networks
- load tests, removing networks
- load tests, virtual networks
- network mix
ms.assetid: 3c4f7874-081a-4ec4-9510-4d6d7d863a11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60fa2bd38f3d7e594e9af7ba8ec544518bdbb920
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115295"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Určení typů virtuálních sítí ve scénáři zátěžového testu

*Kombinace sítě* poskytuje způsob, jak simulovat zatížení ve scénáři zátěžového testu. Zatížení je generováno pomocí heterogenní kombinace typů sítě namísto jednoho typu jednoduché sítě. Vytvoříte blíže přibližné informace o tom, jak koncoví uživatelé pracují s vašimi aplikacemi.

Kombinace sítě určuje pravděpodobnost, že virtuální uživatel spustí daný *profil sítě*. Profil sítě je simulací šířky pásma sítě v aplikační vrstvě. Latence nesimuluje.

Když vytvoříte zátěžový test, může být vhodné simulovat toto zatížení prostřednictvím více než jednoho typu síťového připojení. Kombinace sítě nabízí několik typů sítě. Různé sítě jsou simulované. Když zvolíte možnost, například `Cable-DSL 1.5Mbps`, budou do testu vloženy časy čekání, aby se simulovala vybraná šířka pásma.

Kombinace sítě funguje podobně jako další možnosti kombinace. Typ sítě je náhodně přidružen k virtuálnímu uživateli na základě kombinace sítí. Testy tohoto uživatele se spouští pomocí konkrétního typu sítě, a to na základě pravděpodobnosti, kterou jste zadali v kombinaci.

Po zadání kombinace sítě můžete přidat nebo odebrat typy sítě. Můžete také změnit distribuci kombinace sítě pomocí ovládacího prvku míchání.

Ovládací prvek míchání umožňuje snadno upravit distribuci sítí ve scénáři.

Další informace najdete v tématu [o ovládacím prvku kombinace](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Skutečná emulace sítě

Visual Studio používá skutečnou emulaci sítě založenou na softwaru pro všechny typy testů včetně zátěžových testů. Skutečná emulace sítě simuluje stavy sítě prostřednictvím přímé manipulace se síťovými pakety. Emulátor skutečné sítě může emulovat chování drátové i bezdrátové sítě pomocí spolehlivého fyzického propojení, jako je Ethernet. Následující atributy sítě jsou začleněny do emulace sítě:

- Doba odezvy v síti (latence)

- Množství dostupné šířky pásma

- Chování řízení front

- Ztráta paketů

- Změna pořadí paketů

- Šíření chyb.

Skutečná emulace sítě také poskytuje flexibilitu při filtrování síťových paketů na základě IP adresy nebo protokoly, například TCP, UDP a ICMP.

Skutečná emulace sítě může používat vývojáři a testeri síťových aplikací k emulaci požadovaného testovacího prostředí, vyhodnocení výkonu, předpovědi dopadu změny nebo rozhodování o optimalizaci technologie. Srovnání s vrstvami testovacího hardwaru je skutečná emulace sítě mnohem levnější a pružnější řešení.

## <a name="to-add-new-networks-to-a-scenario"></a>Přidání nových sítí do scénáře

1. Během procesu zadávání kombinace sítě pro určitý scénář vyberte možnost **Přidat**.

     Do mřížky se přidá nová položka sítě.

    > [!NOTE]
    > Chcete-li zobrazit dialogové okno **Upravit kombinaci sítí** , klikněte pravým tlačítkem myši na existující scénář a zvolte možnost **Upravit kombinaci sítí**.

2. Ve sloupci **typ sítě** vyberte šipku pro novou položku. Vyberte požadovaný typ sítě.

3. (Volitelné) Upravte poměr ovládacího prvku k určení distribuci testů. Další informace najdete v tématu [o ovládacím prvku kombinace](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Až skončíte s přidáváním sítí, klikněte na **tlačítko OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Odebrání sítí ze scénáře

1. Otevřete zátěžový test.

2. Klikněte pravým tlačítkem na scénář, ze kterého chcete odebrat síť, a vyberte **Upravit kombinaci sítí**. Zobrazí se dialogové okno **Upravit kombinaci sítí** .

3. Vyberte síť v mřížce a pak zvolte **Odebrat**.

4. (Volitelné) Upravte poměr ovládacího prvku k určení distribuci testů. Další informace najdete v tématu [o ovládacím prvku kombinace](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Po dokončení odebírání sítí klikněte na **tlačítko OK**.

## <a name="about-the-mix-control"></a>O ovládacím prvku kombinace

Ovládací prvek míchání umožňuje upravit procento zatížení distribuované mezi testy, typy prohlížečů nebo typy sítě ve scénáři zátěžového testu. Chcete-li upravit procentuální hodnoty, přesuňte posuvníky. Nastavení kombinace pro typy sítě určuje pravděpodobnost, že virtuální uživatel spustí konkrétní profil sítě ve scénáři zátěžového testu.

Při přesunutí posuvníku procentuální hodnoty všechny dostupné položky změnit. Pokud máte více než dvě položky, velikost, přidat nebo odebrat rovnoměrně distribuovaných mezi ostatní položky. Je možné toto chování přepsat. Pokud vyberete zaškrtávací políčko ve sloupci zámek pro konkrétní položku, uzamknout specifikované procentuální hodnotou pro danou položku. Pak při přesunutí posuvníku, velikost, přidat nebo odebrat platí jenom pro všechny zbývající položky odemknout.

**Rozmístit** tlačítko slouží k přidělení procentní hodnoty rovnoměrně mezi všechny položky. Například pokud máte tři položky, výběrem **rozmístit** nastaví procentní hodnoty 34 33 a 33.

> [!WARNING]
> **Rozmístit** tlačítko přepíše všechny položky, které jsou zamknuté.

Je také možné zadat procentní hodnoty přímo do **%** sloupce namísto použití posuvníků. Pokud zadáte hodnotu v procentech přímo, nebude se automaticky upraví další položky.

> [!NOTE]
> Posuvníky jsou zakázané, pokud celkový počet nepřidá do 100 %, nebo pokud procentní hodnoty zadané do **%** sloupce jsou desetinná čísla.

Když ručně zadáte procentní hodnoty, by měl Ujistěte se, že součet všech položek je 100 %. Když uložíte směs, pokud součet není 100%, budete vyzváni, abyste přijali procentuální hodnoty tak, jak jsou, nebo se vrátíte a upravíte. Pokud budete chtít nepřijmete, jak jsou, budou se poměrné přepočítání na 100 %.  Pokud máte dvě položky a je ručně nastaveno na 80 % až 40 %, nastaví se první položka % 66.67 (80 dělený 120) a nastaví se druhá položka % 33,33 (40 dělený 120).
