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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115295"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Určení typů virtuálních sítí ve scénáři zátěžového testu

*Kombinace sítí* umožňuje simulovat zatížení realističtější ve scénáři zátěžového testu. Zatížení je generováno pomocí heterogenní kombinace typů sítí namísto jednoho typu sítě. Můžete vytvořit bližší aproximaci toho, jak koncoví uživatelé interagují s vašimi aplikacemi.

Kombinace sítí určuje pravděpodobnost, že virtuální uživatel se systémem daného *síťového profilu*. Profil sítě je simulace šířky pásma sítě v aplikační vrstvě. Nesimuluje latenci.

Při vytváření zátěžového testu můžete simulovat, že zatížení je generováno prostřednictvím více než jednoho typu síťového připojení. Síťový mix nabízí několik typů sítí. Různé sítě jsou simulovány. Pokud zvolíte možnost, `Cable-DSL 1.5Mbps`jako je například , čekací doby jsou vloženy do testu simulovat vybrané šířky pásma.

Síťový mix funguje stejně jako ostatní možnosti mixu. Typ sítě je vybrán náhodně přidružený k virtuálnímu uživateli na základě kombinace sítí. Testy tohoto uživatele jsou spouštěny pomocí určitého typu sítě na základě pravděpodobnosti zadané v kombinaci.

Po zadání kombinace sítí můžete přidat a odebrat typy sítí. Můžete také změnit distribuci síťového mixu pomocí ovládacího prvku mix.

Ovládací prvek mix umožňuje snadno upravit distribuci sítí ve scénáři.

Další informace naleznete [v tématu O ovládacím prvku mix](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Skutečná síťová emulace

Visual Studio používá softwarovou skutečnou síťovou emulaci pro všechny typy testů, včetně zátěžových testů. Skutečná emulace sítě simuluje síťové podmínky přímou manipulací se síťovými pakety. Skutečný emulátor sítě může emulovat chování kabelových i bezdrátových sítí pomocí spolehlivého fyzického propojení, například sítě Ethernet. Následující síťové atributy jsou začleněny do skutečné emulace sítě:

- Doba odezvy v síti (latence)

- Velikost dostupné šířky pásma

- Chování při řazení do fronty

- Ztráta paketů

- Změna pořadí paketů

- Šíření chyb.

Skutečná síťová emulace také poskytuje flexibilitu při filtrování síťových paketů na základě adres IP nebo protokolů, jako jsou TCP, UDP a ICMP.

Skutečná síťová emulace může být použita síťovými vývojáři aplikací a testery k emulaci požadovaného testovacího prostředí, posouzení výkonu, předvídání dopadu změn nebo rozhodování o optimalizaci technologií. Ve srovnání s hardwarovými testovacími lůžky je skutečná emulace sítě mnohem levnějším a flexibilnějším řešením.

## <a name="to-add-new-networks-to-a-scenario"></a>Přidání nových sítí do scénáře

1. Během procesu zadávání kombinace sítí pro scénář zvolte **Přidat**.

     Do sítě je přidána nová položka sítě.

    > [!NOTE]
    > Chcete-li zobrazit dialogové okno **Upravit kombinaci sítě,** klepněte pravým tlačítkem myši na existující scénář a pak zvolte **Upravit kombinaci sítě**.

2. Ve sloupci **Typ sítě** zvolte šipku pro novou položku. Zvolte požadovaný typ sítě.

3. (Nepovinné) Nastavte ovládací prvek mix udáváte rozložení testu. Další informace naleznete [v tématu O ovládacím prvku mix](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Po přidání sítí zvolte **OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Odebrání sítí ze scénáře

1. Otevřete zátěžový test.

2. Klepněte pravým tlačítkem myši na scénář, ze kterého chcete odebrat síť, a zvolte **Upravit kombinaci sítě**. Zobrazí se dialogové okno **Upravit síťový mix.**

3. Vyberte síť v mřížce a pak zvolte **Odebrat**.

4. (Nepovinné) Nastavte ovládací prvek mix udáváte rozložení testu. Další informace naleznete [v tématu O ovládacím prvku mix](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Po dokončení odebírání sítí zvolte **OK**.

## <a name="about-the-mix-control"></a>O ovládacím prvku mix

Ovládací prvek mix umožňuje upravit procento zatížení, které je distribuováno mezi testy, typy prohlížečů nebo typy sítí ve scénáři zátěžového testu. Chcete-li upravit procentuální hodnoty, přesuňte posuvníky. Úprava kombinace pro typy sítí určuje pravděpodobnost, že virtuální uživatel spouštějící určitý síťový profil ve scénáři zátěžového testu.

Když posunete jezdec, změní se procentuální hodnoty všech dostupných položek. Pokud máte více než dvě položky, částka, kterou přidáte nebo odeberete, je rovnoměrně rozdělena mezi ostatní položky. Je možné přepsat toto chování. Pokud zaškrtnete políčko ve sloupci zámku pro určitou položku, uzamknete zadanou hodnotu procenta pro tuto položku. Když potom posunete jezdec, částka, kterou přidáte nebo odeberete, se použije pouze na všechny zbývající odemčené položky.

Tlačítko **Distribuovat** se používá k rozdělení procentuálních hodnot rovnoměrně mezi všechny položky. Pokud máte například tři položky, zvolte **Rozmístění,** nastaví tecesní hodnoty na 34, 33 a 33.

> [!WARNING]
> Tlačítko **Rozmístit** přepíše všechny položky, které jsou zamknuté.

Je také možné zadat procentuální **%** hodnoty přímo do sloupce namísto použití posuvníků. Pokud zadáte procentuální hodnotu přímo, ostatní položky se automaticky neupraví.

> [!NOTE]
> Posuvníky jsou zakázány, pokud součet nepřidá až 100 %, nebo pokud jsou procentuální hodnoty zadané do **%** sloupce desetinné čárky.

Při ručním zadávání procentuálních hodnot byste se měli ujistit, že součet všech položek je 100 %. Pokud při uložení směsi neobdržíte součet 100 %, budete vyzváni k přijetí procentuálních hodnot tak, jak jsou, nebo k jejich vrácení a úpravě. Pokud se rozhodnete je přijmout tak, jak jsou, budou poměrně 100%.  Pokud například máte dvě položky a ručně je nastavíte na 80 % a 40 %, bude první položka nastavena na 66,67 % (80 děleno 120) a druhá položka bude nastavena na 33,33 % (40 vydělených 120).
