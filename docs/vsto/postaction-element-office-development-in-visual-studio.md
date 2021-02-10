---
title: '&lt;postAction – &gt; element (vývoj pro Office v sadě Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0490e9423cb747782029eb0fd7254407adb3a607
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955759"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction – &gt; element (vývoj pro Office v sadě Visual Studio)
  `postAction`Element `vstav3` oboru názvů obsahuje `entrypoint` prvky a všechny `postActionData` prvky, které jsou spojeny s akcemi po nasazení, které se spouštějí po instalaci řešení Office.

## <a name="syntax"></a>Syntax

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `postAction`Element je nepovinný a je v `vstav3` oboru názvů. `postAction`V manifestu aplikace je jeden element definovaný pro každou akci po nasazení.

 `postAction`Element nemá žádné atributy.

 `postAction` obsahuje následující prvky.

### <a name="entrypoint"></a>Bod
 Nepovinný parametr. Role `entryPoint` elementu v `vstav3` oboru názvů je definována v [&#60;entrypoint&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 Nepovinný parametr. Role `postActionData` elementu v `vstav3` oboru názvů je definována v [&#60;postActionData&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Příklad akce po nasazení

### <a name="description"></a>Description
 Následující příklad kódu ukazuje `postAction` prvek v manifestu aplikace pro řešení sady Office, které je nasazeno pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
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
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
