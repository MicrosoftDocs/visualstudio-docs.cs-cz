---
title: 'Postupy: používání textových značek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64800721"
---
# <a name="how-to-use-text-markers"></a>Postupy: Použití textových značek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pro úpravu objektu lze použít textové značky <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-apply-text-markers"></a>Použití textových značek  
  
1. Získejte instanci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> třídy.  
  
    > [!NOTE]
    > Základní editor automaticky aplikuje standardní textové značky na libovolný dokument, který upravuje, a neměl by být nutné explicitně použít standardní textové značky.  
  
2. Získejte ID typu značky, které vás zajímá, voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metody s `GUID` textovou značkou, se kterou chcete pracovat.  
  
    > [!NOTE]
    > Nepoužívejte sadu `GUID` VSPackage ani službu, která poskytuje značku textu.  
  
3. Použijte ID typu značky získané voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metody jako parametru pro volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metody nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metody pro použití textové značky na danou oblast textu.  
  
#### <a name="to-add-features-to-text-markers"></a>Přidání funkcí do textových značek  
  
1. Může být vhodné přidat k textové značce další funkce, jako jsou například popisy tlačítek, speciální kontextová nabídka nebo obslužná rutina pro zvláštní okolnosti. Postupujte následovně:  
  
2. Vytvořte objekt implementující <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní.  
  
3. Pokud je žádoucí další funkce, implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> rozhraní a rozhraní na stejném objektu, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní.  
  
4. Předejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní, které vytvoříte, do volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metody nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metody použité k aplikování značky text na danou oblast textu.  
  
5. Když přidáte podporu kontextové nabídky do oblasti textové značky, je nutné vytvořit nabídku.  
  
     Další informace o tom, jak vytvořit kontextovou nabídku, najdete v tématu [kontextové nabídky](../extensibility/context-menus.md).  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Prostředí volá metody dodaných rozhraní, jako je <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> Metoda nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metoda, podle potřeby.  
  
## <a name="see-also"></a>Viz také  
 [Používání textových značek se starší verzí rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Postupy: Přidání standardních značek textu](../extensibility/how-to-add-standard-text-markers.md)   
 [Postupy: vytváření vlastních textových značek](../extensibility/how-to-create-custom-text-markers.md)   
 [Postupy: Implementace chybových značek](../extensibility/how-to-implement-error-markers.md)
