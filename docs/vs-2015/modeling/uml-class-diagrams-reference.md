---
title: 'Diagramy tříd UML: referenční informace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06e83e254cad77d4ede9716a18a51f6476fb51ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850179"
---
# <a name="uml-class-diagrams-reference"></a>Diagramy tříd UML: Referenční dokumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagram tříd UML popisuje objekty a informační struktury, které vaše aplikace používá, interně i ve spojení s uživateli. Tyto informace popisuje bez odkazů na konkrétní implementaci. Jeho třídy a vztahy mohou být implementovány mnoha způsoby, jako jsou tabulky databáze, uzly XML nebo kompozice softwarových objektů.

> [!NOTE]
> Toto téma se zabývá diagramy tříd UML. Existuje jiný druh diagramu tříd, diagram tříd .NET, který slouží k vizualizaci kódu programu. Další informace najdete v tématu [navrhování a zobrazování tříd a typů](https://msdn.microsoft.com/library/ab7aty24.aspx).

 Chcete-li vytvořit diagram tříd UML, v nabídce **Architektura** vyberte možnost **Nový diagram UML nebo vrstva**. Další informace o vykreslování diagramů tříd UML naleznete v tématu [diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md). Další informace o vytváření a kreslení diagramů modelování najdete v tématu [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Čtení diagramů tříd
 Tabulka v této části popisuje prvky, které lze zobrazit v diagramu tříd UML. Informace o vlastnostech těchto prvků naleznete v následujících tématech:

- [Vlastnosti typů v diagramech tříd UML](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Vlastnosti přidružení v diagramech tříd UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Tři třídy ukazující vztahy a vlastnosti](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Obrazec** |       **Prvek**        |                                                                                                                                                             **Popis**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Třída**         |                                                           Definice objektů, které sdílejí dané strukturální nebo behaviorální charakteristiky. Další informace naleznete v tématu [vlastnosti typů v diagramech tříd UML](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Klasifikátor        |                                                                                                             Obecný název třídy, rozhraní nebo výčtu. Komponenty, případy použití a objekty actor jsou také třídění.                                                                                                             |
|     2     | Sbalit/rozbalit ovládací prvek |                                                                                         Pokud nevidíte podrobnosti o třídění, klikněte na rozšíření v levém horním rohu třídění. Může být také nutné kliknout na [+] v každém segmentu.                                                                                         |
|     3     |      **Atribut**       |   Zadaná hodnota připojená k každé instanci klasifikátoru.<br /><br /> Chcete-li přidat atribut, klikněte na oddíl **atributy** a potom stiskněte klávesu **ENTER**. Zadejte signaturu atributu. Další informace naleznete v tématu [vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Operace**       | Metoda nebo funkce, které mohou být provedeny instancemi klasifikátoru. Chcete-li přidat operaci, klikněte na část **operace** a potom stiskněte klávesu **ENTER**. Zadejte podpis operace. Další informace najdete v tématu [vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Řídí**      |                                                                  Vztah mezi členy dvou klasifikátorů. Další informace najdete v tématu [Vlastnosti přidružení v diagramech tříd UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    vkládá     |     **Agregovat**      |                                                                                                    Přidružení představující vztah sdíleného vlastnictví. Vlastnost **agregace** role vlastníka je nastavena na hodnotu **Shared**.                                                                                                     |
|    5b     |     **Složení**      |                                                                                                      Přidružení představující relaci celé části. Vlastnost **agregace** role vlastníka je nastavena na hodnotu **složené**.                                                                                                      |
|     6     |   **Název přidružení**   |                                                                                                                                         Název přidružení. Název může být ponechán prázdný.                                                                                                                                          |
|     7     |      **Název role**       |                       Název role, tj. jeden konec přidružení. Dá se použít k odkazování na přidružený objekt. V předchozím obrázku se v případě libovolného pořadí `O` `O.ChosenMenu` jedná o jeho přidruženou nabídku.<br /><br /> Každá role má své vlastní vlastnosti, které jsou uvedené v části vlastnosti přidružení.                       |
|     8     |     **Násobnost**     |                                         Určuje, kolik objektů na tomto konci lze propojit s každým objektem. V tomto příkladu musí být každá objednávka propojená s právě jednou nabídkou.<br /><br /> **\\**\* znamená, že není k dispozici horní limit počtu odkazů, které lze vytvořit.                                         |
|     9     |    **Generalizace**    |  *Konkrétní* třídění dědí část jeho definice z *obecného* třídění. Obecný klasifikátor se nachází na konci šipky konektoru. Atributy, přidružení a operace dědí konkrétní třídění.<br /><br /> Pomocí nástroje **dědičnosti** vytvořte generalizaci mezi dvěma klasifikátory.   |

 ![Balíček obsahující rozhraní a výčet](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Obrazec|Element|Popis|
|-----------|-------------|-----------------|
|10|**Rozhraní**|Definice části externě viditelného chování objektu. Další informace naleznete v tématu [vlastnosti typů v diagramech tříd UML](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumeration**|Klasifikátor, který se skládá ze sady hodnot literálů.|
|12|**Balíček**|Skupina klasifikátorů, přidružení, akcí, životností, komponent a balíčků. Diagram logické třídy ukazuje, že jsou v balíčku obsaženy klasifikátory členů a balíčky.<br /><br /> Názvy jsou v rámci balíčků vymezeny tak **, aby** se v rámci **PACKAGE1** liší od **Class1** mimo daný balíček. Název balíčku se zobrazí jako součást vlastností **kvalifikovaného názvu** jeho obsahu.<br /><br /> Vlastnost **propojený balíček** libovolného diagramu UML můžete nastavit tak, aby odkazovala na balíček. Všechny prvky, které vytvoříte v tomto diagramu, se pak stanou součástí balíčku. Budou zobrazeny pod balíčkem v **Průzkumníkovi modelů UML**.|
|13|**Import**|Vztah mezi balíčky, což značí, že jeden balíček obsahuje všechny definice jiné.|
|14|**Závislost**|Definice nebo implementace závislého klasifikátoru se může změnit, pokud se změní klasifikátor na konci šipky.|

 ![Realizace zobrazená pomocí konektor a lupy](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Obrazec|**Element**|Popis|
|-----------|-----------------|-----------------|
|15|**Realizace**|Třída implementuje operace a atributy definované rozhraním.<br /><br /> Použijte nástroj **Dědičnost** k vytvoření realizace mezi třídou a rozhraním.|
|16|**Realizace**|Alternativní prezentace stejného vztahu. Popisek na symbolu lupy identifikuje rozhraní.<br /><br /> Chcete-li vytvořit tuto prezentaci, vyberte existující vztah realizace. V blízkosti přidružení se zobrazí značka akce. Klikněte na značku akce a pak klikněte na **Zobrazit jako Lupa**.|

## <a name="see-also"></a>Viz také
 [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md) v diagramech [tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md) pro vlastnosti [typů v diagramech tříd](../modeling/properties-of-types-on-uml-class-diagrams.md) UML vlastnosti [atributů v](../modeling/properties-of-attributes-on-uml-class-diagrams.md) diagramech tříd UML vlastnosti operací v diagramech tříd [UML vlastnosti](../modeling/properties-of-associations-on-uml-class-diagrams.md) [operací v](../modeling/properties-of-operations-on-uml-class-diagrams.md) diagramech tříd UML
