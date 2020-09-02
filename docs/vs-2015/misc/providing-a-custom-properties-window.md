---
title: Poskytnutí okna vlastních vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810696"
---
# <a name="providing-a-custom-properties-window"></a>Poskytnutí okna vlastních vlastností
Pro daný systém projektu je možné poskytnout vlastní okno **vlastností** místo rozšíření okna **vlastností** , které poskytuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE). Nejčastěji zjištěný scénář je při implementaci objektu umístěného v rámci okna.  
  
 V případě, že neimplementujete objekt v rámci okna, ale stále k němu máte přístup jiným způsobem, existuje několik způsobů, jak získat přístup k <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> rozhraní, jak je uvedeno v posledním postupu na této stránce.  
  
### <a name="to-provide-your-properties-window"></a>Poskytnutí okno Vlastnosti  
  
1. Definujte identifikátor GUID, který představuje implementaci okna **vlastností** .  
  
2. Ve vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementaci použijte <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> službu k nabídnout vašeho okna **vlastnosti** jako službu do prostředí sady Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Volání okna vlastností  
  
1. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> metodu.  
  
2. `QueryService` pro <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> z <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> předané <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> metody.  
  
3. Získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> ze <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> služby.  
  
4. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> s prvním parametrem nastaveným na `SEID_PropertyBrowserSID` (převedený z <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> výčtu) a třetí parametr, `varValue` představující řetězec formátu identifikátoru GUID, který představuje okno **vlastností** . Toto volání proveďte pouze jednou při prvním vytvoření okna dokumentu okna **vlastností** . Po volání tohoto okna **vlastnosti** je spojena s rámcem okna.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Získání objektu rámce okna, když nejste implementátor  
  
- `QueryService`Pro službu můžete <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> používat s parametrem `propid` nastaveným na <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
- Můžete získat aktivní okno dokumentu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> prostřednictvím služby SVsMonitorSelection. Nastavte parametr `elementid` na, který je `SEID_WindowFrame` proveden z <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> výčtu.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../extensibility/internals/extending-properties.md)   
 [Pole a rozhraní okna Vlastnosti](../extensibility/internals/properties-window-fields-and-interfaces.md)