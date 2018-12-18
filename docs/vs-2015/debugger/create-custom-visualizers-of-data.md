---
title: Vytváření vlastních Vizualizérů dat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8433af07b5f1315e73e6916e58123fcd14bddf0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792851"
---
# <a name="create-custom-visualizers-of-data"></a>Vytváření vlastních Vizualizérů dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vizualizéry jsou součástí [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uživatelské rozhraní ladicího programu. A *vizualizéru* vytvoří dialogové okno nebo jiné rozhraní pro zobrazení proměnné nebo objektu způsobem, který je vhodný k jeho datovému typu. Například HTML vizualizér interpretuje řetězec ve formátu HTML a výsledek zobrazí, jak se bude zobrazovat v okně prohlížeče; rastrový obrázek vizualizéru interpretuje struktura rastrový obrázek a zobrazí obrázek, který představuje. Některé vizualizéry umožňují snadno změnit také zobrazit data.  
  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Ladicí program obsahuje šest standardní vizualizéry. Toto jsou text, HTML, XML a JSON vizualizátory, nástroje pro všechny z nich pracovat na řetězcových objektů; vizualizéru stromu WPF, pro zobrazení vlastností objektu WPF vizuálního stromu; a vizualizér datasetu, který se dá použít pro objekty datové sady, zobrazení dat a DataTable. Další vizualizéry může být v budoucnosti k dispozici ke stažení od společnosti Microsoft a jsou k dispozici od třetích stran a komunity. Kromě toho můžete napsat vlastní vizualizéry a nainstalovat je do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ladicího programu.  
  
> [!NOTE]
>  V **Store** aplikací, jenom standardní text, HTML, XML a JSON vizualizéry jsou podporovány. Vizualizéry vlastní (uživatelem vytvořené) nejsou podporovány.  
  
 Vizualizéry jsou reprezentovány v ladicím programu ikonou lupy. Když se zobrazí ikona lupy v **datového tipu**, v okně proměnné ladicího programu, nebo v **QuickWatch** dialogové okno, můžete kliknout na ikonu lupy, vyberte odpovídající datovému typu vizualizéru odpovídajícího objektu.  
  
 Vizualizéry nepodporuje Compact Framework.  
  
> [!NOTE]
>  Ladicí program vizualizéry vyžadují, aby větší oprávnění než je povoleno hodnotou aplikace s částečnou důvěryhodností. V důsledku toho vizualizéry nenačtou, když se zastaví v kódu s částečným vztahem důvěryhodnosti. Chcete-li ladit pomocí vizualizéru, musíte spustit kód s úplným vztahem důvěryhodnosti.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [How to: Write a Visualizer](../debugger/how-to-write-a-visualizer.md)  
  
 [Návod: Zápis vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md)  
  
 [Postupy: Testování a ladění vizualizéru](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referenční dokumentace k rozhraní API vizualizéru](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Související oddíly  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)



