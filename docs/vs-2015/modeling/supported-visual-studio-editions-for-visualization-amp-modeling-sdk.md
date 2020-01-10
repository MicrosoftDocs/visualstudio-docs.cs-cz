---
title: Verze Visual Studia podporované pro Visualization and Modeling SDK | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0692efefcc92e3316ccf725c586fc6566b09a6ef
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850781"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Verze Visual Studia podporované pro Visualization &amp; Modeling SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto jsou seznamy edice sady Visual Studio, které jsou podporovány [!INCLUDE[dsl](../includes/dsl-md.md)] v prostředí pro vytváření a nasazení. Další informace o těchto vydáních najdete v tématu Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [středisko pro vývojáře](https://msdn.microsoft.com/vstudio/products/).

## <a name="authoring-edition"></a>Vytváření Edition
 Pokud chcete definovat DSL, musíte mít nainstalovaný následující komponenty:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://www.visualstudio.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](https://docs.microsoft.com/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Sada Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)|

## <a name="deployment-editions"></a>Edice nasazení
 [!INCLUDE[dsl](../includes/dsl-md.md)] podporuje následující konfigurace pro jazyky specifické pro doménu, která bude sestavena nasazení:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (integrovaný režim) redistributable package Distribuovatelný balíček

- Visual Studio Shell (izolovaný režim) redistributable package Distribuovatelný balíček

> [!NOTE]
> Chcete-li DSL ke spuštění v prostředí produktu, je nutné nastavit **podporované edice VS** pole v manifestu rozšíření. Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Viz také
 [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
