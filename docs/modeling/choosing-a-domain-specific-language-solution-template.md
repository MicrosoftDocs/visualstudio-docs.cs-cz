---
title: Výběr šablony řešení jazyka specifického pro doménu
description: Zjistěte, jak vytvořit řešení jazyka specifického pro doménu výběrem jedné ze šablon řešení, které jsou k dispozici v průvodci pro návrháře jazyka Domain-Specific.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23629c2503fd14a758cf3f68f2576db601dd39cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861852"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Výběr šablony řešení jazyka specifického pro doménu
Pokud chcete vytvořit řešení jazyka specifického pro doménu, vyberte jednu ze šablon řešení, které jsou k dispozici v průvodci pro návrháře jazyka Domain-Specific. Když zvolíte šablonu, která se nejvíce podobá jazyku, který chcete vytvořit, můžete minimalizovat změny, které musíte udělat ve spouštěcím řešení.

 V průvodci návrháře jazyka Domain-Specific jsou k dispozici následující šablony řešení.

|Template (Šablona)|Funkce|Description|
|-|-|-|
|Diagramy tříd|– Obrazce oddílů<br />-Class – dědičnost<br />– Dědičnost vztahu<br />– Dědičnost obrazců<br />– Vlastnosti vztahu|Tuto šablonu řešení použijte v případě, že váš jazyk specifický pro doménu zahrnuje entity a vztahy, které mají vlastnosti. Tato šablona vytvoří jazyk specifický pro doménu, který se podobá diagramům tříd UML. Hlavní entity jsou třídy a rozhraní společně s vztahy přidružení, generalizace a implementace. Třída nebo rozhraní se zobrazí jako pole, které obsahuje seznam atributů.|
|Diagramy komponent|– Porty|Tuto šablonu řešení použijte v případě, že váš jazyk specifický pro doménu zahrnuje komponenty, tedy části softwarového systému. Tato šablona vytvoří jazyk specifický pro doménu, který se podobá diagramům komponent UML. Hlavními entitami jsou komponenty a porty, které se zobrazují jako malé tvary na vnějších komponentách.|
|Diagramy toku úloh|– Obrazce obrázků a geometrie<br />-   *Plavecké*|Tuto šablonu řešení použijte v případě, že váš jazyk specifický pro doménu zahrnuje pracovní postupy, stavy nebo sekvence. Tato šablona vytvoří jazyk specifický pro doménu, který se podobá diagramům aktivity UML. Hlavní entita je aktivita a hlavním vztahem je přechod mezi aktivitami. Šablona obsahuje několik dalších prvků, jako je například počáteční stav, konečný stav a řádek synchronizace.|
|Minimální jazyk|-Jedna třída a tvar<br />– Jeden vztah a konektor|Tuto šablonu řešení použijte v případě, že váš jazyk specifický pro doménu nevypadá podobně jako ostatní šablony. Tato šablona vytvoří jazyk specifický pro doménu, který má dvě třídy a jeden vztah, který je reprezentován v sadě **nástrojů** jako **box** a **line**. Třída a vztah mají každý z nich ukázkovou vlastnost řetězce.|
|Návrhář Minimal DataGridView|– Malý model.<br />– Formulář Windows, který zobrazuje model.|Tuto šablonu použijte v případě, že chcete vytvořit aplikaci, ve které je linka DSL svázaná s formulářem Windows, a ne pomocí grafického návrháře.<br /><br /> Formulář, který funguje jako uživatelské rozhraní pro jazyk, je ve složce Dsl\UI.<br /><br /> Projekt byste měli před otevřením Návrháře formulářů sestavit.<br /><br /> Další informace najdete v tématu [vytvoření Domain-Specificho jazyka Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Návrhář s minimálním WPF|– Malý model<br />-Windows Presentation Foundation uživatelské rozhraní, které zobrazuje model|Tuto šablonu použijte v případě, že chcete vytvořit aplikaci, ve které je linka DSL svázána s uživatelským rozhraním WPF, nikoli pomocí grafického návrháře.<br /><br /> Návrhář uživatelského rozhraní je ve složce Dsl\UI.<br /><br /> Projekt byste měli sestavit před otevřením návrháře uživatelského rozhraní.<br /><br /> Další informace najdete v tématu [vytvoření WPF-Basedho Domain-Specificho jazyka](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Knihovna DSL|– Minimální knihovna|Tuto šablonu použijte v případě, že chcete vytvořit částečnou definici DSL, kterou je možné naimportovat do jiných definic DSL.|

## <a name="see-also"></a>Viz také

- [Přehled Nástrojů DSL](../modeling/overview-of-domain-specific-language-tools.md)
