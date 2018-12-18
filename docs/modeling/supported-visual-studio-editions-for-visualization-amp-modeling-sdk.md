---
title: Verze Visual Studia podporované pro Visualization and Modeling SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 65014d8c697adbf5fb8e13d28708090360bb9c17
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049947"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Verze Visual Studia podporované pro Visualization & Modeling SDK

Toto jsou seznamy edice sady Visual Studio, které jsou podporovány [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] v prostředí pro vytváření a nasazení. Další informace o těchto vydáních najdete v tématu Microsoft Visual Studio [středisko pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Vytváření Edition

Pokud chcete definovat DSL, musíte mít nainstalovaný následující komponenty:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edice nasazení

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] podporuje následující konfigurace pro jazyky specifické pro doménu, která bude sestavena nasazení:

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Visual Studio Shell (integrovaný režim) redistributable package Distribuovatelný balíček

-   Visual Studio Shell (izolovaný režim) redistributable package Distribuovatelný balíček

> [!NOTE]
> Chcete-li DSL ke spuštění v prostředí produktu, je nutné nastavit **podporované edice VS** pole v manifestu rozšíření. Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Viz také:

- [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)