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
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 17f57b90b7c6aa4c254b2b55ee838a3086193ef7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543595"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint – &gt; element (vývoj pro Office v sadě Visual Studio)
  Každý `entryPoint` prvek `vstav3` oboru názvů identifikuje sestavení vlastního nastavení, které by mělo být spuštěno při [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] instalaci této aplikace.

## <a name="syntax"></a>Syntax

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `entryPoint`Element je povinný a je v `vstav3` oboru názvů.

 Každý `entryPoint` prvek může obsahovat pouze jedno sestavení přizpůsobení. `entryPoint`V manifestu aplikace může být definován více elementů.

 `entryPoint`Element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`class`|Povinná hodnota. Identifikuje sestavení vlastního nastavení, které má být provedeno. Syntaxe pro tento atribut má hodnotu *Namespace. ClassName*.|

 `entryPoint`má následující element.

### <a name="assemblyidentity"></a>assemblyIdentity
 Povinná hodnota. `assemblyIdentity`Element v `vstav3` oboru názvů odkazuje na existující `assemblyIdentity` prvek v [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] manifestu aplikace.

 Role `assemblyIdentity` a její atributy jsou definovány v [&#60;assemblyIdentity&#62; elementu &#40;aplikace ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-application.md).

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `entryPoint` prvky v manifestu aplikace pro řešení Office na úrovni dokumentu nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
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
```

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `entryPoint` prvek v manifestu aplikace pro řešení Office na úrovni aplikace nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)