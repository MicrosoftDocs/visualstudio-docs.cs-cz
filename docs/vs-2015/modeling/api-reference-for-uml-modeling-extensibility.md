---
title: Reference k rozhraní API pro rozšíření modelování UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672798"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Referenční dokumentace k rozhraní API pro rozšíření modelování UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete napsat kód programu pro čtení a úpravy modelů, které vytvoříte pomocí sady Visual Studio. Reference k rozhraní API poskytuje informace o konkrétních třídách, které vám s tím pomůžou. Další informace, které jsou zaměřeny na úlohy, naleznete v tématech v části [rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md). Chcete-li zjistit, které verze aplikace Visual Studio podporují modely UML, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="assemblies"></a>Sestavení

|Assembly|Co vám to umožňuje|
|--------------|--------------------------------|
|Microsoft. VisualStudio. Uml. Interfaces. dll|-Číst a měnit prvky modelu, například IUseCase, IAssociation a tak dále.<br />-Procházení vztahů mezi prvky.<br /><br /> Obory názvů a typy odpovídají atributům, které jsou definovány ve specifikaci UML.|
|Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost. dll|-Vytvořit nové instance prvků modelu<br />– Přístup k obrazcům a diagramům a jejich úpravy|

## <a name="see-also"></a>Viz také
 Referenční dokumentace k rozhraní API [modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md) [pro sadu Modeling SDK pro Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
