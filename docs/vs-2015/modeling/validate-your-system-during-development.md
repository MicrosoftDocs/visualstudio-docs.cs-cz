---
title: Ověření systému během vývoje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1beeef572282a642e4a989086ac0fd228409fec
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586265"
---
# <a name="validate-your-system-during-development"></a>Ověřování systému během vývoje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio může zajistit konzistenci softwaru v souladu s požadavky uživatelů a architekturou systému.

 Chcete-li zjistit, které verze sady Visual Studio podporují jednotlivé funkce, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Klíčové úlohy
 K ověření softwaru použijte následující úlohy.

|**Úlohy**|**Související témata**|
|---------------|---------------------------|
|**Ujistěte se, že váš model je konzistentní:**<br /><br /> V závislosti na způsobu, jakým projekt používá a interpretuje modely, může být užitečné zakázat některé kombinace prvků. Můžete například omezit třídy UML tak, aby vždy měly [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]názvy kompatibilní. V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšířeních můžete definovat omezení, jako jsou tato.|-   [Ověření modelu UML](../modeling/validate-your-uml-model.md)<br />-   [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)|
|Ujistěte **se, že váš software splňuje požadavky uživatelů**:<br /><br /> Můžete použít požadavky a modely architektury, které vám pomůžou organizovat testy vašeho systému a jeho součástí. Tento postup pomáhá zajistit, že budete testovat požadavky, které jsou důležité pro uživatele a další zúčastněné strany, a pomůže vám rychle aktualizovat testy v případě změny požadavků.|-   [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)|
|**Ujistěte se, že váš software zůstává v souladu s zamýšleným návrhem vašeho systému:**<br /><br /> Diagramy vrstev popisují zamýšlené závislosti mezi komponentami vaší aplikace. Během vývoje můžete ověřit, zda skutečné závislosti v kódu odpovídají zamýšlenému návrhu.|-   [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|------------------|---------------|
|**Videa**|![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kanál 9: Doug 7: porozumění kódu a návrh systému pomocí sady Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kanál 9: architekt aplikace pomocí diagramu vrstev](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-5-Architecting-an-Application)<br /><br /> ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN postup I série: jak ověřit kód pomocí diagramů vrstev](https://msdn.microsoft.com/vstudio/gg501755)|
|**Fóra**|-   [Nástroje pro vizualizaci sady Visual Studio & modelování](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogy**|-   [Blog sady Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Technické články a deníky**|[Centrum architektury MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Viz také
 [Testování aplikace](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md) [požadavky uživatelů](../modeling/model-user-requirements.md) na [analýzu a modelování architektury](../modeling/analyze-and-model-your-architecture.md)
