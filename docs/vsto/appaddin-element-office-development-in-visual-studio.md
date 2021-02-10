---
title: '&lt;appAddin – &gt; element (vývoj pro Office v sadě Visual Studio)'
description: Přečtěte si, jak element appAddin oboru názvů vstov4 ukládá informace specifické pro přizpůsobení pro doplňky VSTO.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 427d7bc0ec59b98394b292745985be7fdf69b904
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950507"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin – &gt; element (vývoj pro Office v sadě Visual Studio)
  Element **appAddin** `vstov4` oboru názvů ukládá informace specifické pro přizpůsobení pro doplňky VSTO.

## <a name="syntax"></a>Syntax

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 Element **appAddin** je povinný a je v `vstov4` oboru názvů. V manifestu aplikace je definován pouze jeden element **appAddin** .

 Element **appAddin** má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|**aplikace**|Povinná hodnota. Identifikuje aplikaci systém Microsoft Office. Hodnota může být jedna z následujících: Excel, InfoPath, Outlook, PowerPoint, Project, Visio nebo Word.|
|**loadBehavior**|Nepovinný parametr. Ve výchozím nastavení je **loadBehavior** povolený nastavením této hodnoty na. Pro ladění můžete doplněk VSTO zakázat nastavením hodnoty na dvě. Další informace najdete v tabulce s názvem LoadBehavior hodnoty v [položkách registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|
|**Klíče**|Povinná hodnota. Tato hodnota je název klíče registru, který bude aplikace používat k načtení doplňku VSTO. Další informace najdete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|

 Element **appAddin** má následující podřízené prvky.

### <a name="friendlyname"></a>friendlyName
 Nepovinný parametr. Element **FriendlyName** je vysvětlen v [&#60;friendlyName&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>description
 Nepovinný parametr. Element **Description** je vysvětlen v [&#60;description&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 Vyžaduje se jenom pro doplňky Outlook VSTO, které obsahují oblasti formulářů. Element **FormRegions** je vysvětlen v [&#60;formRegions&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="description"></a>Description
 Následující příklad kódu ukazuje prvky **appAddin** v řešení aplikace Outlook nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstov4:appAddIn
  application="Outlook"
  loadBehavior="3"
  keyName="ContosoOutlookAddIn">
  <vstov4:friendlyName>
    ContosoOutlookAddIn
  </vstov4:friendlyName>
  <vstov4:description>
    ContosoOutlookAddIn - Outlook VSTO Add-in
    created with Visual Studio Tools for Office
  </vstov4:description>
  <vstov4:formRegions>
    <vstov4:formRegion
        name="OutlookAddIn1.FormRegion1">
      <vstov4:messageClass name="IPM.Note" />
      <vstov4:messageClass name="IPM.Contact" />
      <vstov4:messageClass name="IPM.Appointment" />
    </vstov4:formRegion>
  </vstov4:formRegions>
</vstov4:appAddIn>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)