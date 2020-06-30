---
title: Podporované edice sady Visual Studio pro vizualizaci a modelování sady SDK | Microsoft Docs
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
ms.openlocfilehash: 3eebefeab6b78955b03d4546a60dd811f5e9ae4e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547651"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Verze Visual Studia podporované pro Visualization &amp; Modeling SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Níže jsou uvedeny edice sady Visual Studio, které jsou podporovány [!INCLUDE[dsl](../includes/dsl-md.md)] v prostředí pro tvorbu a nasazení. Další informace o těchto edicích najdete v tématu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [středisko pro vývojáře](https://msdn.microsoft.com/vstudio/products/)společnosti Microsoft.

## <a name="authoring-edition"></a>Vytváření edice
 K definování DSL musíte mít nainstalované následující součásti:

|Produkt|Odkaz ke stažení|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Sada SDK pro vizualizaci a modelování sady Visual Studio|[Stažení sady SDK pro modelování](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Edice nasazení
 [!INCLUDE[dsl](../includes/dsl-md.md)]podporuje následující konfigurace pro nasazení jazyků specifických pro doménu, které sestavíte:

- Visual Studio Enterprise

- Visual Studio Professional

- Distribuovatelný balíček balíčku Visual Studio Shell (integrovaný režim)

- Distribuovatelný balíček balíčku Visual Studio Shell (izolovaný režim)

> [!NOTE]
> Aby bylo možné aktivovat DSL na produktovém prostředí, musíte v manifestu rozšíření nastavit pole **podporované edice vs Edition** . Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Viz také
 [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
