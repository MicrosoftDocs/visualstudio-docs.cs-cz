---
title: 'Postupy: použití značek Text | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a3b766e4eacc04bbf4d4a8e4c022484d452954f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820873"
---
# <a name="how-to-use-text-markers"></a>Postupy: použití značek text
Textu značky lze použít k úpravě <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objektu.  
  
## <a name="procedures"></a>Procedury  
  
### <a name="to-apply-text-markers"></a>Chcete-li použít text značky  
  
1.  Získání instance <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> třídy.  
  
    > [!NOTE]
    >  Základní editor automaticky aplikuje standardní text značky na všechny dokumenty, které je úpravy a neměl by být nutné explicitní použití standardního textu značky.  
  
2.  Získat Identifikátor značky typu značky jsou zajímá voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metodu s `GUID` text značky chcete pracovat.  
  
    > [!NOTE]
    >  Nepoužívejte `GUID` sady VSPackage nebo služby, která obsahuje text značky.  
  
3.  Použití ID typu značky získán voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metodu jako parametr pro volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metoda nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> způsob, jak použít značku textu pro danou oblast textu.  
  
### <a name="to-add-features-to-text-markers"></a>Přidávání funkcí do textu značky  
  
1. Může být vhodné pro přidání dalších funkcí do textu značky, jako jsou popisy tlačítek, speciální místní nabídky nebo obslužná rutina pro zvláštní okolnosti. Postup:  
  
2. Vytvoření implementace objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní.  
  
3. V případě potřeby je další funkce, implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> rozhraní na stejný objekt, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní.  
  
4. Předání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní, které vytvoříte, volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metoda nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metoda používá k aplikování text značky pro danou oblast textu.  
  
5. Při přidávání kontextové nabídky podpory do oblasti značky text je potřeba vytvořit v nabídce.  
  
    Další informace o tom, jak vytvořit kontextové nabídky, naleznete v tématu [kontextové nabídky](../extensibility/context-menus.md).  
  
6. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Prostředí volání metody zadané rozhraní, jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> metodu, nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metoda podle potřeby.  
  
## <a name="see-also"></a>Viz také  
 [Text značky pomocí starší verze rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Postupy: Přidání standardní text značky](../extensibility/how-to-add-standard-text-markers.md)   
 [Postupy: vytvoření vlastního textu značky](../extensibility/how-to-create-custom-text-markers.md)   
 [Postupy: implementace označování chyb](../extensibility/how-to-implement-error-markers.md)