---
title: '&lt;entryPoint – &gt; element (vývoj pro Office v sadě Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoints> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8e735cfabcc02a46ca83759a7ad53877bfb05f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543569"
---
# <a name="ltentrypointsgt-element-office-development-in-visual-studio"></a>&lt;entryPoint – &gt; element (vývoj pro Office v sadě Visual Studio)
  `entryPoints`Element `vstav3` oboru názvů obsahuje všechny `entryPoint` prvky přidružené k řešení systému Office.

## <a name="syntax"></a>Syntax

```xml
<entryPoints>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
</entryPoints>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `entryPoints`Element je povinný a je v `vstav3` oboru názvů. `entryPoints`V manifestu aplikace pro každé řešení sady Office je definován jeden prvek. Například pokud nasadíte tři řešení pro systém Office v nasazení více projektů, jsou `entryPoints` v manifestu aplikace tři prvky.

 `entryPoints`Element má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|id|Vyžaduje se pro nasazení ve více projektech. Název řešení pro Office. Identifikátor nesmí obsahovat symbol EQUAL (=).|

 `entryPoints` obsahuje následující prvky.

### <a name="entrypoint"></a>Bod
 Povinná hodnota. Role `entryPoint` elementu v `vstav3` oboru názvů je definována v [&#60;entryPoint&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `entryPoints` prvek v manifestu aplikace pro řešení na úrovni dokumentu nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstav3:entryPoints>
  <vstav3:entryPoint
    class="ContosoExcelWorkbook.ThisWorkbook">
    <assemblyIdentity
      name="ContosoExcelWorkbook"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:entryPoint
    class="ContosoExcelWorkbook.Sheet1">
    <assemblyIdentity
      name="ContosoExcelWorkbook"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:entryPoint
    class="ContosoExcelWorkbook.Sheet2">
    <assemblyIdentity
      name="ContosoExcelWorkbook"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:entryPoint
    class="ContosoExcelWorkbook.Sheet3">
    <assemblyIdentity
      name="ContosoExcelWorkbook"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
</vstav3:entryPoints>
```

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `entryPoints` prvek v manifestu aplikace pro řešení na úrovni aplikace nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstav3:entryPoints>
  <vstav3:entryPoint
    class="ContosoOutlookAddIn.ThisAddIn">
    <assemblyIdentity
      name="ContosoOutlookAddIn"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
</vstav3:entryPoints>
```

## <a name="multi-project-deployment-example"></a>Příklad nasazení s více projekty

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `entryPoints` prvek v manifestu aplikace pro nasazení ve více projektech. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstav3:entryPoints
  id="ContosoExcel">
  <vstav3:entryPoint
    class="ContosoExcelWorkbook.ThisWorkbook">
    <assemblyIdentity
      name="ContosoExcelWorkbook"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:entryPoint
    class="ContosoExcelWorkbook.Sheet1">
    <assemblyIdentity
      name="ContosoExcelWorkbook"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:entryPoint
    class="ContosoExcelWorkbook.Sheet2">
    <assemblyIdentity
      name="ContosoExcelWorkbook"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:entryPoint
    class="ContosoExcelWorkbook.Sheet3">
    <assemblyIdentity
      name="ContosoExcelWorkbook"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
</vstav3:entryPoints>
<vstav3:entryPoints
  id="ContosoOutlook">
  <vstav3:entryPoint
    class="ContosoOutlookAddIn.ThisAddIn">
    <assemblyIdentity
      name="ContosoOutlookAddIn"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
</vstav3:entryPoints>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)