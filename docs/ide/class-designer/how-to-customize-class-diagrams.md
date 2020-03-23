---
title: 'Postupy: Přizpůsobení diagramů tříd (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4c55204983f9e7a546867621ec21070c8d69645
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590160"
---
# <a name="how-to-customize-class-diagrams"></a>Postup: Přizpůsobení diagramů tříd

Můžete změnit způsob, jak diagramy tříd zobrazují informace. Můžete přizpůsobit celý diagram nebo jednotlivé typy na ploše návrhu.

Můžete například upravit úroveň zvětšení celého diagramu tříd, změnit způsob seskupování a řazení jednotlivých členů typu, skrýt nebo zobrazit vztahy a přesunout jednotlivé typy nebo množiny typů kamkoli v diagramu.

> [!NOTE]
> Upravením způsobu, jakým se tvary v diagramu zobrazují, nezměníte základní kód pro typy znázorněné v diagramu.

Oddíly, které obsahují členy typu, například **vlastnosti** oddílu ve třídě, se nazývají oddíly. Jednotlivé oddíly a členy typu můžete skrýt nebo zobrazit.

## <a name="zoom-in-and-out-of-the-class-diagram"></a>Přiblížení a oddálení diagramu tříd

1. Otevřete a vyberte soubor diagramu třídy v **Návrháři tříd**.

2. Na panelu nástrojů **Návrhář eniciála tříd** můžete klepnutím na tlačítko **Přiblížit** nebo **Oddálit** změnit úroveň přiblížení povrchu návrháře.

     – nebo –

     Zadejte hodnotu přiblížení. Můžete použít rozevírací seznam **Lupa** nebo zadat platnou úroveň přiblížení (platný rozsah je mezi 10 % a 400 %).

    > [!NOTE]
    > Změna úrovně přiblížení neovlivní měřítko výtisku vašeho diagramu tříd.

## <a name="customize-grouping-and-sorting-of-type-members"></a>Přizpůsobení seskupování a řazení členů typu

1. Otevřete a vyberte soubor diagramu třídy v **Návrháři tříd**.

2. Klepněte pravým tlačítkem myši na prázdnou oblast na návrhové ploše a přejděte na **položku Členové skupiny**.

3. Vyberte jednu z dostupných možností:

    - **Skupina podle druhu** odděluje jednotlivé členy typu do seskupeného seznamu vlastností, metod, událostí a polí. Jednotlivé skupiny závisí na definici entit: třída například nebude zobrazovat žádnou skupinu událostí, pokud pro danou třídu zatím nebyly definovány žádné události.

    - **Skupina podle aplikace Access** odděluje jednotlivé členy typu do seskupeného seznamu na základě modifikátorů přístupu člena. Například veřejné a soukromé.

    - **Seřadit abecedně** zobrazí položky, které tvoří entitu jako jeden abecední seznam. Seznam je seřazen vzestupně.

## <a name="hide-compartments-on-a-type"></a>Skrytí oddílů typu

1. Otevřete a vyberte soubor diagramu třídy v **Návrháři tříd**.

2. Klikněte pravým tlačítkem myši na kategorii členů typu, který chcete přizpůsobit (například vyberte uzel **Metody** ve třídě.

3. Klepněte na **skrýt přihrádku**.

     Vybraný oddíl zmizí z kontejneru typu.

## <a name="hide-individual-members-on-a-type"></a>Skrytí jednotlivých členů typu

1. Otevřete a vyberte soubor diagramu třídy v **Návrháři tříd**.

2. Klikněte pravým tlačítkem myši na člen v typu, který chcete skrýt.

3. Klepněte na **tlačítko Skrýt**.

     Vybraný člen zmizí z kontejneru typu.

## <a name="show-hidden-compartments-and-members-on-a-type"></a>Zobrazení skrytých oddílů a členů typu

1. Otevřete a vyberte soubor diagramu třídy v **Návrháři tříd**.

2. Klikněte pravým tlačítkem na název typu se skrytým oddílem.

3. Klepněte na tlačítko **Zobrazit všechny členy**.

     Všechny skryté oddíly a členy se zobrazí v kontejneru typu.

## <a name="hide-relationships"></a>Skrytí vztahů

1. Otevřete a vyberte soubor diagramu třídy v **Návrháři tříd**.

2. Klikněte pravým tlačítkem myši na asociační čáru nebo čáru dědičnosti, kterou chcete skrýt.

3. Klikněte na **Skrýt** pro asociační řádky a na **skrýt řádek dědičnosti** pro řádky dědičnosti.

4. Klepněte na tlačítko **Zobrazit všechny členy**.

     Všechny skryté oddíly a členy se zobrazí v kontejneru typu.

## <a name="show-hidden-relationships"></a>Zobrazení skrytých vztahů

1. Otevřete a vyberte soubor diagramu třídy v **Návrháři tříd**.

2. Klikněte pravým tlačítkem na typ se skrytým přidružením nebo dědičností.

   Klikněte na **Zobrazit všechny členy** pro řádky přidružení a klikněte na Zobrazit základní **třídu** nebo **Zobrazit odvozené třídy** pro řádky dědičnosti.

## <a name="remove-a-shape-from-a-class-diagram"></a>Odebrání tvaru z diagramu tříd
Můžete odebrat tvar typu z diagramu tříd bez ovlivnění základního kódu typu. Odebrání tvarů typu z diagramu tříd ovlivní pouze tento diagram: základní kód definující typ a ostatní diagramy, které typ zobrazují, ovlivněny nejsou.

1. V diagramu tříd vyberte tvar typu, který chcete z diagramu odebrat.

2. V nabídce **Úpravy** zvolte **Odebrat z diagramu**.

     Tvar typu a čáry přidružení nebo dědičnosti spojené s tvarem se již v diagramu nezobrazí.

## <a name="delete-a-type-shape-and-its-underlying-code"></a>Odstranění tvaru typu a jeho základního kódu

1. Klikněte pravým tlačítkem myši na tvar na návrhové ploše.

2. V místní nabídce vyberte **Odstranit kód.**

     Tvar je odstraněn z diagramu a jeho základní kód je odstraněn z projektu.

## <a name="see-also"></a>Viz také

- [Postup: Změna mezi zápisem členů a zápisem přidružení](how-to-change-between-member-notation-and-association-notation.md)
- [Postup: Zobrazení existujících typů](how-to-view-existing-types.md)
- [Zobrazování typů a vztahů](designing-and-viewing-classes-and-types.md)
