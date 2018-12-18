---
title: Vlastnosti přidružení v UML diagramech tříd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b132ee2aa0f67662fcfcad92b8ae945c2d66c680
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810281"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Vlastnosti přidružení v diagramech tříd UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu tříd UML lze nakreslit *přidružení* mezi nějaká dvojice typy. Typ je třída, rozhraní nebo výčet.  

 Přidružení označuje, že systém, který vyvíjíte ukládá odkazů mezi instancemi přidružené typy určitého druhu. Obecně platí neznamená to nic o implementaci odkazy. Například se může být, že ukazatele, řádky v tabulce, křížové odkazy. názvy ve formátu XML a tak dále.  

 Asociace je diagramatické metoda znázorňující atribut nebo dvojice atributů. Například pokud definujete třídy restaurace s atributem typu Nabídka vám stavu stejnou definici pojmů kreslením přidružení mezi restaurace a nabídky.  

 Chcete-li nakreslit asociace, klikněte na tlačítko **přidružení** v sadě nástrojů klikněte na typ první a druhý. Dvěma časy stejného typu můžete kliknout a zobrazit, že instance lze propojit s jinými instancemi stejného typu.  

## <a name="properties"></a>Vlastnosti  
 Toto jsou vlastnosti asociace v diagramu tříd UML.  

 Pokud chcete zobrazit vlastnosti asociace, klikněte pravým tlačítkem na přidružení a potom klikněte na **vlastnosti**. Vlastnosti se zobrazí v okně Vlastnosti.  

 Některé vlastnosti jsou také viditelné v diagramu, jak je znázorněno na následujícím obrázku.  

 ![Vlastnosti přidružení](../modeling/media/uml-classprop.png "UML_ClassProp")  

|**Vlastnost**|Popis|  
|------------------|-----------------|  
|**Název (1)**|Identifikuje přidružení. Také se zobrazí v diagramu v polovině přidružení.|  
|**Kvalifikovaný název**|Jednoznačně identifikuje přidružení. Předponu úplný název balíčku, který obsahuje první role přidružení.|  
|**Pracovní položky**|Počet propojení pracovních položek s toto přidružení. Pokud chcete propojit pracovní položky, naleznete v tématu [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|  
|**Barva**|Barva konektoru. Na rozdíl od dalších vlastností Toto je vlastnost tohoto zobrazení přidružení, nejedná se o vlastnost základní relace v modelu.|  
|**První Role**<br /><br /> **Druhá Role**|Každý konec asociace, se nazývá role. Každá role jsou popsané vlastnosti odpovídající atribut ve třídě na protilehlé straně asociace.<br /><br /> Přidružení mezi nabídkou a položka nabídky v diagramu příklad má rolí jako nabídky a obsah.<br /><br /> Obsah je název atributu ve třídě nabídky.|  

### <a name="properties-of-each-role"></a>Vlastnosti jednotlivých rolí  
 Chcete-li zobrazit vlastnosti jednotlivých rolí, rozbalte **první Role** nebo **druhá Role** vlastnost.  


|     **Vlastnost**     |          **Default**          |                                                                                                                                                                                                                                                                                                                                        Popis                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Název role (2)**   | Název typu na tuto roli |                                                                                                                                                                                                                                                                                                       Název role. Zobrazí se blíží ke konci asociace v diagramu.                                                                                                                                                                                                                                                                                                        |
|   **Agregace**    |             Žádné              |                                                                        **Žádný** (4) – představuje obecné vztah mezi instancemi třídy.<br /><br /> **Složený** (5) – objekt v opačné role obsahuje objekt v této roli. Můžete použít **složené** vytvořte přidružení k složené agregace.<br /><br /> **Sdílené** (6) – objekt v této roli obsahuje odkazy na objekt v jiné roli. Můžete použít **agregace** nástroj k vytvoření přidružení s průběhem Shared.<br /><br /> Přesné výkladu je otevřená pro místní konvence.                                                                         |
|    **Je odvozen**    |             False             |                                                                                                                                                                                                                          Při hodnotě true se objekt v tomto konci odkazu se počítá od jiné atributy a asociace. Například MyWorkPlace počítají na základě MyEmployer.WorkPlace. Podrobnosti by měly být typu v popisu nebo připojeného komentáře.                                                                                                                                                                                                                           |
| **Je odvozen sjednocení** |             False             |                                                                                                                                                                                                                                                                                                             Při hodnotě true je role sjednocení sadu rolí v odvozených typech.                                                                                                                                                                                                                                                                                                             |
|   **Jedná o navigaci**   |             Hodnota TRUE              |                                                 Přidružení můžete přečíst v tomto směru. Zadané instance opačné role, software, který se popisující efektivně určit přidruženou instanci v této roli.<br /><br /> Pokud jedna role je Navigable a druhý není, se šipka zobrazí (7) na přidružení v jejím směru.<br /><br /> Ve výchozím nastavení vytvoří nástroj přidružení asociace je provázána v jednom směru. Převést na přidružení obousměrný, můžete vybrat přidružení, klikněte na značku akce, který se zobrazí a potom klikněte na **vytvořit obousměrný**.                                                 |
|   **Je jen pro čtení**   |             False             |                                                                                                                                                                                                                                                                                   Při hodnotě true nelze po jeho vytvoření změnit instance přidružení. Odkaz je vždy stejný objekt.                                                                                                                                                                                                                                                                                    |
| **Násobnost (3)** |               1               | **1** – za tímto účelem přidružení vždy odkazuje na jeden objekt. Na obrázku má každá položka nabídky jednu nabídku.<br /><br /> **0..1** – jedna ze dvou za tímto účelem přidružení odkazuje na jeden objekt nebo neexistuje žádný odkaz.<br /><br /> **\\**\* -všechny objekty na druhém konci přidružení je propojený na kolekci objektů za tímto účelem a kolekce může být prázdný.<br /><br /> **1..\\**  \* – každý objekt na druhém konci přidružení je propojený s alespoň jeden objekt za tímto účelem. Na obrázku každý nabídka obsahuje alespoň jednu položku nabídky.<br /><br /> *n* **...** *m* -každého objektu na druhém konci má kolekci mezi *n* a *m* odkazy na objekty za tímto účelem. |
|    **Je seřazen**    |             False             |                                                                                                                                                                                                                                                                                                  Při hodnotě true se vrácená kolekce tvoří sekvenční seznamu. Pro násobnost větší než 1.                                                                                                                                                                                                                                                                                                   |
|    **Je jedinečný**     |             False             |                                                                                                                                                                                                                                                                                              Pokud je hodnota true, nejsou žádné duplicitní hodnoty v kolekci vrácené. Pro násobnost větší než 1.                                                                                                                                                                                                                                                                                              |
|    **Viditelnost**    |            Public             |                                                                                                                                                                                                                                 Public – viditelné globálně<br /><br /> Privátní – nejsou viditelné mimo vlastnící typ<br /><br /> Chráněné – viditelné pro typy odvozené od vlastníka<br /><br /> Balíček – viditelné pro ostatní typy v rámci stejného balíčku.                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Viz také  
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Vlastnosti typů v diagramech tříd UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)



