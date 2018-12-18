---
title: Výběr šablony řešení jazyka specifického pro doménu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 618a26740759431ffe9de2b6ed5b51ffb32ea69e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268480"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Výběr šablony řešení jazyka specifického pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K vytváření řešení jazyka specifického pro doménu, vyberte jednu z šablon řešení, které jsou k dispozici v Průvodci návrháře jazyka specifického pro doménu. Výběrem šablony, která nejlépe odpovídá jazyk, ve kterém chcete vytvořit, můžete minimalizovat úpravy, které je nutné provést počáteční řešení.  
  
 Následující šablony řešení jsou k dispozici v Průvodci návrháře jazyka specifického pro doménu.  
  
> [!NOTE]
>  Účel šablony je poskytnout výchozí DSL. Šablony s názvem třídy a komponenty diagramy nejsou úplné diagramy UML. Pokud chcete vytvořit UML model, vezměte v úvahu nástroje, které poskytují sadu diagramy, které jsou integrované jednoho modelu pomocí modelování UML. Jsou rozšiřitelný a je možné integrovat se službou vašeho DSL pomocí ModelBus. Další informace najdete v tématu [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md).  
  
|Šablony|Funkce|Popis|  
|--------------|--------------|-----------------|  
|Diagramy tříd|-Oddíl obrazce<br />– Dědičnost třída<br />-Vztah dědičnosti<br />– Obrazec dědičnosti<br />– Vlastnosti relace|Pomocí této šablony řešení jazyka specifického pro doménu obsahuje entity a vztahy, které mají vlastnosti. Tato šablona vytvoří jazyka specifického pro doménu, která se podobá diagramů tříd UML. Hlavní entity jsou třídy a rozhraní, společně s relací asociace, generalizace a implementaci. Třídy nebo rozhraní se zobrazí jako pole, která obsahuje seznam atributů.|  
|Diagramy komponent|-Porty|Pomocí této šablony řešení jazyka specifického pro doménu obsahuje součásti, tedy součástí softwaru system. Tato šablona vytvoří jazyka specifického pro doménu, která se podobá diagramy komponent UML. Hlavní entity jsou komponenty a porty, které se zobrazí jako malá tvary na povrchu komponenty.|  
|Diagramy toku úkolů|– Image a geometrických obrazců<br />-   *Plaveckých drah*|Pomocí této šablony řešení jazyka specifického pro doménu obsahuje pracovní postupy, stavů nebo pořadí. Tato šablona vytvoří jazyka specifického pro doménu, která se podobá diagramy činnosti UML. Hlavní entity je aktivita a hlavní relace je přechod mezi aktivitami. Šablona obsahuje několik elementů jako počáteční stav, konečného stavu a panel synchronizace.|  
|Minimální jazykový|-Jednu třídu a obrazec<br />– Jeden vztah a spojnici|Pomocí této šablony řešení jazyka specifického pro doménu není vypadat jako další šablony-li. Tato šablona vytvoří jazyka specifického pro doménu, která má dvě třídy a jedna relace, které jsou reprezentovány v **nástrojů** jako **pole** a **řádku**. Třídy a relace mít vlastnost řetězce příklad.|  
|Minimální návrháři formuláře Windows|-Malá modelu.<br />– Windows formulář, který zobrazuje model.|Tuto šablonu použijte, pokud chcete sestavit aplikaci, ve kterém je DSL vázán na formuláři Windows, nikoli grafického návrháře.<br /><br /> Ve složce Dsl\UI je formulář, který funguje jako uživatelské rozhraní pro jazyk.<br /><br /> Projekt má sestavit před otevřením Návrhář formulářů.<br /><br /> Další informace najdete v tématu [vytvoření jazyka specifického pro doménu Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Minimální WPF Designer|-Malá modelu<br />– Windows Presentation Foundation uživatelské rozhraní, které zobrazuje model|Tuto šablonu použijte, pokud chcete k sestavení aplikace 00Z DSL vázán na uživatelské rozhraní WPF, nikoli grafického návrháře.<br /><br /> Návrhář uživatelského rozhraní je ve složce Dsl\UI.<br /><br /> Projekt má sestavit před otevřením návrháře uživatelského rozhraní.<br /><br /> Další informace najdete v tématu [vytvoření jazyka specifického pro doménu WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|Knihovna DSL, která|-Minimální knihovny|Tuto šablonu použijte, pokud chcete sestavit částečnou definici DSL, která se dají importovat do jiné definice DSL.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled Nástrojů DSL](../modeling/overview-of-domain-specific-language-tools.md)



