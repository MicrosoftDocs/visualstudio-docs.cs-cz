---
title: Vlastnosti elementů v diagramech činnosti UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
- activity diagrams, properties
ms.assetid: 9849d45e-65d5-46bd-a319-757e90b7c748
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5a3233d073a4b54c7c52b4b725f0d15833f5a51f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803055"
---
# <a name="properties-of-elements-on-uml-activity-diagrams"></a>Vlastnosti elementů v diagramech činnosti UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Každý prvek v diagramu na diagram činností UML, má vlastnosti. Pokud chcete zobrazit vlastnosti elementu, klikněte pravým tlačítkem na elementu v diagramu nebo v **Průzkumníku modelů UML** a potom klikněte na tlačítko **vlastnosti**. Vlastnosti se zobrazí v **vlastnosti** okna.  
  
> [!NOTE]
>  Toto téma se věnuje vlastnosti elementů v diagramech činnosti UML. Informace o tom, jak přečíst diagramy činnosti UML, naleznete v tématu [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md). Další informace o tom, jak nakreslit diagramy činnosti UML, naleznete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Vlastnosti elementů  
  
|         Vlastnost         |        Výchozí         |                               Prvek                               |                                                                                                                                                                Popis                                                                                                                                                                 |
|--------------------------|------------------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         **Jméno**         |     Výchozí název     |                                 Všechny                                 |                                                                                                                                                          Určuje element.                                                                                                                                                           |
|    **Kvalifikovaný název**    |    Balíček:: název     |                                 Všechny                                 |                                                                                                                     Jednoznačně identifikuje elementu. Předponu úplný název balíčku, který jej obsahuje.                                                                                                                     |
|      **Pracovní položky**      |      související 0      |                                 Všechny                                 |                                                                                Počet pracovních položek, které jsou spojené s tímto prvkem. Přidružení pracovních položek, naleznete v tématu [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).                                                                                |
|     **Popis**      |         (žádné)         |                                 Všechny                                 |                                                                                                                                             Můžete nastavit obecné poznámky o prvku tady.                                                                                                                                             |
|        **Barva**         | (výchozí nastavení pro typ) |                                 Všechny                                 |                                                                                                                                                          Barva obrazce.                                                                                                                                                           |
|         **Text**         |         (žádné)         |                               Akce                                |                                                                                                                                                      Určuje akci podrobně.                                                                                                                                                       |
|       **Jazyk**       |         (žádné)         |                               Akce                                |                                                                                                                                                  Jazyk výrazů v těle.                                                                                                                                                   |
| **Místní vstupních** |         (žádné)         |         Akce, odeslat, přijmout, volání chování, volání operace         |                                                                                                                          Omezení, které musí být splněny, při ukončení provádění. Cílem dosáhnout akce.                                                                                                                          |
| **Místní předběžné podmínky**  |         (žádné)         |         Akce, odeslat, přijmout, volání chování, volání operace         |                                                                                                                                        Omezení, které musí být splněny, než začne provádění.                                                                                                                                         |
|    **Je synchronní**    |          Hodnota TRUE          |                    Volání chování, zavolejte operaci                    |                                                                                                                                        – Pokud je hodnota true, akce počká, až do doby ukončení aktivity.                                                                                                                                        |
|       **Chování**       |         (žádné)         |                            Volání chování                            |                                                                                                                                                         – Aktivity vyvolání.                                                                                                                                                          |
|      **Operace**       |         (žádné)         |                           Volání operace                            |                                                                                                                                                         -Operace se vyvolala.                                                                                                                                                         |
|    **Je vyřadit**     |         False          |                            Přijímat události                             |                                                                                                       – Pokud je hodnota true, může být několik typem výstupní spojky a data jsou zařazeny do nich. Pokud má hodnotu false, se zobrazí všechna data na jeden pin.                                                                                                        |
|     **Horní mez**      |        **\\**\*        |                   Objekt uzlu, parametr aktivity                   |                                                                                                      **0** označuje, že přímo máte tok musí předat data.<br /><br /> **\\**\* Označuje, že data mohou být uložena v toku.                                                                                                      |
|      **Výběr**       |         (žádné)         | Objekt uzlu, parametr aktivity, Pin vstupní, výstupní spojky objektu toku |                                                                                                                          Spustí proces, který filtruje data. Tento proces lze definovat do jiného diagramu.                                                                                                                          |
|       **Řazení**       |         (žádné)         |       Objekt uzlu, parametr aktivity Pin vstupní, výstupní spojky        |                                                                                                                                                    – Jsou uložené jak více tokenů.                                                                                                                                                     |
|      **Ovládací prvek**      |         False          |                        Vstupní kód Pin, výstupní spojky                        |                                                                                                                            – Při hodnotě true se tok na tento PIN kód je tok řízení. Pokud má hodnotu false, je tok, který objekt.                                                                                                                            |
|         **Typ**         |         (žádné)         |       Uzel objektu Pin vstupní, výstupní spojky, parametr aktivity        |                              -Typ objektů přenášených.<br />-Typ může být primitivní typ, například tedy typu Integer nebo klasifikátor definovaný jinde v modelu. Pokud zadáte název typu, který není definován, se zobrazí v **nespecifikované typy** části Průzkumníku modelů UML.                               |
|     **Násobnost**     |           1            |                        Vstupní kód Pin, výstupní spojky                        | -Může být jedna hodnota nebo rozsah `[n..m]`.<br />-Dolní mez `n` – akce nelze spustit (pro vstupní kód pin) nebo zastavení (pro výstupní spojky), dokud nejsou `n` objekty čeká se na kód pin.<br />-Horní mez `m` – akce nemůže využívat nebo vytvářet více než `m` objektů v jedno provedení. \* znamená to, že není nijak omezený. |
|    **Transformace**    |         (žádné)         |                             Objekt toku                             |                                                                                                                      -Spustí proces, který transformuje data. Tento proces lze definovat do jiného diagramu.                                                                                                                       |
|     **Je vícesměrového vysílání**     |         False          |                             Objekt toku                             |                                                                                                                                 -Označuje, že může existovat několik příjemců objekty nebo komponenty.                                                                                                                                 |
|   **Je MultiReceive**    |         False          |                             Objekt toku                             |                                                                                                                                 -Označuje, že může existovat několik příjemců objekty nebo komponenty.                                                                                                                                 |
| **Je jedno provedení**  |         False          |                          Diagram činnosti                           |                                                                                                                                   -If nastaven, bylo nanejvýš jedno provedení tohoto diagramu současně.                                                                                                                                    |
  
## <a name="see-also"></a>Viz také  
 [Diagramy činnosti UML: referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)   
 [Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)



