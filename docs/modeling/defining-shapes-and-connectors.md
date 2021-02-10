---
title: Definování obrazců a konektorů
description: Přečtěte si o několika základních typech tvarů, které můžete použít k zobrazení informací v diagramu v jazyce specifickém pro doménu (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 898bb0f3a923cfeac863b365e4746a63ccbc4c91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935323"
---
# <a name="define-shapes-and-connectors"></a>Definování obrazců a konektorů

K dispozici je několik základních typů tvarů, které lze použít k zobrazení informací v diagramu v jazyce specifickém pro doménu (DSL).

## <a name="basic-types-of-shapes-and-connectors"></a><a name="shapeTypes"></a> Základní typy obrazců a konektorů

Diagram DSL zobrazuje kolekci *obrazců* propojených pomocí spojnic nebo *spojnic*. Obvykle, ale ne vždy:

- Tvary jsou viditelné reprezentace prvků modelu.

- Konektory znázorňují referenční vztahy.

- Diagram představuje kořenovou instanci modelu.

- Vložení vztahů mezi prvky modelu se zobrazuje pomocí omezení. Například prvky představující porty komponent jsou vloženy do komponenty.

Tyto vzory nejsou vynutily, ale jsou lépe podporovány. Při návrhu DSL je potřeba mít na paměti, že návrh vztahů vložení by měl mít vliv na to, jak chcete model prezentovat na obrazovce. Naopak referenční vztahy by měly odrážet koncepty vaší obchodní domény.

K dispozici jsou následující typy tvarů:

|Typ obrazce|Description|
|-|-|
|Obrazec geometrie|Pravoúhlý nebo eliptický tvar pro obecné účely Text a ikonu dekoratéry můžete zobrazit v konkrétních polohách vzhledem k hranicím obrazce. Obrazce lze také vnořit do obrazců geometrie.|
|Obrazec oddílu|Obdélník obsahující záhlaví a oddíly, jako je třída UML. Každý oddíl může obsahovat seznam textových řádků.<br /><br /> Řádky typicky představují prvky vložené v rámci elementu reprezentovaného tvarem. Můžete například vytvořit DSL ze šablony řešení diagramy tříd.|
|Obrazec obrázku|Obrazec, který zobrazuje obrázek.|
|Obrazec portu|Malý obdélník navržený tak, aby se připojil k obrysu jiného obrazce. Obvykle se používá v modelech komponent.<br /><br /> Element modelu reprezentovaný portem je obvykle vložen do prvku reprezentovaného nadřazeným obrazcem. Můžete například vytvořit DSL pomocí šablony řešení součásti.<br /><br /> Ve výchozím nastavení se obrazec portu může vysouvat podél stran svého nadřazeného prvku. Můžete definovat pravidlo omezení pro omezení na konkrétní pozici.<br /><br /> Když je obrazec portu velmi malý a transparentní, můžete ho použít k poskytnutí pevného spojovacího bodu na povrchu jeho nadřazeného obrazce.|
|Plavecké|Plavecké dráhy rozdělí diagram do horizontálních nebo vertikálních segmentů. Plavecká dráha vždy zůstane pod ostatními tvary v diagramu.<br /><br /> Prvky modelu plavecké dráhy jsou obvykle nadřazené pro kořen modelu a ostatní prvky jsou na nich nadřazené. Příklad: vytvoření DSL ze šablony řešení Flow úlohy.|
|Konektory|Čáry vykreslené mezi obrazci typicky znázorňují referenční vztahy. Můžete nastavit možnosti pro vytvoření konektoru rovnou nebo lomené a pro různé typy šipek.|

## <a name="shape-inheritance"></a>Dědičnost obrazců

Obrazec může dědit z jiného obrazce. Avšak obrazce musí být stejného typu. Například pouze obrazec geometrie může dědit z obrazce geometrie. Zděděné obrazce mají oddíly a dekoratéry jejich základního tvaru. Konektory mohou dědit z konektorů.
