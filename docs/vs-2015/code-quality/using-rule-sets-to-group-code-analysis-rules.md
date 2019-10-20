---
title: Použití sad pravidel k seskupení pravidel analýzy kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603479"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Použití sad pravidel k seskupování pravidel analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při konfiguraci analýzy kódu v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vsPro](../includes/vspro-md.md)], si můžete vybrat ze seznamu předdefinovaných *sad pravidel*společnosti Microsoft. Sada pravidel je logické seskupení pravidel analýzy kódu, která vyhledávají cílené problémy a zvláštní podmínky. Můžete například použít sadu pravidel, která je navržena tak, aby kontrolovala kód veřejně dostupných rozhraní API, nebo můžete použít sadu pravidel, která obsahuje pouze minimální doporučená pravidla. Můžete také použít sadu pravidel, která zahrnuje všechna pravidla.

 Můžete přizpůsobit sadu pravidel přidáním nebo odstraněním pravidel nebo změnou pravidel, která se mají zobrazit v okně **Seznam chyb** jako upozornění nebo chyby. Sada vlastních pravidel může splnit potřebu konkrétního vývojového prostředí. Při přizpůsobování sady vlastních pravidel poskytuje stránka sady pravidel nástroje pro vyhledávání a filtrování, které vám s tím pomohou.

## <a name="common-tasks"></a>Obecné úlohy

|Úloha|Související obsah|
|----------|---------------------|
|**Získat praktickou praxi:** Pomocí nástrojů pro analýzu kódu můžete určit vlastní sadu pravidel k vyhledání a opravě problémů v jednoduché aplikaci .NET Framework.|-   [Návod: konfigurace a používání vlastní sady pravidel](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Konfigurace analýzy kódu pro projekt:** Vyberte existující sadu pravidel pro projekt, web nebo řešení.|-   [Postupy: konfigurace analýzy kódu pro projekt spravovaného kódu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [použití sad pravidel k určení C++ pravidel ke spuštění](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Postupy: konfigurace analýzy kódu pro webovou aplikaci ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Postupy: Určení sad pravidel pro více projektů v řešení](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Přizpůsobení sady pravidel:** Zadejte pravidla, která se mají použít pro váš projekt.|-   [vytváření vlastních sad pravidel](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|Seznamte **se s předdefinovanými sadami pravidel:** Zobrazí pravidla analýzy kódu, která tvoří předdefinované sady pravidel.|[Referenční dokumentace sady pravidel analýzy kódu](../code-quality/code-analysis-rule-set-reference.md) -   |
|**Integrace analýzy kódu s Team Foundation Server:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] zásady vracení se změnami umožňují vývojovým týmům zajistit, aby všechna vrácení se změnami kódu splňovala společnou sadu standardů pro analýzu kódu.|-   [Postupy: synchronizace sady pravidel projektu kódu se zásadou vrácení se změnami týmového projektu](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
