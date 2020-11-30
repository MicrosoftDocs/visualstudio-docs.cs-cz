---
title: Určení typů virtuálních sítí (zátěžové testování)
description: Naučte se používat kombinaci sítí k vytvoření užšího odhadu toho, jak koncoví uživatelé pracují s vašimi aplikacemi.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: 94973f8f791158f408b841442478dcfa6aeeff58
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330209"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Určení typů virtuálních sítí ve scénáři zátěžového testu

*Kombinace sítě* poskytuje způsob, jak simulovat zatížení ve scénáři zátěžového testu. Zatížení je generováno pomocí heterogenní kombinace typů sítě namísto jednoho typu jednoduché sítě. Vytvoříte blíže přibližné informace o tom, jak koncoví uživatelé pracují s vašimi aplikacemi.

Kombinace sítě určuje pravděpodobnost, že virtuální uživatel spustí daný *profil sítě*. Profil sítě je simulací šířky pásma sítě v aplikační vrstvě. Latence nesimuluje.

Když vytvoříte zátěžový test, může být vhodné simulovat toto zatížení prostřednictvím více než jednoho typu síťového připojení. Kombinace sítě nabízí několik typů sítě. Různé sítě jsou simulované. Zvolíte-li možnost `Cable-DSL 1.5Mbps` , například, časy čekání jsou vloženy do testu, aby se simulovala vybraná šířka pásma.

Kombinace sítě funguje podobně jako další možnosti kombinace. Typ sítě je náhodně přidružen k virtuálnímu uživateli na základě kombinace sítí. Testy tohoto uživatele se spouští pomocí konkrétního typu sítě, a to na základě pravděpodobnosti, kterou jste zadali v kombinaci.

Po zadání kombinace sítě můžete přidat nebo odebrat typy sítě. Můžete také změnit distribuci kombinace sítě pomocí ovládacího prvku míchání.

Ovládací prvek míchání umožňuje snadno upravit distribuci sítí ve scénáři.

Další informace naleznete v tématu [o ovládacím prvku míchání](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Skutečná emulace sítě

Visual Studio používá skutečnou emulaci sítě založenou na softwaru pro všechny typy testů včetně zátěžových testů. Skutečná emulace sítě simuluje stavy sítě pomocí přímé manipulace se síťovými pakety. Skutečný emulátor sítě může emulovat chování drátové i bezdrátové sítě pomocí spolehlivého fyzického propojení, jako je Ethernet. Následující atributy sítě jsou začleněny do skutečné emulace sítě:

- Doba odezvy v síti (latence)

- Množství dostupné šířky pásma

- Chování fronty

- Ztráta paketů

- Změna pořadí paketů

- Šíření chyb.

Skutečná emulace sítě také poskytuje flexibilitu při filtrování síťových paketů na základě IP adres nebo protokolů, jako jsou TCP, UDP a ICMP.

Skutečná emulace sítě může používat vývojáři a testeri síťových aplikací k emulaci požadovaného testovacího prostředí, vyhodnocení výkonu, předpovědi dopadu změny nebo rozhodování o optimalizaci technologie. Ve srovnání s vrstvami testovacího hardwaru je skutečná emulace sítě mnohem levnější a pružnější řešení.

## <a name="to-add-new-networks-to-a-scenario"></a>Přidání nových sítí do scénáře

1. Během procesu zadávání kombinace sítě pro určitý scénář vyberte možnost **Přidat**.

     Do mřížky se přidá nová položka sítě.

    > [!NOTE]
    > Chcete-li zobrazit dialogové okno **Upravit kombinaci sítí** , klikněte pravým tlačítkem myši na existující scénář a zvolte možnost **Upravit kombinaci sítí**.

2. Ve sloupci **typ sítě** vyberte šipku pro novou položku. Vyberte požadovaný typ sítě.

3. Volitelné Upravte ovládací prvek míchání pro určení distribuce testu. Další informace naleznete v tématu [o ovládacím prvku míchání](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Až skončíte s přidáváním sítí, klikněte na **tlačítko OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Odebrání sítí ze scénáře

1. Otevřete zátěžový test.

2. Klikněte pravým tlačítkem na scénář, ze kterého chcete odebrat síť, a vyberte **Upravit kombinaci sítí**. Zobrazí se dialogové okno **Upravit kombinaci sítí** .

3. Vyberte síť v mřížce a pak zvolte **Odebrat**.

4. Volitelné Upravte ovládací prvek míchání pro určení distribuce testu. Další informace naleznete v tématu [o ovládacím prvku míchání](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Po dokončení odebírání sítí klikněte na **tlačítko OK**.

## <a name="about-the-mix-control"></a>O ovládacím prvku míchání

Ovládací prvek míchání umožňuje upravit procento zatížení distribuované mezi testy, typy prohlížečů nebo typy sítě ve scénáři zátěžového testu. Chcete-li upravit procentuální hodnoty, přesuňte posuvníky. Nastavení kombinace pro typy sítě určuje pravděpodobnost, že virtuální uživatel spustí konkrétní profil sítě ve scénáři zátěžového testu.

Při přesunutí posuvníku se změní procentuální hodnoty všech dostupných položek. Pokud máte více než dvě položky, je množství, které přidáváte nebo odebíráte, rozděleno rovnoměrně mezi ostatní položky. Toto chování je možné přepsat. Pokud zaškrtnete políčko ve sloupci uzamknout pro konkrétní položku, zamknete pro tuto položku zadanou procentuální hodnotu. Když přesunete posuvník, množství, které přidáte nebo odeberete, se použije jenom u zbývajících odemčených položek.

Tlačítko **rozmístit** se používá k přidělení procentuálních hodnot rovnoměrně mezi všechny položky. Například pokud máte tři položky, volba **distribuovat** nastaví procentuální hodnoty na 34, 33 a 33.

> [!WARNING]
> Tlačítko **distribuovat** přepisuje všechny položky, které jsou zamčené.

Je také možné zadat hodnoty procent přímo do **%** sloupce místo pomocí posuvníků. Pokud zadáte hodnotu v procentech přímo, ostatní položky se automaticky neupraví.

> [!NOTE]
> Když celkový součet nepřidá až 100%, nebo když jsou procentuální hodnoty zadané do sloupce desetinná, jsou posuvníky zakázané **%** .

Když zadáte procentuální hodnoty ručně, měli byste se ujistit, že součet všech položek je 100%. Když uložíte směs, pokud součet není 100%, budete vyzváni, abyste přijali procentuální hodnoty tak, jak jsou, nebo se vrátíte a upravíte. Pokud se rozhodnete je přijmout, bude se poměrně 100%.  Pokud máte například dvě položky a ručně jste je nastavili na 80% a 40%, bude první položka nastavena na 66,67% (80 dělena 120) a druhá položka bude nastavena na 33,33% (40 dělený 120).
