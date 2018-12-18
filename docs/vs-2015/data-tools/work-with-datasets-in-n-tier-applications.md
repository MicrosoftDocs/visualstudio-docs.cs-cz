---
title: Práce s datovými sadami ve vícevrstvých aplikacích | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d05204edfd7c3cd5daecad3a1cb21ba5ba7e60d8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205969"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Práce s datovými sadami ve vícevrstvých aplikacích
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vícevrstvé datové aplikace * jsou datově orientovaných aplikací, které jsou rozdělené do několika logické vrstvy (nebo *úrovně*). Jinými slovy vícevrstvé datové aplikace je aplikace, která je rozdělena do několika projektů s vrstvě přístupu k datům, vrstvu obchodní logiky a prezentační vrstvou každý ve svém vlastním projektu. Další informace najdete v tématu [přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md).  
  
 Typové datové sady vylepšené tak, aby do samostatných projektů se můžou generovat třídy TableAdapter a datové sady. To poskytuje schopnost rychle samostatné aplikace a generovat vícevrstvých datových aplikací.  
  
 N-vrstvá podpora v typových datových sadách umožňuje iterativního vývoje návrhu, n vrstvá architektura aplikací. Odebere také nutnost ručně rozdělení kódu do více než jeden projekt. Začíná návrh datové vrstvě pomocí [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md). Jakmile budete připraveni, abyste při návrhu n vrstvé architektury aplikace, nastavte **projektu DataSet** vlastnosti datové sady, chcete-li vytvořit třídu dataset do samostatného projektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Rozdělování datových sad a objektů TableAdapter do různých projektů](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Popisuje, jak přesunout vytvořenou třídu datové sady z projektu, který obsahuje generované třídy TableAdapter a do nového projektu.  
  
 [Přidávání kódu do objektů TableAdapter ve vícevrstvých aplikacích](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Popisuje, jak generovat částečné třídy, ve které je možné přidat kód pro TableAdapter n vrstvou.  
  
 [Přidávání kódu do datových sad ve vícevrstvých aplikacích](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Popisuje, jak generovat částečné třídy, ve kterém můžete přidat kód pro n vrstvá datovou sadu.  
  
 [Přidávání ověřování do vícevrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Popisuje, kde je přidání kódu k ověření se měnícími daty.  
  
 [Návod: Vytvoření vícevrstvé datové aplikace](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Obsahuje podrobné pokyny pro vytvoření typové datové sady a oddělení kódu TableAdapter a datové sady do více projektů.  
  
 [Návod: Přidávání ověřování do vícevrstvé datové aplikace](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 Obsahuje podrobné pokyny pro přidání ověřování do aplikace, který byl vytvořen v návodu vícevrstvých datových aplikací.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)  
  
 [Hierarchická aktualizace](../data-tools/hierarchical-update.md)  
  
 [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)  
  
 [N-vrstvé a vzdálené aplikace s LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

