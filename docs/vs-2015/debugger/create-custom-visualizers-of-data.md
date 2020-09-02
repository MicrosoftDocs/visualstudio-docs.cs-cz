---
title: Vytvořit vlastní vizualizace dat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 50df868f0e01d49d4c49bccae32d743d5291a066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820662"
---
# <a name="create-custom-visualizers-of-data"></a>Vytváření vlastních vizualizací dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroje pro vizualizaci jsou komponenty [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uživatelského rozhraní ladicího programu. *Vizualizér* vytvoří dialogové okno nebo jiné rozhraní pro zobrazení proměnné nebo objektu způsobem, který je vhodný pro svůj datový typ. Například Vizualizér HTML interpretuje řetězec jazyka HTML a zobrazí výsledek tak, jak by se zobrazil v okně prohlížeče. Vizualizér rastrového obrázku interpretuje strukturu rastrového obrázku a zobrazuje obrázek, který představuje. Některé vizualizace umožňují upravovat a zobrazovat data.  
  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]Ladicí program obsahuje šest standardních vizualizací. Jedná se o textové, HTML, XML a vizualizace, které fungují na objektech řetězců. Vizualizér stromu WPF pro zobrazení vlastností vizuálního stromu objektu WPF; a Vizualizér datových sad, který funguje pro objekty DataSet, DataView a DataTable. Další vizualizace mohou být k dispozici ke stažení od společnosti Microsoft Corporation v budoucnu a jsou k dispozici od třetích stran a komunity. Kromě toho můžete napsat vlastní vizualizace a nainstalovat je v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ladicím programu.  
  
> [!NOTE]
> V aplikacích pro **Store** se podporují jenom standardní texty, HTML, XML a vizualizace JSON. Vlastní (uživatelsky vytvořené) vizualizace se nepodporují.  
  
 Vizualizace jsou reprezentovány v ladicím programu pomocí ikony lupy. Když se v **DataTip**zobrazí ikona lupy, v okně proměnné ladicího programu nebo v dialogovém okně **QuickWatch** můžete kliknout na zvětšovací sklo a vybrat Vizualizér odpovídající datovému typu odpovídajícího objektu.  
  
 V kompaktním rozhraní se nepodporují vizualizace.  
  
> [!NOTE]
> Nástroje pro vizualizace ladicího programu vyžadují větší oprávnění, než povoluje aplikace s částečnou důvěryhodností. V důsledku toho se vizualizace nenačte, když jste zastavili kód s částečnou důvěryhodností. Chcete-li provést ladění pomocí vizualizér, je nutné spustit kód s úplným vztahem důvěryhodnosti.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Zápis vizualizéru](../debugger/how-to-write-a-visualizer.md)  
  
 [Návod: Zápis vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Postupy: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md)  
  
 [Postupy: testování a ladění Vizualizér](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referenční dokumentace rozhraní API vizualizéru](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Související oddíly  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
