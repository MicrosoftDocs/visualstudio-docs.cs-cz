---
title: '&lt;postActionData – &gt; element (vývoj pro Office)'
description: Element postActionData oboru názvů vstav3 určuje data přidružená k jakékoli akci po nasazení, která se spustí po instalaci řešení Office.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a75f61c6d1f80a127f49d96c4e3f4910c66dd8aa
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470063"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;postActionData – &gt; element (vývoj pro Office)
  `postActionData`Element `vstav3` oboru názvů Určuje data přidružená k jakékoli akci po nasazení, která se spustí po instalaci řešení Office.

## <a name="syntax"></a>Syntax

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `postActionData`Element je nepovinný a je v `vstav3` oboru názvů. `postActionData`V manifestu aplikace je jeden element definovaný pro každou akci po nasazení.

 `postActions`Element nemá žádné atributy.

 `postActions` nemá žádné podřízené elementy.

## <a name="post-deployment-action-example"></a>Příklad akce po nasazení

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `postAction` prvek v manifestu aplikace pro řešení Office nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
