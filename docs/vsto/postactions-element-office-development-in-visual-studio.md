---
title: '&lt;postActions – &gt; element (vývoj pro Office)'
description: Element postActions oboru názvů vstav3 obsahuje všechny prvky postAction, které popisují akce po nasazení, které se spouštějí po instalaci řešení Office.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5c4a66e270cd446996884262d380df0f7384f54f
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470037"
---
# <a name="ltpostactionsgt-element-office-development"></a>&lt;postActions – &gt; element (vývoj pro Office)
  `postActions`Element `vstav3` oboru názvů obsahuje všechny `postAction` prvky, které popisují akce po nasazení, které se spouštějí po instalaci řešení Office.

## <a name="syntax"></a>Syntax

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `postActions`Element je nepovinný a je v `vstav3` oboru názvů. `postActions`V manifestu aplikace je definován pouze jeden prvek.

 `postActions`Element nemá žádné atributy.

 `postActions` má následující element.

### <a name="postaction"></a>postAction
 Nepovinný parametr. Role `postAction` elementu v `vstav3` oboru názvů je definována v [&#60;postAction&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Příklad akce po nasazení

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `postActions` prvek v manifestu aplikace pro řešení Office nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstav3:postActions>
  <vstav3:postAction>
    <vstav3:entryPoint
      class="PostDeploymentAction.PostDeploymentActionSample">
      <assemblyIdentity
        name="PostDeploymentAction"
        version="1.0.0.0"
        language="neutral"
        processorArchitecture="msil" />
    </vstav3:entryPoint>
    <vstav3:postActionData>
    </vstav3:postActionData>
  </vstav3:postAction>
</vstav3:postActions>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
