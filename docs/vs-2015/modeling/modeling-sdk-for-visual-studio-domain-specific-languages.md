---
title: Sada Modeling SDK – jazyky domény | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 79
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0673f7511276799804dc327bab67637f3fc450b7
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850101"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Sada Modeling SDK pro sadu Visual Studio – jazyky domény
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí sady SDK modelování pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (MSDK) můžete vytvořit výkonné založené na modelu vývojářské nástroje, které můžete integrovat do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jako příklad jsou pomocí MSDK vytvořeny nástroje UML. Stejným způsobem můžete vytvořit jednu nebo několik definic modelu a integrovat je do sady nástrojů.

 V centru MSDK je definice modelu, který je vytvořen, aby představoval pojmy v oblasti vašeho podnikání. Je možné ohraničit model s širokou škálu nástrojů, jako je diagramatické zobrazení, možnost generování kódů a jiných artefaktů a příkazů pro transformaci modelu a možnost interakce s kódem a dalšími objekty v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Při vývoji lze model kombinovat s dalšími modely a nástroji, jež tvoří výkonnou sadu nástrojů, které jsou zaměřeny na vývoj.

 MSDK umožňuje rychlý vývoj modelu ve formě jazyka specifického pro doménu (DSL). Začínáte se speciálním editorem, kterým definujete schéma nebo abstraktní syntaxi a grafickou notaci. Z této definice vygeneruje VMSDK následující položky:

- Model implementace s rozhraním API silného typu, který je spuštěn v obchodě založeném na transakcích.

- Průzkumník založený na stromové architektuře.

- Grafický editor, ve kterém uživatelé mohou zobrazit model nebo jeho části, které definujete.

- Metody serializace, které uloží modely ve formátu XML pro čtení.

- Zařízení pro generování programového kódu a jiných artefaktů pomocí šablonování textu.

  Můžete přizpůsobit a rozšířit všechny tyto funkce. Vaše rozšíření jsou integrována tak, že můžete i nadále aktualizovat definici DSL a znovu generovat funkce bez ztráty rozšíření.

## <a name="samples-and-the-latest-information"></a>Ukázky a nejnovější informace
 [Stáhněte si modelování SDK pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

 [Ukázky](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) pro modelování SDK pro Visual Studio.

 Návod s pokročilými technikami a řešení potíží najdete na webu [fórum Visual Studio DSL & modelování rozšiřitelnosti nástrojů](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx).

## <a name="in-this-section"></a>V tomto oddílu
 [Začínáme s jazyky specifickými pro doménu](../modeling/getting-started-with-domain-specific-languages.md)

 [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)

 [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)

 [Přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [Ověřování v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md)

 [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)

 [Porozumění kódu DSL](../modeling/understanding-the-dsl-code.md)

 [Přizpůsobení souborového úložiště a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md)

 [Nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md)

 [Vytvoření jazyka specifického pro doménu založeného na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [Vytvoření jazyka specifického pro doménu založeného na WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [Postupy: Rozšíření Návrháře DSL](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Verze sady Visual Studio podporované pro Visualization & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [Postupy: Migrace jazyka specifického pro doménu na novou verzi](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Referenční dokumentace rozhraní API k sadě Modeling SDK pro Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
