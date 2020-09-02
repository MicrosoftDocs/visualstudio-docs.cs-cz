---
title: '&lt;Application – &gt; element (vývoj pro Office v sadě Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <application> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3540df77b4498376dcde389730e17e7506647fb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543738"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;Application – &gt; element (vývoj pro Office v sadě Visual Studio)
  `application`Element `vstav3` oboru názvů obtéká popis řešení pro systém Office. Podřízené prvky jsou odlišné pro přizpůsobení na úrovni dokumentu a doplňky VSTO.

## <a name="syntax-for-document-level-customizations"></a>Syntaxe pro přizpůsobení na úrovni dokumentu

```xml
<application>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</application>
```

## <a name="syntax-for-application-level-add-ins"></a>Syntaxe pro Doplňky na úrovni aplikace

```xml
<application>
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
</application>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `application`Element `vstav3` oboru názvů je uzel, který zabalí všechny informace specifické pro vlastní nastavení, které jsou obsaženy v `vstov4` oboru názvů.

 `application`Element nemá žádné atributy.

 `application`Element má následující element.

### <a name="customization"></a>Přizpůsobení
 Role `customization` elementu v `vstov3` oboru názvů je definována v [&#60;přizpůsobení&#62; elementu &#40;vývojář pro Office v sadě Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `application` prvek v řešení Office na úrovni dokumentu nasazeném pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:document
        solutionId="73e" />
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `application` prvek v řešení Office na úrovni aplikace nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
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
  </vstov4:customizations>
</vstav3:application>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)