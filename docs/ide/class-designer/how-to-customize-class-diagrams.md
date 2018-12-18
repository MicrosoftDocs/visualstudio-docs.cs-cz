---
title: 'Postupy: Přizpůsobení diagramů tříd (návrhář tříd)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4546324a5789c408c22ac610d7a878ad990af2a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913212"
---
# <a name="how-to-customize-class-diagrams"></a>Postupy: přizpůsobení diagramů tříd

Můžete změnit způsob, jak diagramy tříd zobrazují informace. Můžete přizpůsobit celý diagram nebo jednotlivé typy na ploše návrhu.

Můžete například upravit úroveň zvětšení celého diagramu tříd, změnit způsob seskupování a řazení jednotlivých členů typu, skrýt nebo zobrazit vztahy a přesunout jednotlivé typy nebo množiny typů kamkoli v diagramu.

> [!NOTE]
> Upravením způsobu, jakým se tvary v diagramu zobrazují, nezměníte základní kód pro typy znázorněné v diagramu.

Oddíly, které obsahují členy, typu, jako **vlastnosti** části ve třídě, se nazývají oddíly. Jednotlivé oddíly a členy typu můžete skrýt nebo zobrazit.

## <a name="zoom-in-and-out-of-the-class-diagram"></a>Přiblížení a oddálení diagramu tříd

1. Otevřete a vyberte soubor diagramu tříd v **návrhář tříd**.

2. Na **návrhář tříd** nástrojů, klikněte na tlačítko **přiblížit** nebo **Oddálit** tlačítko a změňte úroveň přiblížení návrhové ploše.

     or

     Zadejte hodnotu přiblížení. Můžete použít **přiblížení** rozevíracím seznamu nebo zadejte platnou úroveň přiblížení (platný rozsah je od 10 do 400 %).

    > [!NOTE]
    > Změna úrovně přiblížení neovlivní měřítko výtisku vašeho diagramu tříd.

## <a name="customize-grouping-and-sorting-of-type-members"></a>Přizpůsobení seskupování a řazení členů typu

1. Otevřete a vyberte soubor diagramu tříd v **návrhář tříd**.

2. Klikněte pravým tlačítkem na prázdnou oblast na návrhové ploše a přejděte na **členy skupiny**.

3. Vyberte jednu z dostupných možností:

    - **Seskupit podle druhu** odděluje jednotlivé členy typu do seskupeného seznamu vlastností, metod, událostí a polí. Jednotlivé skupiny závisí na definici entit: třída například nebude zobrazovat žádnou skupinu událostí, pokud pro danou třídu zatím nebyly definovány žádné události.

    - **Seskupit podle přístupu ke** modifikátorů přístupu odděluje jednotlivé členy typu do seskupeného seznamu na základě tohoto členu. Například veřejné a soukromé.

    - **Seřadit podle abecedy** zobrazuje položky, které tvoří entitu, jako jeden abecední seznam. Seznam je seřazen vzestupně.

## <a name="hide-compartments-on-a-type"></a>Skrytí oddílů typu

1. Otevřete a vyberte soubor diagramu tříd v **návrhář tříd**.

2. Klikněte pravým tlačítkem myši klikněte na kategorii členu v typu, který chcete přizpůsobit (například, vyberte **metody** uzlu ve třídě.

3. Klikněte na tlačítko **skrýt oddíl**.

     Vybraný oddíl zmizí z kontejneru typu.

## <a name="hide-individual-members-on-a-type"></a>Skrytí jednotlivých členů typu

1. Otevřete a vyberte soubor diagramu tříd v **návrhář tříd**.

2. Klikněte pravým tlačítkem myši na člen v typu, který chcete skrýt.

3. Klikněte na tlačítko **skrýt**.

     Vybraný člen zmizí z kontejneru typu.

## <a name="show-hidden-compartments-and-members-on-a-type"></a>Zobrazení skrytých oddílů a členů typu

1. Otevřete a vyberte soubor diagramu tříd v **návrhář tříd**.

2. Klikněte pravým tlačítkem na název typu se skrytým oddílem.

3. Klikněte na tlačítko **zobrazit všechny členy**.

     Všechny skryté oddíly a členy se zobrazí v kontejneru typu.

## <a name="hide-relationships"></a>Skrytí vztahů

1. Otevřete a vyberte soubor diagramu tříd v **návrhář tříd**.

2. Klikněte pravým tlačítkem myši na asociační čáru nebo čáru dědičnosti, kterou chcete skrýt.

3. Klikněte na tlačítko **skrýt** pro Asociační čáry a klikněte na **Skrýt čáru dědičnosti** u čar dědičnosti.

4. Klikněte na tlačítko **zobrazit všechny členy**.

     Všechny skryté oddíly a členy se zobrazí v kontejneru typu.

## <a name="show-hidden-relationships"></a>Zobrazení skrytých vztahů

1. Otevřete a vyberte soubor diagramu tříd v **návrhář tříd**.

2. Klikněte pravým tlačítkem na typ se skrytým přidružením nebo dědičností.

   Klikněte na tlačítko **zobrazit všechny členy** pro Asociační čáry a klikněte na **zobrazit základní třídu** nebo **Zobrazit odvozené třídy** u čar dědičnosti.

## <a name="remove-a-shape-from-a-class-diagram"></a>Odebrání tvaru z diagramu tříd
Můžete odebrat tvar typu z diagramu tříd bez ovlivnění základního kódu typu. Odebrání tvarů typu z diagramu tříd ovlivní pouze tento diagram: základní kód definující typ a ostatní diagramy, které typ zobrazují, ovlivněny nejsou.

1. V diagramu tříd vyberte tvar typu, který chcete z diagramu odebrat.

2. Na **upravit** nabídce zvolte **odebrat z diagramu**.

     Tvar typu a čáry přidružení nebo dědičnosti spojené s tvarem se již v diagramu nezobrazí.

## <a name="delete-a-type-shape-and-its-underlying-code"></a>Odstranění tvaru typu a jeho základního kódu

1. Klikněte pravým tlačítkem myši na tvar na návrhové ploše.

2. Vyberte **smazat kód** v místní nabídce.

     Tvar je odstraněn z diagramu a jeho základní kód je odstraněn z projektu.

## <a name="see-also"></a>Viz také:

- [Práce s diagramy tříd](working-with-class-diagrams.md)
- [Postupy: změna mezi zápisem člena a zápisem asociace](how-to-change-between-member-notation-and-association-notation.md)
- [Postupy: zobrazení existujících typů](how-to-view-existing-types.md)
- [Zobrazování typů a vztahů](viewing-types-and-relationships.md)