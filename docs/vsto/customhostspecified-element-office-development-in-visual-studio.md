---
title: '&lt;customHostSpecified – &gt; element (vývoj pro Office v sadě Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 689848f14b4540a54489b4ea5bbad67e493fe276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544908"
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