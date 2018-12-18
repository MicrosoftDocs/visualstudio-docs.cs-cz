---
title: Poskytování vlastních vlastností okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 8b3aeae11e087b6a6bd662ed32564d93062426df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186274"
---
# <a name="providing-a-custom-properties-window"></a>Poskytování vlastních vlastností okna
Je možné poskytnout vlastní **vlastnosti** okna pro daný projekt systému, místo rozšíření **vlastnosti** okno poskytované [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE). Většina často došlo k chybě scénář je při sami implementaci objektu umístěn v rámci okna.  
  
 V případě, že neimplementují objektu umístěn v rámci okna, ale ještě k ní máte přístup jiným způsobem, existuje mnoho způsobů, jak získat přístup <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> rozhraní, jak je uvedeno v posledním postupu na této stránce.  
  
### <a name="to-provide-your-properties-window"></a>K poskytování okna Vlastnosti  
  
1.  Definovat identifikátor GUID, který představuje vaše **vlastnosti** implementace okna.  
  
2.  Ve vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementaci, použijte <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> služby se nabídnout vaše **vlastnosti** okno jako služba pro prostředí sady Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Volání vlastnosti okna  
  
1.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> metody.  
  
2.  `QueryService` pro <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> z <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> předán <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> metody.  
  
3.  Získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> služby.  
  
4.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> s prvním parametrem nastaveným na `SEID_PropertyBrowserSID` (na základě <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> výčet) a třetí parametr `varValue`, představující řetězec forma identifikátoru GUID, který představuje vaše **vlastnosti** okno. Toto volání pouze jednou při prvním vytváření vaší **vlastnosti** okna okno dokumentu. Po zavolání toto **vlastnosti** okna je přidružený k vaší rámec okna.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>K získání objektu okno rámce, když nejste implementátor  
  
-   Je možné `QueryService` pro <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> služba <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> s parametrem `propid` nastavena na <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.  
  
-   Okno aktivní dokument lze získat voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> prostřednictvím SVsMonitorSelection služby. Nastavte parametr `elementid` k `SEID_WindowFrame`, z <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> výčtu.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../extensibility/internals/extending-properties.md)   
 [Pole a rozhraní okna Vlastnosti](../extensibility/internals/properties-window-fields-and-interfaces.md)