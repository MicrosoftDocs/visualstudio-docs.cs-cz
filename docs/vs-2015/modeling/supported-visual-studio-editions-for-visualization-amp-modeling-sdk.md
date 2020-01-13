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
ms.openlocfilehash: 227c2871f68545c9f9fe5fa1ea3ceee827ccdc6a
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917310"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Verze Visual Studia podporované pro Visualization &amp; Modeling SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto jsou seznamy edice sady Visual Studio, které jsou podporovány [!INCLUDE[dsl](../includes/dsl-md.md)] v prostředí pro vytváření a nasazení. Další informace o těchto vydáních najdete v tématu Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [středisko pro vývojáře](https://msdn.microsoft.com/vstudio/products/).

## <a name="authoring-edition"></a>Vytváření Edition
 Pokud chcete definovat DSL, musíte mít nainstalovaný následující komponenty:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Sada Visual Studio Visualization and Modeling SDK|[Stažení sady SDK pro modelování](https://www.microsoft.com/download/details.aspx?id=48148)|
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
