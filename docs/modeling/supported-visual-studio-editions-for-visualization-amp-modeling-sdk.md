---
title: Podporovaná edice sady Visual Studio pro vizualizaci a modelování sady SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efe452f059d7184e1f7c87fddd6bdc6c213ece8a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983730"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Verze Visual Studia podporované pro Visualization & Modeling SDK

Níže jsou uvedeny edice sady Visual Studio, které jsou podporovány [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] v prostředí pro tvorbu a nasazení. Další informace o těchto edicích najdete v centru pro [vývojáře](https://visualstudio.microsoft.com/)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Vytváření edice

K definování DSL musíte mít nainstalované následující součásti:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Sada SDK pro vizualizaci a modelování sady Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edice nasazení

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] podporuje následující konfigurace pro nasazení jazyků specifických pro doménu, které sestavíte:

- Visual Studio Enterprise

- Visual Studio Professional

- Distribuovatelný balíček balíčku Visual Studio Shell (integrovaný režim)

- Distribuovatelný balíček balíčku Visual Studio Shell (izolovaný režim)

> [!NOTE]
> Aby bylo možné aktivovat DSL na produktovém prostředí, musíte v manifestu rozšíření nastavit pole **podporované edice vs Edition** . Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Viz také:

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)