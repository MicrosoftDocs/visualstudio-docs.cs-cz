---
title: Výběr šablony řešení jazyka specifického pro doménu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d5eac08833c534e9da3a998687992cca6bc47c2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653684"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Výběr šablony řešení jazyka specifického pro doménu
Pokud chcete vytvořit řešení jazyka specifického pro doménu, vyberte jednu ze šablon řešení, které jsou k dispozici v průvodci návrháře jazyka specifického pro doménu. Když zvolíte šablonu, která se nejvíce podobá jazyku, který chcete vytvořit, můžete minimalizovat změny, které musíte udělat ve spouštěcím řešení.

 V průvodci návrháře jazyka specifického pro doménu jsou k dispozici následující šablony řešení.

|Vzhledu|Funkce|Popis|
|-|-|-|
|Diagramy tříd|– Obrazce oddílů<br />-Class – dědičnost<br />– Dědičnost vztahu<br />– Dědičnost obrazců<br />– Vlastnosti vztahu|Tuto šablonu řešení použijte v případě, že váš jazyk specifický pro doménu zahrnuje entity a vztahy, které mají vlastnosti. Tato šablona vytvoří jazyk specifický pro doménu, který se podobá diagramům tříd UML. Hlavní entity jsou třídy a rozhraní společně s vztahy přidružení, generalizace a implementace. Třída nebo rozhraní se zobrazí jako pole, které obsahuje seznam atributů.|
|Diagramy komponent|– Porty|Tuto šablonu řešení použijte v případě, že váš jazyk specifický pro doménu zahrnuje komponenty, tedy části softwarového systému. Tato šablona vytvoří jazyk specifický pro doménu, který se podobá diagramům komponent UML. Hlavními entitami jsou komponenty a porty, které se zobrazují jako malé tvary na vnějších komponentách.|
|Diagramy toku úloh|– Obrazce obrázků a geometrie<br />-   *plavecké dráhy*|Tuto šablonu řešení použijte v případě, že váš jazyk specifický pro doménu zahrnuje pracovní postupy, stavy nebo sekvence. Tato šablona vytvoří jazyk specifický pro doménu, který se podobá diagramům aktivity UML. Hlavní entita je aktivita a hlavním vztahem je přechod mezi aktivitami. Šablona obsahuje několik dalších prvků, jako je například počáteční stav, konečný stav a řádek synchronizace.|
|Minimální jazyk|-Jedna třída a tvar<br />– Jeden vztah a konektor|Tuto šablonu řešení použijte v případě, že váš jazyk specifický pro doménu nevypadá podobně jako ostatní šablony. Tato šablona vytvoří jazyk specifický pro doménu, který má dvě třídy a jeden vztah, který je reprezentován v sadě **nástrojů** jako **box** a **line**. Třída a vztah mají každý z nich ukázkovou vlastnost řetězce.|
|Návrhář Minimal DataGridView|– Malý model.<br />– Formulář Windows, který zobrazuje model.|Tuto šablonu použijte v případě, že chcete vytvořit aplikaci, ve které je linka DSL svázaná s formulářem Windows, a ne pomocí grafického návrháře.<br /><br /> Formulář, který funguje jako uživatelské rozhraní pro jazyk, je ve složce Dsl\UI.<br /><br /> Projekt byste měli před otevřením Návrháře formulářů sestavit.<br /><br /> Další informace najdete v tématu [Vytvoření jazyka specifického pro doménu založeného na model Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Návrhář s minimálním WPF|– Malý model<br />-Windows Presentation Foundation uživatelské rozhraní, které zobrazuje model|Tuto šablonu použijte v případě, že chcete vytvořit aplikaci, ve které je linka DSL svázána s uživatelským rozhraním WPF, nikoli pomocí grafického návrháře.<br /><br /> Návrhář uživatelského rozhraní je ve složce Dsl\UI.<br /><br /> Projekt byste měli sestavit před otevřením návrháře uživatelského rozhraní.<br /><br /> Další informace najdete v tématu [Vytvoření jazyka specifického pro doménu založeného na WPF](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Knihovna DSL|– Minimální knihovna|Tuto šablonu použijte v případě, že chcete vytvořit částečnou definici DSL, kterou je možné naimportovat do jiných definic DSL.|

## <a name="see-also"></a>Viz také

- [Přehled Nástrojů DSL](../modeling/overview-of-domain-specific-language-tools.md)
