---
title: Ukázka rozšíření programového testu UI pro Excel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c6075f9f95f7dc1d21db91936cf35c76f9b2e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672231"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Ukázka rozšíření programového testu UI pro Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Součást rozšíření v ukázce se spouští v procesu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] programového testu uživatelského rozhraní a je trochu hierarchicky s `ExtensionPackage`ou třídou v základní třídě. Třídy `TechnologyManager`, `ActionFilter` a `PropertyProvider` jsou na další úrovni s ovládacími prvky na nejvyšší úrovni.

 ![Architektura testovacího rozšíření aplikace Excel](../test/media/excel-extarch.png "Excel_ExtArch") Architektura rozšíření aplikace Excel

## <a name="extension-points"></a>Rozšiřovací body
 Tyto třídy představují Rozšiřovací body, které jsou implementovány v ukázce pro povolení programového testování uživatelského rozhraní pro [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

### <a name="extensionpackage"></a>ExtensionPackage
 Zděděno z třídy <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> je toto vstupní bod pro rozšíření programového testování uživatelského rozhraní. Implementace této abstraktní třídy poskytuje programový test UI Framework interní přístup k vašemu vlastnímu Správci technologie testování uživatelského rozhraní, poskytovateli vlastností testu uživatelského rozhraní a filtru akcí testu uživatelského rozhraní pro testování nového uživatelského rozhraní. Další informace naleznete v tématu [Třída ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 Tato třída zděděná od třídy <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> poskytuje manažerovi technologie pro nahrávání a přehrávání testů. Další informace naleznete v tématu [Třída TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 Tato třída je zděděná od třídy [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) a poskytuje základní třídu pro agregaci podobných výsledků testovacích akcí do jednoho výsledku testu. Další informace naleznete v tématu [třída ActionFilter](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Prvky technologie
 Základní třída zděděná z třídy <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> poskytuje základ pro prvky technologie ve vašich testech uživatelského rozhraní, které je možné zaznamenat a přehrát zpátky. Další informace naleznete v tématu [třídy prvků](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 Tato třída zděděná od třídy <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> poskytuje základní třídu pro podporu vlastností prvků uživatelského rozhraní pro nahrávání a přehrávání testů. Další informace naleznete v tématu [Třída PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [ExtensionPackage – třída](../test/sample-excel-extension-extensionpackage-class.md)
- [TechnologyManager – třída](../test/sample-excel-extension-technologymanager-class.md)
- [ActionFilter – třída](../test/sample-excel-extension-actionfilter-class.md)
- [Třídy Element](../test/sample-excel-extension-element-classes.md)
- [PropertyProvider – třída](../test/sample-excel-extension-propertyprovider-class.md)
