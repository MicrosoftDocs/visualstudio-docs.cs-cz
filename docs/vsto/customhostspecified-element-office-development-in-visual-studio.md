---
title: '&lt;customHostSpecified – &gt; element (vývoj pro Office v sadě Visual Studio)'
description: Přečtěte si, jak element customHostSpecified označuje, že toto řešení není samostatná aplikace.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ba5ce54e862862c1e6750c78416fec4d5cf51cdd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849980"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified – &gt; element (vývoj pro Office v sadě Visual Studio)
  `customHostSpecified`Element označuje, že toto řešení není samostatná aplikace. Řešení pro systém Office obsahují součásti, které jsou hostovány v aplikacích systém Microsoft Office.

## <a name="syntax"></a>Syntax

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `customHostSpecified`Element je vyžadován pro řešení Office. Tento prvek je v `co.v1` oboru názvů a určuje, že toto nasazení obsahuje komponentu, která bude nasazena v rámci vlastního hostitele a není samostatnou aplikací.

 Tento prvek je podřízeným prvkem prvního `<entrypoint>` prvku v manifestu aplikace. V tomto elementu nesmí být žádné další podřízené elementy `<entrypoint>` nebo [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] během instalace dojde k chybě ověřování.

 Tento element nemá žádné atributy ani podřízené elementy.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `customHostSpecified` prvek v manifestu aplikace pro řešení Office. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)