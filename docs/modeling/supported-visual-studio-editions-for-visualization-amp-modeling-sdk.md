---
title: Verze Visual Studia podporované pro Visualization and Modeling SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 127b45ae6a0ab28d7f83ee41449d7846858ee4a9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591902"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Verze Visual Studia podporované pro Visualization & Modeling SDK

Toto jsou seznamy edice sady Visual Studio, které jsou podporovány [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] v prostředí pro vytváření a nasazení. Další informace o těchto vydáních najdete v tématu Microsoft Visual Studio [středisko pro vývojáře](https://visualstudio.microsoft.com/).

## <a name="authoring-edition"></a>Vytváření Edition

Pokud chcete definovat DSL, musíte mít nainstalovaný následující komponenty:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Sada Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edice nasazení

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] podporuje následující konfigurace pro jazyky specifické pro doménu, která bude sestavena nasazení:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (integrovaný režim) redistributable package Distribuovatelný balíček

- Visual Studio Shell (izolovaný režim) redistributable package Distribuovatelný balíček

> [!NOTE]
> Chcete-li DSL ke spuštění v prostředí produktu, je nutné nastavit **podporované edice VS** pole v manifestu rozšíření. Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Viz také:

- [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
