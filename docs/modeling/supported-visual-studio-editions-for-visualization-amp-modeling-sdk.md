---
title: Podporované Visual Studio edice pro sadu Visualization and Modeling SDK
description: Seznamte se s Visual Studio, které jsou podporovány nástroji DSL v prostředích pro vytváření a nasazení.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8435f37ebe68e954af135be0f513247191ea8a9
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386394"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Verze Visual Studia podporované pro Visualization & Modeling SDK

Následuje seznam edicí Visual Studio, které jsou podporované v prostředích pro vytváření obsahu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] a nasazení. Další informace o těchto edicích najdete na webu Microsoft Visual Studio [developer Center.](https://visualstudio.microsoft.com/)

## <a name="authoring-edition"></a>Authoring Edition

Pokud chcete definovat DSL, musíte mít nainstalované následující komponenty:

|Produkt|Odkaz ke stažení|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Visual Studio vizualizace a modelování SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edice nasazení

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] podporuje následující konfigurace pro nasazení jazyků specifických pro doménu, které sestavíte:

- Visual Studio Enterprise

- Visual Studio Professional

- distribuovatelný balíček Visual Studio Shell (integrovaný režim)

- distribuovatelný balíček Visual Studio Shellu (v izolovaném režimu)

> [!NOTE]
> Pokud chcete, aby dsl mohl běžet na produktu Shell, musíte v manifestu rozšíření nastavit pole Supported VS Edition (Podporovaná edice **VS).** Další informace najdete v tématu [Nasazení Domain-Specific jazyka](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Viz také

- [Nástroje DSL glosář](/previous-versions/bb126564(v=vs.100))