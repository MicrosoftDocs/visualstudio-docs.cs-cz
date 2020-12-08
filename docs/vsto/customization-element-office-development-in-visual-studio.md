---
title: '&lt;přizpůsobení – &gt; element (vývoj pro Office v sadě Visual Studio)'
description: Přečtěte si, jak element Customization oboru názvů vstov4 popisuje konkrétní řešení Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f50b441393e9d07dcd0b409248f199484022654
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844111"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;přizpůsobení – &gt; element (vývoj pro Office v sadě Visual Studio)
  `customization`Element `vstov4` oboru názvů popisuje konkrétní řešení Office. Podřízené prvky jsou odlišné pro přizpůsobení na úrovni dokumentu a doplňky VSTO.

## <a name="syntax-for-document-level-customizations"></a>Syntaxe pro přizpůsobení na úrovni dokumentu

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>Syntaxe doplňků VSTO

```xml
<customization
  id
  <appAddin
    application
    loadBehavior
    keyName>
  <friendlyName></friendlyName>
  <description></description>
  <formRegions></formRegions>
</customization>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `customization`Element obsahuje informace specifické pro přizpůsobení. Tento element musí být v následujícím oboru názvů: `vstov4=urn:schemas-microsoft-com:vsto.v4` . `customization`Pro každé řešení Office existuje jeden element. Například pokud nasadíte tři řešení pro systém Office v nasazení více projektů, jsou `customization` v manifestu aplikace tři prvky.

 Podřízené elementy sestavení musí být také v tomto oboru názvů.

 `customization`Element má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`id`|Vyžaduje se pro nasazení ve více projektech. `id`Prvek jednoznačně identifikuje řešení pro systém Office.|

### <a name="document-level-customizations"></a>Document-Level přizpůsobení
 `customization`Element má následující podřízený element.

#### <a name="document"></a>dokument
 `document`Element v `vstov4` oboru názvů je definován v [&#60;dokumentu&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).

### <a name="vsto-add-ins"></a>Doplňky VSTO
 `customization`Element má následující podřízený element.

#### <a name="appaddin"></a>appAddin
 `appAddin`Element v `vstov4` oboru názvů je definován v [&#60;appAddin&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `customization` prvek pro přizpůsobení na úrovni dokumentu. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>Příklad doplňku VSTO

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `customization` prvek doplňku VSTO. Toto je doplněk VSTO pro Outlook, který obsahuje oblasti formuláře. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstov4:customization>
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
</vstov4:customization>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)