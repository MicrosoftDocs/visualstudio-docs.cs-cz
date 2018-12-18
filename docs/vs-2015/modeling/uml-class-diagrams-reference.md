---
title: 'Diagramy tříd UML: Referenční | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4f3a4fe9949236045238688a9edcd5eef911efb8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741064"
---
# <a name="uml-class-diagrams-reference"></a>Diagramy tříd UML: Referenční dokumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagram tříd UML popisuje objektu a informace o strukturách používané aplikace, interně i v komunikaci se svým uživatelům. Popisuje informace, bez ohledu na žádnou konkrétní implementaci. Jeho tříd a vztahů je možné implementovat mnoha způsoby, například databázové tabulky, z uzlů XML nebo sestavení objektů softwaru.  
  
> [!NOTE]
>  Toto téma se zabývá diagramy tříd UML. Existuje jiný typ diagramu tříd, diagram tříd .NET, který slouží k vizualizaci kódu programu. Další informace najdete v tématu [navrhování a zobrazování tříd a typů](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
 Chcete-li vytvořit diagram tříd UML, na **architektury** nabídce zvolte **nové UML nebo diagramu vrstev**. Další informace o tom, jak nakreslit diagramy tříd UML, naleznete v tématu [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md). Další informace o tom, jak vytvořit a kreslit diagramy modelování najdete v tématu [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-class-diagrams"></a>Čtení diagramů tříd  
 Tabulky v této části popisuje prvky, které se zobrazí v diagramu tříd UML. Informace o vlastnostech těchto prvků naleznete v následujících tématech:  
  
- [Vlastnosti typů v diagramech tříd UML](../modeling/properties-of-types-on-uml-class-diagrams.md)  
  
- [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
- [Vlastnosti přidružení v diagramech tříd UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
  ![Tři třídy znázorňující vztahy a vlastnosti](../modeling/media/uml-classovreading.png "UML_ClassOvReading")  
  
| **Obrazec** |       **Element**        |                                                                                                                                                             **Popis**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Třída**         |                                                           Definice objektů, které sdílejí daný strukturální nebo behaviorální charakteristiky. Další informace najdete v tématu [diagramech tříd vlastnosti typů v UML](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Třídění        |                                                                                                             Obecný název třídy, rozhraní nebo výčet. Komponenty, případy použití a actors jsou také Klasifikátory.                                                                                                             |
|     2     | Sbalit nebo rozbalit ovládací prvek |                                                                                         Pokud nelze zobrazit podrobnosti o třídění, klikněte na rozšíření v levém horním třídění. Budete také muset klikněte na tlačítko [+] v každém segmentu.                                                                                         |
|     3     |      **Atribut**       |   Zadaná hodnota připojeným ke každé instanci třídění.<br /><br /> Chcete-li přidat atribut, klikněte na tlačítko **atributy** části a potom stiskněte klávesu **ENTER**. Typ podpisu atributu. Další informace najdete v tématu [diagramech tříd vlastnosti atributů v UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Operace**       | Metoda nebo funkce, které instance klasifikátoru mohou provádět. Chcete-li přidat operaci, klikněte na tlačítko **operace** části a potom stiskněte klávesu **ENTER**. Typ podpisu operace. Další informace najdete v tématu [vlastnosti operací v UML diagramech tříd](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Přidružení**      |                                                                  Vztah mezi dvěma Klasifikátory jako objekty její členové. Další informace najdete v tématu [vlastnosti přidružení v UML diagramech tříd](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Agregace**      |                                                                                                    Přidružení reprezentující relaci sdílené vlastnictví. **Agregace** role vlastník je nastavena na **Shared**.                                                                                                     |
|    5b     |     **Složení**      |                                                                                                      Přidružení představující vztah část celek. **Agregace** role vlastník je nastavena na **složené**.                                                                                                      |
|     6     |   **Název přidružení**   |                                                                                                                                         Název přidružení. Název může být prázdný.                                                                                                                                          |
|     7     |      **Název role**       |                       Název role, to znamená, že jeden konec asociace. Slouží k odkazování na související objekt. Na předchozím obrázku pro všechny objednávky `O`, `O.ChosenMenu` je jeho přidružené nabídky.<br /><br /> Každá role má své vlastní vlastnosti uvedené pod vlastností asociace.                       |
|     8     |     **Násobnost**     |                                         Určuje, kolik objektů v této ukončení nesmí být propojení každého objektu na druhém. V tomto příkladu je potřeba propojit každý pořadí přesně jednu nabídku.<br /><br /> **\\**\* znamená to, že neexistuje žádná horní limit počtu odkazů, které lze provést.                                         |
|     9     |    **Generalizace**    |  *Konkrétní* třídění dědí část definice z *Obecné* třídění. Obecného třídění je na konci šipku konektoru. Operace, přiřazení a atributy jsou zvláštní třídění dědí.<br /><br /> Použití **dědičnosti** nástroj k vytváření generalizace mezi dvěma Klasifikátory.   |
  
 ![Balíček, který obsahuje rozhraní a výčet](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")  
  
|Obrazec|Prvek|Popis|  
|-----------|-------------|-----------------|  
|10|**Rozhraní**|Definice část externě viditelného chování objektu. Další informace najdete v tématu [diagramech tříd vlastnosti typů v UML](../modeling/properties-of-types-on-uml-class-diagrams.md).|  
|11|**Výčet**|Klasifikátor, který se skládá ze sady hodnot literálů.|  
|12|**Balíček**|Skupiny klasifikátorů, přidružení, akce, životností, komponent a balíčků. Logické třídy diagram znázorňuje, že člen třídění a balíčky jsou obsaženy v rámci balíčku.<br /><br /> Názvy jsou vymezeny do balíčků tak, aby **Class1** v rámci **Package1** se liší od **Class1** mimo tento balíček. Název balíčku se zobrazí jako součást **kvalifikovaný název** vlastnosti jeho obsah.<br /><br /> Můžete nastavit **odkazovaný balíček** vlastnost jakýkoliv diagram UML odkázat na balíček. Všechny prvky, které vytvoříte v tomto diagramu se pak stane součástí balíčku. Zobrazí se v rámci balíčku v **Průzkumníku modelů UML**.|  
|13|**Import**|Vztah mezi balíčky, která udává, že se, že jeden balíček obsahuje všechny definice jiného.|  
|14|**Závislost**|Definice nebo provádění závislé třídění může změnit při změně třídění po uplynutí šipky.|  
  
 ![Realizace znázorněná s konektorem a lollipop](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")  
  
|Obrazec|**Element**|Popis|  
|-----------|-----------------|-----------------|  
|15|**realizace**|Třída implementuje operace a atributy definované v rozhraní.<br /><br /> Použití **dědičnosti** nástroj k vytváření realizace mezi třídou a rozhraní.|  
|16|**realizace**|Alternativní prezentaci stejné relace. Popisek na lollipop symbol určuje rozhraní.<br /><br /> K vytvoření této prezentace, vyberte existujícího vztahu realizace. Přidružení se zobrazí značka akce. Klikněte na značku akce a potom klikněte na tlačítko **zobrazit jako typ Lupa**.|  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)   
 [Vlastnosti typů v diagramech tříd UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Vlastnosti přidružení v diagramech tříd UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)



