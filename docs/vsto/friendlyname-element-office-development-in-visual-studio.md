---
description: Element friendlyName oboru názvů vstov4 ukládá název, který se zobrazí v seznamu nainstalovaných programů.
title: '&lt;friendlyName – &gt; element (vývoj pro Office v sadě Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: adcf46a2c232176026181283549c0c59fc713603
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223443"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName – &gt; element (vývoj pro Office v sadě Visual Studio)
  `friendlyName`Element `vstov4` oboru názvů ukládá název, který se zobrazí v seznamu nainstalovaných programů.

## <a name="syntax"></a>Syntax

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `friendlyName`Element je v `vstov4` oboru názvů. Hodnota se zobrazí v seznamu nainstalovaných programů v počítači a v dialogovém okně doplňky VSTO COM aplikace systém Microsoft Office aplikace.

 `friendlyName`Element nemá žádné atributy ani podřízené elementy.

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `friendlyName` prvek v řešení na úrovni aplikace nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
