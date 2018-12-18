---
title: 'Ukázka rozšíření Excel: Třída ActionFilter | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 87bffbbd3d463de19c923e6d1bd9f865aca37851
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285388"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Ukázka rozšíření aplikace Excel: třída ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento vnitřní třída rozšiřuje <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> třídy a představuje filtr testovacích akcí na [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] elementu.  
  
## <a name="simple-properties"></a>Jednoduché vlastnosti  
 Tyto vlastnosti jen pro čtení umožňují vývojářům určit, jak tento filtr akce testu má být provedena v rámci programových rozhraní testování uživatelského rozhraní. Například <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> vlastnosti obsahuje název filtru akce. Další vlastnosti get <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> filtru akce <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> název akce testu, které jsou filtrovány podle filtru akce tohoto testu. Ostatní označuje, jestli se má <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> a také, jestli je akce testu <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>ProcessRule – metoda  
 Tato metoda je volána metodou testovací rozhraní programového uživatelského rozhraní a spouští filtr proti poskytnuté <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>. Toto konkrétní přepsání odebere myši vybrat akci na buňky při další akce v zásobníku odešle stisknutí kláves do buňky. Potom vrátí `false`.  
  
## <a name="private-methods"></a>Privátní metody  
 `IsLeftClick` Metody Určuje, zda zadaná akce představuje přejít myši. `AreActionsOnSameExcelCell` Metoda určuje, zda dva zadané akce jsou spouštěny na stejné buňky v aplikaci Excel.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



