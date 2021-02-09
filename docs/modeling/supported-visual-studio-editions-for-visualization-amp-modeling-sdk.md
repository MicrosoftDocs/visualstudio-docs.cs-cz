---
title: Podporovaná edice sady Visual Studio pro vizualizaci a modelování sady SDK
description: Seznamte se s edicemi sady Visual Studio, které jsou podporované pomocí nástrojů DSL v prostředí pro tvorbu a nasazení.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 14c23df472361fdee0bc657eb277d3a6bef4be73
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899686"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Verze Visual Studia podporované pro Visualization & Modeling SDK

Níže jsou uvedeny edice sady Visual Studio, které jsou podporovány [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] v prostředí pro tvorbu a nasazení. Další informace o těchto edicích najdete v centru pro [vývojáře](https://visualstudio.microsoft.com/)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Vytváření edice

K definování DSL musíte mít nainstalované následující součásti:

|Produkt|Odkaz ke stažení|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Sada SDK pro vizualizaci a modelování sady Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edice nasazení

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] podporuje následující konfigurace pro nasazení jazyků specifických pro doménu, které sestavíte:

- Visual Studio Enterprise

- Visual Studio Professional

- Distribuovatelný balíček balíčku Visual Studio Shell (integrovaný režim)

- Distribuovatelný balíček balíčku Visual Studio Shell (izolovaný režim)

> [!NOTE]
> Aby bylo možné aktivovat DSL na produktovém prostředí, musíte v manifestu rozšíření nastavit pole **podporované edice vs Edition** . Další informace najdete v tématu [nasazení Domain-Specific jazykových řešení](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))