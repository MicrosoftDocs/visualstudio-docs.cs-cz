---
title: 'Postupy: přizpůsobení diagramů tříd (návrhář tříd) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a4b163aef25972968933d3352486aab9ebbf962
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950973"
---
# <a name="how-to-customize-class-diagrams-class-designer"></a>Postupy: Přizpůsobení diagramů tříd (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit způsob, jak diagramy tříd zobrazují informace. Můžete přizpůsobit celý diagram nebo jednotlivé typy na ploše návrhu.  
  
 Můžete například upravit úroveň zvětšení celého diagramu tříd, změnit způsob seskupování a řazení jednotlivých členů typu, skrýt nebo zobrazit vztahy a přesunout jednotlivé typy nebo množiny typů kamkoli v diagramu.  
  
> [!NOTE]
>  Upravením způsobu, jakým se tvary v diagramu zobrazují, nezměníte základní kód pro typy znázorněné v diagramu.  
  
 Části, které obsahují členy typu, jako je například část Vlastnosti ve třídě, se nazývají oddíly. Jednotlivé oddíly a členy typu můžete skrýt nebo zobrazit.  
  
 **V tomto tématu**  
  
-   [Přiblížení a oddálení diagramu tříd](../ide/how-to-customize-class-diagrams-class-designer.md#ZoomInOut)  
  
-   [Přizpůsobení seskupování a řazení členů typu](../ide/how-to-customize-class-diagrams-class-designer.md#CustomizeGroupingSorting)  
  
-   [Skrytí oddílů typu](../ide/how-to-customize-class-diagrams-class-designer.md#HideCompartments)  
  
-   [Skrytí jednotlivých členů typu](../ide/how-to-customize-class-diagrams-class-designer.md#HideMembers)  
  
-   [Zobrazení skrytých oddílů a členů typu](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayHiddenCompartmentsAndMemberrs)  
  
-   [Skrytí vztahů](../ide/how-to-customize-class-diagrams-class-designer.md#HideAssociationAndInheritance)  
  
-   [Zobrazení skrytých vztahů](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayAssociationAndInheritance)  
  
-   [Odebrání tvaru z diagramu tříd](../ide/how-to-customize-class-diagrams-class-designer.md#RemoveCodeAndShape)  
  
-   [Odstranění tvaru typu a jeho základního kódu](../ide/how-to-customize-class-diagrams-class-designer.md#DeleteTypeShapeAndCode)  
  
##  <a name="ZoomInOut"></a> Přiblížení a oddálení diagramu tříd  
  
1.  Otevřete a vyberte soubor diagramu tříd v Návrháři tříd.  
  
2.  Na panelu nástrojů návrháře tříd klikněte na tlačítko **přiblížit** nebo **Oddálit** tlačítko a změňte úroveň přiblížení návrhové ploše.  
  
     or  
  
     Zadejte hodnotu přiblížení. Můžete použít **přiblížení** rozevíracím seznamu nebo zadejte platnou úroveň přiblížení (platný rozsah je od 10 do 400 %).  
  
    > [!NOTE]
    >  Změna úrovně přiblížení neovlivní měřítko výtisku vašeho diagramu tříd.  
  
##  <a name="CustomizeGroupingSorting"></a> Přizpůsobení seskupování a řazení členů typu  
  
1.  Otevřete a vyberte soubor diagramu tříd v Návrháři tříd.  
  
2.  Klikněte pravým tlačítkem na prázdnou oblast na návrhové ploše a přejděte na **členy skupiny**.  
  
3.  Vyberte jednu z dostupných možností:  
  
    1.  **Seskupit podle druhu** odděluje jednotlivé členy typu do seskupeného seznamu vlastností, metod, událostí a polí. Jednotlivé skupiny závisí na definici entit: třída například nebude zobrazovat žádnou skupinu událostí, pokud pro danou třídu zatím nebyly definovány žádné události.  
  
    2.  **Seskupit podle přístupu ke** modifikátorů přístupu odděluje jednotlivé členy typu do seskupeného seznamu na základě tohoto členu. Například veřejné a soukromé.  
  
    3.  **Seřadit podle abecedy** zobrazuje položky, které tvoří entitu, jako jeden abecední seznam. Seznam je seřazen vzestupně.  
  
##  <a name="HideCompartments"></a> Skrytí oddílů typu  
  
1.  Otevřete a vyberte soubor diagramu tříd v Návrháři tříd.  
  
2.  Klikněte pravým tlačítkem myši klikněte na kategorii členu v typu, který chcete přizpůsobit (například, vyberte **metody** uzlu ve třídě.  
  
3.  Klikněte na tlačítko **skrýt oddíl**.  
  
     Vybraný oddíl zmizí z kontejneru typu.  
  
##  <a name="HideMembers"></a> Skrytí jednotlivých členů typu  
  
1.  Otevřete a vyberte soubor diagramu tříd v Návrháři tříd.  
  
2.  Klikněte pravým tlačítkem myši na člen v typu, který chcete skrýt.  
  
3.  Klikněte na tlačítko **skrýt**.  
  
     Vybraný člen zmizí z kontejneru typu.  
  
##  <a name="DisplayHiddenCompartmentsAndMemberrs"></a> Zobrazení skrytých oddílů a členů typu  
  
1.  Otevřete a vyberte soubor diagramu tříd v Návrháři tříd.  
  
2.  Klikněte pravým tlačítkem na název typu se skrytým oddílem.  
  
3.  Klikněte na tlačítko **zobrazit všechny členy**.  
  
     Všechny skryté oddíly a členy se zobrazí v kontejneru typu.  
  
##  <a name="HideAssociationAndInheritance"></a> Skrytí vztahů  
  
1.  Otevřete a vyberte soubor diagramu tříd v Návrháři tříd.  
  
2.  Klikněte pravým tlačítkem myši na asociační čáru nebo čáru dědičnosti, kterou chcete skrýt.  
  
3.  Klikněte na tlačítko **skrýt** pro Asociační čáry a klikněte na **Skrýt čáru dědičnosti** u čar dědičnosti.  
  
4.  Klikněte na tlačítko **zobrazit všechny členy**.  
  
     Všechny skryté oddíly a členy se zobrazí v kontejneru typu.  
  
##  <a name="DisplayAssociationAndInheritance"></a> Zobrazení skrytých vztahů  
  
1. Otevřete a vyberte soubor diagramu tříd v Návrháři tříd.  
  
2. Klikněte pravým tlačítkem na typ se skrytým přidružením nebo dědičností.  
  
   Klikněte na tlačítko **zobrazit všechny členy** pro Asociační čáry a klikněte na **zobrazit základní třídu** nebo **Zobrazit odvozené třídy** u čar dědičnosti.  
  
##  <a name="RemoveCodeAndShape"></a> Odebrání tvaru z diagramu tříd  
 Můžete odebrat tvar typu z diagramu tříd bez ovlivnění základního kódu typu. Odebrání tvarů typu z diagramu tříd ovlivní pouze tento diagram: základní kód definující typ a ostatní diagramy, které typ zobrazují, ovlivněny nejsou.  
  
1.  V diagramu tříd vyberte tvar typu, který chcete z diagramu odebrat.  
  
2.  Na **upravit** nabídce zvolte **odebrat z diagramu**.  
  
     Tvar typu a čáry přidružení nebo dědičnosti spojené s tvarem se již v diagramu nezobrazí.  
  
##  <a name="DeleteTypeShapeAndCode"></a> Odstranění tvaru typu a jeho základního kódu  
  
1.  Klikněte pravým tlačítkem myši na tvar na návrhové ploše.  
  
2.  Vyberte **smazat kód** v místní nabídce.  
  
     Tvar je odstraněn z diagramu a jeho základní kód je odstraněn z projektu.  
  
## <a name="see-also"></a>Viz také  
 [Práce s diagramy tříd (návrhář tříd)](../ide/working-with-class-diagrams-class-designer.md)   
 [Postupy: změna mezi zápisem člena a zápisem asociace (návrhář tříd)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)   
 [Postupy: zobrazení existujících typů (návrhář tříd)](../ide/how-to-view-existing-types-class-designer.md)   
 [Zobrazování typů a vztahů (Návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md)



