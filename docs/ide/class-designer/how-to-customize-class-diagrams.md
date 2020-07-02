---
title: 'Postupy: Přizpůsobení diagramů tříd (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 4e8e4665790aa228bb30aac05ea4782cfe4a62f1
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770176"
---
# <a name="how-to-customize-class-diagrams"></a>Postupy: přizpůsobení diagramů tříd

Můžete změnit způsob, jak diagramy tříd zobrazují informace. Můžete přizpůsobit celý diagram nebo jednotlivé typy na ploše návrhu.

Můžete například upravit úroveň zvětšení celého diagramu tříd, změnit způsob seskupování a řazení jednotlivých členů typu, skrýt nebo zobrazit vztahy a přesunout jednotlivé typy nebo množiny typů kamkoli v diagramu.

> [!NOTE]
> Upravením způsobu, jakým se tvary v diagramu zobrazují, nezměníte základní kód pro typy znázorněné v diagramu.

Oddíly, které obsahují členy typu, jako je například oddíl **Properties (vlastnosti** ) třídy, se nazývají oddíly. Jednotlivé oddíly a členy typu můžete skrýt nebo zobrazit.

## <a name="zoom-in-and-out-of-the-class-diagram"></a>Přiblížení a oddálení diagramu tříd

1. Otevřete a vyberte soubor diagramu tříd v **Návrhář tříd**.

2. Na panelu nástrojů **Návrhář tříd** klikněte na tlačítko **přiblížení** nebo **oddálení** a změňte úroveň přiblížení plochy návrháře.

     – nebo –

     Zadejte hodnotu přiblížení. Můžete použít rozevírací seznam **Lupa** nebo zadat platnou úroveň přiblížení (platný rozsah je mezi 10 a 400%).

    > [!NOTE]
    > Změna úrovně přiblížení neovlivní měřítko výtisku vašeho diagramu tříd.

## <a name="customize-grouping-and-sorting-of-type-members"></a>Přizpůsobení seskupování a řazení členů typu

1. Otevřete a vyberte soubor diagramu tříd v **Návrhář tříd**.

2. Klikněte pravým tlačítkem myši na prázdnou oblast na návrhové ploše a nastavte ukazatel na **členy skupiny**.

3. Vyberte jednu z dostupných možností:

    - **Seskupení podle druhu** odděluje jednotlivé členy typu do seskupeného seznamu vlastností, metod, událostí a polí. Jednotlivé skupiny závisí na definici entit: třída například nebude zobrazovat žádnou skupinu událostí, pokud pro danou třídu zatím nebyly definovány žádné události.

    - **Seskupení podle přístupu** odděluje jednotlivé členy typu do seskupeného seznamu založeného na modifikátorech přístupu člena. Například veřejné a soukromé.

    - **Řazení abecedně** zobrazuje položky, které tvoří entitu jako jeden abecední seznam. Seznam je seřazen vzestupně.

## <a name="hide-compartments-on-a-type"></a>Skrytí oddílů typu

1. Otevřete a vyberte soubor diagramu tříd v **Návrhář tříd**.

2. Pravým tlačítkem myši klikněte na kategorii členů v typu, který chcete upravit (například vyberte uzel **metody** ve třídě.

3. Klikněte na **Skrýt oddíl**.

     Vybraný oddíl zmizí z kontejneru typu.

## <a name="hide-individual-members-on-a-type"></a>Skrytí jednotlivých členů typu

1. Otevřete a vyberte soubor diagramu tříd v **Návrhář tříd**.

2. Klikněte pravým tlačítkem myši na člen v typu, který chcete skrýt.

3. Klikněte na tlačítko **Skrýt**.

     Vybraný člen zmizí z kontejneru typu.

## <a name="show-hidden-compartments-and-members-on-a-type"></a>Zobrazení skrytých oddílů a členů typu

1. Otevřete a vyberte soubor diagramu tříd v **Návrhář tříd**.

2. Klikněte pravým tlačítkem na název typu se skrytým oddílem.

3. Klikněte na **Zobrazit všechny členy**.

     Všechny skryté oddíly a členy se zobrazí v kontejneru typu.

## <a name="hide-relationships"></a>Skrytí vztahů

1. Otevřete a vyberte soubor diagramu tříd v **Návrhář tříd**.

2. Klikněte pravým tlačítkem myši na asociační čáru nebo čáru dědičnosti, kterou chcete skrýt.

3. Klikněte na **Skrýt** pro asociační čáry a pak klikněte na **Skrýt čáru dědičnosti** pro čáry dědičnosti.

4. Klikněte na **Zobrazit všechny členy**.

     Všechny skryté oddíly a členy se zobrazí v kontejneru typu.

## <a name="show-hidden-relationships"></a>Zobrazení skrytých vztahů

1. Otevřete a vyberte soubor diagramu tříd v **Návrhář tříd**.

2. Klikněte pravým tlačítkem na typ se skrytým přidružením nebo dědičností.

   Klikněte na **Zobrazit všechny členy** pro asociační linky a klikněte na **Zobrazit základní třídu** nebo **Zobrazit odvozené třídy** pro čáry dědičnosti.

## <a name="remove-a-shape-from-a-class-diagram"></a>Odebrání tvaru z diagramu tříd
Můžete odebrat tvar typu z diagramu tříd bez ovlivnění základního kódu typu. Odebrání tvarů typu z diagramu tříd ovlivní pouze tento diagram: základní kód definující typ a ostatní diagramy, které typ zobrazují, ovlivněny nejsou.

1. V diagramu tříd vyberte tvar typu, který chcete z diagramu odebrat.

2. V nabídce **Upravit** vyberte možnost **Odebrat z diagramu**.

     Tvar typu a čáry přidružení nebo dědičnosti spojené s tvarem se již v diagramu nezobrazí.

## <a name="delete-a-type-shape-and-its-underlying-code"></a>Odstranění tvaru typu a jeho základního kódu

1. Klikněte pravým tlačítkem myši na tvar na návrhové ploše.

2. V místní nabídce vyberte **Odstranit kód** .

     Tvar je odstraněn z diagramu a jeho základní kód je odstraněn z projektu.

## <a name="see-also"></a>Viz také:

- [Postupy: Změna mezi zápisem člena a zápisem přidružení](how-to-change-between-member-notation-and-association-notation.md)
- [Postupy: zobrazení existujících typů](how-to-view-existing-types.md)
- [Zobrazování typů a vztahů](designing-and-viewing-classes-and-types.md)
