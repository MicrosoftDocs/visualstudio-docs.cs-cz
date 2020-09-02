---
title: '&lt;&gt;element dokumentu (vývoj pro Office v sadě Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36d822d60d1a28d48f660f6d358b75bf4a913048
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "63000022"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;&gt;element dokumentu (vývoj pro Office v sadě Visual Studio)
  `document`Element `vstov4` oboru názvů ukládá informace specifické pro přizpůsobení pro přizpůsobení na úrovni dokumentu.

## <a name="syntax"></a>Syntax

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 Vyžaduje se jenom pro přizpůsobení na úrovni dokumentu. `document`Element je v `vstov4` oboru názvů. `document`Element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`solutionId`|Povinná hodnota. Identifikátor GUID používaný modulem runtime Visual Studio Tools for Office k jednoznačné identifikaci řešení na úrovni dokumentu. Tato hodnota je uložena jako vlastnost vlastního dokumentu _AssemblyLocation. Další informace najdete v tématu [Přehled vlastností vlastního dokumentu](../vsto/custom-document-properties-overview.md).|

 `document` nemá žádné podřízené elementy.

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `document` prvek v řešení Office na úrovni dokumentu nasazeném pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)