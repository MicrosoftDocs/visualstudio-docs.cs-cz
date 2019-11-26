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
ms.openlocfilehash: 4fec3595ba7886f5ba979c35e9441ab108174726
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301343"
---
# <a name="validate-your-system-during-development"></a>Ověřování systému během vývoje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio může zajistit konzistenci softwaru v souladu s požadavky uživatelů a architekturou systému.

 Chcete-li zjistit, které verze sady Visual Studio podporují jednotlivé funkce, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Klíčové úlohy
 K ověření softwaru použijte následující úlohy.

|**Úlohy**|**Přidružená témata**|
|---------------|---------------------------|
|**Ujistěte se, že váš model je konzistentní:**<br /><br /> V závislosti na způsobu, jakým projekt používá a interpretuje modely, může být užitečné zakázat některé kombinace prvků. Můžete například omezit třídy UML tak, aby vždy měly názvy kompatibilní s [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. Můžete definovat omezení, například v rozšířeních [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|-   [ověření modelu UML](../modeling/validate-your-uml-model.md)<br />-   [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)|
|Ujistěte **se, že váš software splňuje požadavky uživatelů**:<br /><br /> Můžete použít požadavky a modely architektury, které vám pomůžou organizovat testy vašeho systému a jeho součástí. Tento postup pomáhá zajistit, že budete testovat požadavky, které jsou důležité pro uživatele a další zúčastněné strany, a pomůže vám rychle aktualizovat testy v případě změny požadavků.|-   [vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)|
|**Ujistěte se, že váš software zůstává v souladu s zamýšleným návrhem vašeho systému:**<br /><br /> Diagramy vrstev popisují zamýšlené závislosti mezi komponentami vaší aplikace. Během vývoje můžete ověřit, zda skutečné závislosti v kódu odpovídají zamýšlenému návrhu.|-   [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Externí prostředky

|**Kategorií**|**Odkazy**|
|------------------|---------------|
|**Videa**|![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kanál 9: Doug 7: porozumění kódu a návrh systému pomocí sady Visual Studio 2010](https://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kanál 9: architekt aplikace pomocí diagramu vrstev](https://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN postup I série: jak ověřit kód pomocí diagramů vrstev](https://go.microsoft.com/fwlink/?LinkID=214405)|
|**Fóra**|-   [nástrojů pro modelování sady Visual Studio pro vizualizaci &](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogy**|-   [blog sady Visual Studio ALM + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Technické články a deníky**|[Centrum architektury MSDN](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Viz také
 [Testování aplikace](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md) [požadavky uživatelů](../modeling/model-user-requirements.md) na [analýzu a modelování architektury](../modeling/analyze-and-model-your-architecture.md)
