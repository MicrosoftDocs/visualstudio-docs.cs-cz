---
title: '&lt;formRegions – &gt; element (vývoj pro Office v sadě Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f98c74c2df998f0e79f5b95a316a7917304e029
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538356"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions – &gt; element (vývoj pro Office v sadě Visual Studio)
  `formRegions`Element `vstov4` oboru názvů obsahuje oblasti formuláře systém Microsoft Office Outlooku, které jsou přidruženy k doplňku VSTO.

## <a name="syntax"></a>Syntax

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `formRegions`Element `vstov4` oboru názvů obsahuje všechny `formRegion` prvky pro doplněk VSTO pro Outlook. Je vyžadován pouze pro Doplňky aplikace Outlook VSTO, které obsahují oblasti formuláře.

 `formRegions`V manifestu aplikace může být definován pouze jeden prvek.

 `formRegions`Element nemá žádné atributy.

 `formRegions`Element má následující element.

### <a name="formregion"></a>formRegion
 Vyžaduje se pro doplňky Outlook VSTO, které obsahují oblasti formuláře. `formRegion`Element je definován v [&#60;FormRegion&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `formRegions` prvek v manifestu aplikace pro řešení Office na úrovni aplikace nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)