---
title: Přístup k textu vrstvy pomocí starší verze rozhraní API | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5eb9d92e3604224f3806cf64f2dd8d4529e8d01
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729041"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Přístup k textu vrstvy pomocí starší verze rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Text vrstva obvykle zapouzdřuje určitý aspekt rozložení textu. Například vrstva "funkce na-time" Skryje text před a za funkci obsahující znak stříšky (textový kurzor).  
  
 Text vrstvě se nachází mezi vyrovnávací paměť a zobrazení a mění způsob zobrazení se zobrazí obsah přípravné vyrovnávací paměti.  
  
## <a name="text-layer-information"></a>Informace o vrstvě textu  
 Následující seznam popisuje, jak fungují text vrstvy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
-   Text ve vrstvě text můžete opatřený s barevné zvýrazňování syntaxe a značky.  
  
-   Momentálně nelze implementovat vlastní vrstvy.  
  
-   Poskytuje vrstvu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, který je odvozen z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Samotné vyrovnávací paměti textu je také implementováno jako vrstvu, která umožňuje zobrazení řešit polymorphically vrstvách.  
  
-   Libovolný počet vrstvy můžou být mezi zobrazením a vyrovnávací paměti. Každá vrstva se zabývá pouze vrstvy pod ní a zobrazení se zabývá do značné míry vrstvě úplně nahoře. (Zobrazení má některé informace o vyrovnávací paměti.)  
  
-   Vrstva může mít vliv pouze vrstvy, které jsou pod ním. Ho nemůže ovlivnit vrstvy nad ním nad rámec standardních události pocházející.  
  
-   V editoru skrytý text, syntetické a zalamování řádků jsou implementovány jako vrstvy. Skryté a syntetické text můžete implementovat bez práci přímo s vrstvami. Další informace najdete v tématu [osnovy ve službě starší verze jazyka](../extensibility/internals/outlining-in-a-legacy-language-service.md) a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Každá vrstva text má vlastní místní systém souřadnic, který je zveřejněný prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> rozhraní. Zalamování řádků vrstvy, například může obsahovat dva řádky během základní textové vyrovnávací paměti může obsahovat pouze jeden řádek.  
  
-   Zobrazení komunikuje s vrstvami prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> rozhraní. Pomocí tohoto rozhraní sjednotit zobrazení souřadnic s vyrovnávací paměť souřadnic.  
  
-   Žádné vrstvy, jako je vrstva syntetické text, který pochází text musí poskytnout implementaci místní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Kromě <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, musí implementovat vrstvu text <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> a aktivovat události v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Barevné zvýrazňování syntaxe ve vlastních editorech](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Text značky pomocí starší verze rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Přizpůsobení ovládacích prvků a nabídek editoru pomocí zastaralého rozhraní API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)

