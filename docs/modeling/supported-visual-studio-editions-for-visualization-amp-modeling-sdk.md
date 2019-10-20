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
ms.openlocfilehash: 1fdfe698096da53abf28aa583c816d9238810333
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609335"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Verze Visual Studia podporované pro Visualization & Modeling SDK

Níže jsou uvedeny edice sady Visual Studio, které jsou podporovány [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] v prostředí pro tvorbu a nasazení. Další informace o těchto edicích najdete v centru pro [vývojáře](http://go.microsoft.com/fwlink/?LinkId=75628)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Vytváření edice

K definování DSL musíte mít nainstalované následující součásti:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Sada SDK pro vizualizaci a modelování sady Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

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