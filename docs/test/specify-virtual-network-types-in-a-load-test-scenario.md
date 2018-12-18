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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 586038d325f17d37167166a361ee214d959ba2ab
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894674"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Určení typů virtuálních sítí ve scénáři zátěžového testu

*Kombinace sítí* poskytuje způsob, jak simulovat zatížení více realisticky v případě zkušebního scénáře. Zatížení je generováno pomocí heterogenní kombinace typů sítí místo jednoho jediného typu sítě. Můžete vytvořit užší odhad jak koncoví uživatelé pracují s vašimi aplikacemi.

Určuje pravděpodobnost, že virtuální uživatel spustí kombinaci sítí danou *sítě profilu*. Profil sítě je simulace šířky pásma sítě v aplikační vrstvě. Není to simulovat latence.

Když vytvoříte zátěžový test, můžete simulovat tak, že zatížení je právě generován prostřednictvím více než jeden typ připojení k síti. Mix sítě nabízí několik typů sítí. Jsou simulované různých sítí. Při výběru možnosti, jako `Cable-DSL 1.5Mbps`, čekací dobu jsou vloženy do testů pro simulaci vybrané šířky pásma.

Poměr sítí funguje stejně jako jiné kombinace možností. Typ sítě je vybraný náhodně přidružené s virtuálního uživatele, založené na kombinaci sítí. Tento uživatel testy pomocí určitý typ sítě, podle pravděpodobnosti, kterou jste zadali v kombinaci.

Po zadání kombinace sítě můžete přidávat a odebírat typy sítě. Můžete také změnit rozdělení kombinaci sítí pomocí ovládacího prvku kombinace.

Kombinace řízení umožňuje snadno upravit distribuci sítí ve scénáři.

Další informace najdete v tématu [o ovládacím prvku kombinace](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Skutečná emulace sítě

Visual Studio používá softwarových skutečná emulace sítě pro všechny typy testu včetně zátěžových testů. Skutečná emulace sítě simuluje stavy sítě prostřednictvím přímé manipulace se síťovými pakety. Emulátor skutečné sítě může emulovat chování drátové i bezdrátové sítě pomocí spolehlivého fyzického propojení, jako je Ethernet. Následující atributy sítě jsou začleněny do emulace sítě:

-   Časem přenosu v síti (čekací doba)

-   Množství dostupné šířky pásma

-   Chování řízení front

-   Ztráta paketů

-   Změna pořadí paketů

-   Šíření chyb.

Skutečná emulace sítě také poskytuje flexibilitu při filtrování síťových paketů na základě IP adresy nebo protokoly, například TCP, UDP a ICMP.

Skutečná emulace sítě je možné aplikace založené na síti vývojářům a testerům emulovat požadované zkušební prostředí, hodnotit výkon, odhadnout dopadu změn nebo rozhodovat o optimalizaci technologie. Srovnání s vrstvami testovacího hardwaru je skutečná emulace sítě mnohem levnější a pružnější řešení.

## <a name="to-add-new-networks-to-a-scenario"></a>Přidání nových sítí do scénáře

1.  Během procesu určení kombinace sítě pro scénáře, zvolte **přidat**.

     Nová položka sítě je přidané do mřížky.

    > [!NOTE]
    > Pro zobrazení **upravit kombinaci sítí** dialogového okna, klikněte pravým tlačítkem na existující scénář a pak vyberte **upravit kombinaci sítí**.

2.  V **typ sítě** sloupce, klikněte na šipku pro novou položku. Zvolte typ požadované síti.

3.  (Volitelné) Upravte poměr ovládacího prvku k určení distribuci testů. Další informace najdete v tématu [o ovládacím prvku kombinace](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4.  Po dokončení přidávání sítí, zvolte **OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Chcete-li odebrat sítě ze scénáře

1.  Otevřete zátěžový test.

2.  Klikněte pravým tlačítkem na scénář, ze kterého chcete odebrat síť a zvolte **upravit kombinaci sítí**. **Upravit kombinaci sítí** se zobrazí dialogové okno.

3.  Vyberte síť v mřížce a potom zvolte **odebrat**.

4.  (Volitelné) Upravte poměr ovládacího prvku k určení distribuci testů. Další informace najdete v tématu [o ovládacím prvku kombinace](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5.  Po dokončení odebírání sítí, zvolte **OK**.

## <a name="about-the-mix-control"></a>O ovládacím prvku kombinace

 Ovládací prvek kombinace umožňuje nastavit procento zatížení, která je distribuovaná mezi testy, typu prohlížeče nebo typy sítí ve scénáři testu zatížení. Chcete-li upravit procentní hodnoty, přesuňte posuvníky. Úpravy poměru pro typy sítě určuje pravděpodobnost, že virtuální uživatel spustí konkrétní síťový profil ve scénáři testu zatížení.

 Při přesunutí posuvníku procentuální hodnoty všechny dostupné položky změnit. Pokud máte více než dvě položky, velikost, přidat nebo odebrat rovnoměrně distribuovaných mezi ostatní položky. Je možné toto chování přepsat. Pokud vyberete zaškrtávací políčko ve sloupci zámek pro konkrétní položku, uzamknout specifikované procentuální hodnotou pro danou položku. Pak při přesunutí posuvníku, velikost, přidat nebo odebrat platí jenom pro všechny zbývající položky odemknout.

 **Rozmístit** tlačítko slouží k přidělení procentní hodnoty rovnoměrně mezi všechny položky. Například pokud máte tři položky, výběrem **rozmístit** nastaví procentní hodnoty 34 33 a 33.

> [!WARNING]
> **Rozmístit** tlačítko přepíše všechny položky, které jsou zamknuté.

 Je také možné zadat procentní hodnoty přímo do **%** sloupce namísto použití posuvníků. Pokud zadáte hodnotu v procentech přímo, nebude se automaticky upraví další položky.

> [!NOTE]
> Posuvníky jsou zakázané, pokud celkový počet nepřidá do 100 %, nebo pokud procentní hodnoty zadané do **%** sloupce jsou desetinná čísla.

Když ručně zadáte procentní hodnoty, by měl Ujistěte se, že součet všech položek je 100 %. Při ukládání kombinaci, nejsou-li součet 100 %, vyzve tak, aby přijímal procentuální hodnoty, jak jsou, nebo se vrátit a upravte je tak. Pokud budete chtít nepřijmete, jak jsou, budou se poměrné přepočítání na 100 %.  Pokud máte dvě položky a je ručně nastaveno na 80 % až 40 %, nastaví se první položka % 66.67 (80 dělený 120) a nastaví se druhá položka % 33,33 (40 dělený 120).