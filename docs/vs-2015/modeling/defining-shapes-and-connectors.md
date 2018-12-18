---
title: Definování obrazců a konektorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fae548d-9288-4dd5-a24f-ff0d69c73628
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 61cd27b307b4761e3f7773f91583965466892285
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812943"
---
# <a name="defining-shapes-and-connectors"></a>Definování obrazců a konektorů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Existuje několik typů základní tvary, které můžete použít k zobrazení informací v diagramu v jazyka specifického pro doménu (DSL).  
  
##  <a name="shapeTypes"></a> Základní typy obrazců a konektorů  
 DSL diagram ukazuje kolekci *tvary* vzájemně propojena těmito řádky nebo *konektory*.  Obvykle, ale ne vždy:  
  
- Tvary jsou viditelné reprezentace prvky modelu.  
  
- Konektory představují vztahy odkazu.  
  
- Diagram představuje instanci kořenovém modelu.  
  
- Vkládání vztahy mezi elementy modelu jsou uvedeny ve členství ve skupině. Například prvků, která představuje součást porty jsou vložené v komponentě.  
  
  Tyto modely nejsou vynucená, ale jsou silněji podporovány. Při návrhu DSL berte v úvahu, který návrh vztahů obsažení by měl být ovlivněno způsob, jak mají být k dispozici modelu na obrazovce. Naopak referenční stavy by měly odrážet koncepty obchodní domény.  
  
  K dispozici jsou následující typy tvarů:  
  
|Obrazec typu|Popis|  
|----------------|-----------------|  
|Obrazec geometrie|Obecné účely obrazec obdélníkové nebo elipsy. Text a ikona dekoratéry můžete zobrazit v konkrétní pozici vzhledem k hranicím tvaru.<br /><br /> Vnoření obrazců uvnitř obrazce geometrie, naleznete v tématu [vnořování obrazců](../modeling/nesting-shapes.md).|  
|Obrazec oddílu|Obdélník, který obsahuje hlavičky a obory, jako je třída UML. Každý oddíl může obsahovat seznam řádků textu.<br /><br /> Řádky představují obvykle prvky vložené v rámci elementu reprezentována tvaru. Příklad vytvoření DSL ze šablony řešení diagramy tříd.|  
|Obrazec obrázku|Obrazec, který zobrazuje obrázek.|  
|Tvar portu|Malý obdélník navržené tak, aby připojení k osnovy jiný tvar. Obvykle se používá v modelech komponenty.<br /><br /> Prvek modelu, který je reprezentován port je obvykle vložený pod element reprezentovaný nadřazeného obrazce. Příklad vytvoření DSL pomocí šablony řešení komponenty.<br /><br /> Ve výchozím nastavení můžete snímek obrazec portu spolu strany svého nadřazeného objektu. Můžete definovat pravidla hranice omezit na konkrétní pozici.<br /><br /> Tím, že obrazec portu velmi malé a transparentní, můžete ho poskytnout pevné spojovacího bodu na povrchu nadřazeného obrazce.|  
|Plaveckých drah|Plaveckých drah diagramu rozdělit do segmentů vodorovně nebo svisle. Plavecké stále pod tvary v diagramu.<br /><br /> Obvykle jsou prvky modelu plavecké nadřazena na kořen modelu a další prvky jsou nadřazena na ně. Příklad vytvoření DSL ze šablony řešení tok úkolů.|  
|Konektory|Čáry dekorace mezi tvary obvykle představují vztahy odkazu. Můžete nastavit možnosti, aby konektor přímá nebo Pravoúhlá a mají různé typy šipky.|  
  
##  <a name="shapeInheritance"></a> Tvar dědičnosti  
 Obrazce mohou dědit z jiného obrazce. Tvary však musí být stejného druhu. Například může dědit pouze obrazec geometrie z obrazec geometrie. Zděděné tvary mít oddíly a dekorátory jejich základní obrazec. Konektory mohou dědit z konektorů.



