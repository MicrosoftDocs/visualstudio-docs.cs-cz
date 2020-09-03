---
title: Definování obrazců a konektorů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1fae548d-9288-4dd5-a24f-ff0d69c73628
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8304e573f64671936eee2ce922b904b41187aad2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669847"
---
# <a name="defining-shapes-and-connectors"></a>Definování obrazců a konektorů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K dispozici je několik základních typů tvarů, které lze použít k zobrazení informací v diagramu v jazyce specifickém pro doménu (DSL).

## <a name="basic-types-of-shapes-and-connectors"></a><a name="shapeTypes"></a> Základní typy obrazců a konektorů
 Diagram DSL zobrazuje kolekci *obrazců* propojených pomocí spojnic nebo *spojnic*.  Obvykle, ale ne vždy:

- Tvary jsou viditelné reprezentace prvků modelu.

- Konektory znázorňují referenční vztahy.

- Diagram představuje kořenovou instanci modelu.

- Vložení vztahů mezi prvky modelu se zobrazuje pomocí omezení. Například prvky představující porty komponent jsou vloženy do komponenty.

  Tyto vzory nejsou vynutily, ale jsou lépe podporovány. Při návrhu DSL je potřeba mít na paměti, že návrh vztahů vložení by měl mít vliv na to, jak chcete model prezentovat na obrazovce. Naopak referenční vztahy by měly odrážet koncepty vaší obchodní domény.

  K dispozici jsou následující typy tvarů:

|Typ obrazce|Popis|
|----------------|-----------------|
|Obrazec geometrie|Pravoúhlý nebo eliptický tvar pro obecné účely Text a ikonu dekoratéry můžete zobrazit v konkrétních polohách vzhledem k hranicím obrazce.<br /><br /> Chcete-li vnořovat obrazce uvnitř geometrických tvarů, viz [vnořování tvarů](../modeling/nesting-shapes.md).|
|Obrazec oddílu|Obdélník obsahující záhlaví a oddíly, jako je třída UML. Každý oddíl může obsahovat seznam textových řádků.<br /><br /> Řádky typicky představují prvky vložené v rámci elementu reprezentovaného tvarem. Můžete například vytvořit DSL ze šablony řešení diagramy tříd.|
|Obrazec obrázku|Obrazec, který zobrazuje obrázek.|
|Obrazec portu|Malý obdélník navržený tak, aby se připojil k obrysu jiného obrazce. Obvykle se používá v modelech komponent.<br /><br /> Element modelu reprezentovaný portem je obvykle vložen do prvku reprezentovaného nadřazeným obrazcem. Můžete například vytvořit DSL pomocí šablony řešení součásti.<br /><br /> Ve výchozím nastavení se obrazec portu může vysouvat podél stran svého nadřazeného prvku. Můžete definovat pravidlo omezení pro omezení na konkrétní pozici.<br /><br /> Když je obrazec portu velmi malý a transparentní, můžete ho použít k poskytnutí pevného spojovacího bodu na povrchu jeho nadřazeného obrazce.|
|Plavecké|Plavecké dráhy rozdělí diagram do horizontálních nebo vertikálních segmentů. Plavecká dráha vždy zůstane pod ostatními tvary v diagramu.<br /><br /> Prvky modelu plavecké dráhy jsou obvykle nadřazené pro kořen modelu a ostatní prvky jsou na nich nadřazené. Příklad: vytvoření DSL ze šablony řešení Flow úlohy.|
|Konektory|Čáry vykreslené mezi obrazci typicky znázorňují referenční vztahy. Můžete nastavit možnosti pro vytvoření konektoru rovnou nebo lomené a pro různé typy šipek.|

## <a name="shape-inheritance"></a><a name="shapeInheritance"></a> Dědičnost obrazců
 Obrazec může dědit z jiného obrazce. Avšak obrazce musí být stejného typu. Například pouze obrazec geometrie může dědit z obrazce geometrie. Zděděné obrazce mají oddíly a dekoratéry jejich základního tvaru. Konektory mohou dědit z konektorů.
