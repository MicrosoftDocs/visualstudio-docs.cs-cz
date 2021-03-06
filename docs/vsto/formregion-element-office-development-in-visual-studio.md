---
description: Element formRegion oboru názvů vstov4 systém Microsoft Office identifikuje oblast formuláře Outlooku, která je přidružená k doplňku VSTO.
title: '&lt;formRegion – &gt; element (vývoj pro Office v sadě Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0851ba9e117b464d3a2fbb9ad9903af17ceda0c4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221077"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion – &gt; element (vývoj pro Office v sadě Visual Studio)
  `formRegion`Element `vstov4` oboru názvů identifikuje oblast formuláře systém Microsoft Office Outlooku, která je přidružená k doplňku VSTO.

## <a name="syntax"></a>Syntax

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `formRegion`Element `vstov4` oboru názvů identifikuje oblast formuláře přidruženou k DOPLŇKu VSTO pro Outlook. Je vyžadován pouze pro Doplňky aplikace Outlook VSTO, které obsahují oblasti formuláře.

 V `formRegion` rámci jednoho doplňku VSTO může být definováno více elementů `formRegions` .

 `formRegion`Element má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`name`|Povinná hodnota. Určuje název oblasti formuláře.|

 `formRegion`Element má následující podřízené prvky.

### <a name="messageclass"></a>messageClass
 `messageClass`Prvek identifikuje formulář aplikace Outlook, který je přidružen k oblasti formuláře.

 `messageClass`Element má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`name`|Povinná hodnota. Určuje formulář, který je spojen s oblastí formuláře.|

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `formRegion` prvek v manifestu aplikace pro doplněk aplikace Outlook VSTO nasazený pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . S touto oblastí formuláře jsou přidruženy tři třídy zpráv. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Viz také

- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
