---
title: '&lt;Description – &gt; element (vývoj pro Office v sadě Visual Studio)'
description: Přečtěte si, že element Description oboru názvů vstov4 ukládá popis řešení Office, který se zobrazí v dialogovém okně Doplňky modelu COM.
titleSuffix: ''
ms.custom: secdec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f065dd07e901ee0d59b39f1096cc351cd70bc02
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897597"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Description – &gt; element (vývoj pro Office v sadě Visual Studio)
  `description`Element `vstov4` oboru názvů ukládá popis řešení Office, který se zobrazí v dialogovém okně Doplňky modelu COM aplikace systém Microsoft Office aplikací.

## <a name="syntax"></a>Syntax

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 Nepovinný parametr. `description`Element je v `vstov4` oboru názvů. Obsahuje popis doplňku, který se zobrazí v dialogovém okně Doplňky modelu COM aplikace systém Microsoft Office aplikací.

 `description`Element nemá žádné atributy ani elementy.

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="description"></a>Description
 Následující příklad kódu ukazuje `description` element pro řešení na úrovni aplikace nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)