---
title: Vlastnosti přidružení v diagramech tříd UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c5c914d87f0740dcd7b0f71190a4c2f54727f66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652096"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Vlastnosti přidružení v diagramech tříd UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu tříd UML lze nakreslit *přidružení* mezi libovolnými páry typů. Typ je třída, rozhraní nebo výčet.

 Asociace označuje, že systém, který vyvíjí, ukládá odkazy na určitý druh mezi instancemi přidružených typů. Obecně to nezahrnuje žádné informace o implementaci odkazů. Můžou to být například ukazatele, řádky v tabulce, názvy křížových odkazů v XML a tak dále.

 Přidružení je diagramatické metoda zobrazení atributu nebo páru atributů. Například pokud jste definovali třídu restauraci tak, aby měla atribut typu nabídka, můžete stejnou definici nakreslit přidružením mezi restaurací a nabídkou.

 Chcete-li nakreslit přidružení, klikněte na tlačítko **asociace** v sadě nástrojů, klikněte na první typ a pak na druhý. Můžete kliknout na stejný typ dvakrát a zobrazit tak, že instance mohou být propojeny s jinými instancemi stejného typu.

## <a name="properties"></a>Vlastnosti
 Jedná se o vlastnosti přidružení v diagramu tříd UML.

 Vlastnosti přidružení zobrazíte tak, že kliknete pravým tlačítkem na přidružení a potom kliknete na **vlastnosti**. Vlastnosti se zobrazí v okno Vlastnosti.

 Některé vlastnosti jsou také viditelné v diagramu, jak je znázorněno na následujícím obrázku.

 ![Vlastnosti přidružení](../modeling/media/uml-classprop.png "UML_ClassProp")

|**Vlastnost**|Popis|
|------------------|-----------------|
|**Název (1)**|Identifikuje přidružení. Také se zobrazí v diagramu poblíž střední části přidružení.|
|**Kvalifikovaný název**|Jednoznačně identifikuje přidružení. Předpona s úplným názvem balíčku, který obsahuje první roli přidružení.|
|**Pracovní položky**|Počet pracovních položek propojených s tímto přidružením Chcete-li propojit pracovní položky, přečtěte si téma [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|
|**Color**|Barva konektoru. Na rozdíl od ostatních vlastností se jedná o vlastnost tohoto zobrazení přidružení, nikoli o vlastnost podkladového vztahu v modelu.|
|**První role**<br /><br /> **Druhá role**|Každý konec asociace se nazývá role. Každá role popisuje vlastnosti ekvivalentního atributu pro třídu na opačném konci přidružení.<br /><br /> V diagramu příkladu obsahuje přidružení mezi nabídkou a položkou nabídky role s názvem nabídka a obsah.<br /><br /> Obsah je název atributu třídy nabídky.|

### <a name="properties-of-each-role"></a>Vlastnosti každé role
 Vlastnosti každé role zobrazíte tak, že rozbalíte vlastnost **první role** nebo **druhá role** .

|     **Vlastnost**     |          **Výchozí**          |                                                                                                                                                                                                                                                                                                                                        Popis                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Název role (2)**   | Název typu v této roli |                                                                                                                                                                                                                                                                                                       Název role. Zobrazuje se na konci přidružení v diagramu.                                                                                                                                                                                                                                                                                                        |
|   **Agregovat**    |             Žádné              |                                                                        **None** (4) – představuje obecný vztah mezi instancemi tříd.<br /><br /> **Složené** (5) – objekt v této roli obsahuje objekt u protilehlé role. Pomocí **složeného** nástroje můžete vytvořit přidružení se složenou agregací.<br /><br /> **Shared** (6) – objekt v této roli obsahuje odkazy na objekt v druhé roli. Pomocí nástroje **agregace** můžete vytvořit přidružení se sdílenou agregací.<br /><br /> Přesný výklad je otevřený pro místní konvenci.                                                                         |
|    **Je odvozen**    |             Ne             |                                                                                                                                                                                                                          Při hodnotě true se objekt na tomto konci odkazu vypočítá z jiných atributů a přidružení. Například MyWorkPlace vypočítaný z MyEmployer. pracoviště. Podrobnosti by měly být zadány v popisu nebo připojeném komentáři.                                                                                                                                                                                                                           |
| **Je odvozen sjednocení** |             Ne             |                                                                                                                                                                                                                                                                                                             Pokud je nastaveno na true, role je sjednocením sady rolí v odvozených typech.                                                                                                                                                                                                                                                                                                             |
|   **Je naviguje**   |             Ano              |                                                 V tomto směru lze toto přidružení přečíst. Vzhledem k instanci protější role může software, který popisujete, efektivně určit přidruženou instanci v této roli.<br /><br /> Pokud je jedna role naviguje a druhá není, zobrazí se u přidružení ve směru naviguje šipka (7).<br /><br /> Ve výchozím nastavení vytvoří nástroj přidružení přidružení naviguje v jednom směru. Pokud ho chcete převést na obousměrné přidružení, můžete vybrat přidružení, kliknout na značku akce, která se zobrazí, a pak kliknout na **nastavit obousměrný**.                                                 |
|   **Je jen pro čtení**   |             Ne             |                                                                                                                                                                                                                                                                                   Je-li nastavena hodnota true, nelze po vytvoření instance přidružení změnit. Odkaz je vždy na stejný objekt.                                                                                                                                                                                                                                                                                    |
| **Násobnost (3)** |               1               | **1** – tento konec přidružení vždy odkazuje na jeden objekt. Každá položka nabídky má na obrázku jednu nabídku.<br /><br /> **0.. 1** – tento konec vazeb přidružení k jednomu objektu nebo neexistuje odkaz.<br /><br /> **\\**\* -Každý objekt na druhém konci přidružení je propojen s kolekcí objektů na tomto konci a kolekce může být prázdná.<br /><br /> **1.. \\ ** \* – každý objekt na druhém konci přidružení je propojen s alespoň jedním objektem na tomto konci. Každá nabídka na obrázku obsahuje alespoň jednu položku nabídky.<br /><br /> *n* **...** *m* – každý objekt na druhém konci má kolekci mezi *n* a *m* odkazy na objekty na tomto konci. |
|    **Je seřazen**    |             Ne             |                                                                                                                                                                                                                                                                                                  Pokud má hodnotu true, vrácená kolekce vytvoří sekvenční seznam. Pro násobnost větší než 1.                                                                                                                                                                                                                                                                                                   |
|    **Je jedinečný**     |             Ne             |                                                                                                                                                                                                                                                                                              Pokud má hodnotu true, v vrácené kolekci nejsou žádné duplicitní hodnoty. Pro násobnost větší než 1.                                                                                                                                                                                                                                                                                              |
|    **Přehlednost**    |            Veřejná             |                                                                                                                                                                                                                                 Veřejné – viditelné globálně<br /><br /> Private – nezobrazuje se mimo vlastnící typ.<br /><br /> Protected-Visible pro typy odvozené od vlastníka<br /><br /> Balíček – viditelný pro jiné typy v rámci stejného balíčku.                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Viz také
 [Diagramy tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) [vlastnosti typů v DIAGRAMech tříd UML](../modeling/properties-of-types-on-uml-class-diagrams.md) vlastnosti [atributů v](../modeling/properties-of-attributes-on-uml-class-diagrams.md) diagramech tříd UML [vlastnosti operací v](../modeling/properties-of-operations-on-uml-class-diagrams.md) diagramech tříd UML diagramy tříd [UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)
