---
title: Události vyrovnávací paměti textu ve starších verzích API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186408"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Události vyrovnávací paměti textu v zastaralém rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Objekt textové vyrovnávací paměti generuje několik různých událostí, které umožňují reagovat na různé situace.  
  
 Pokud používáte starší verze rozhraní API, měli byste implementovat následující rozhraní, aby bylo možné dostávat oznámení o změnách ve vyrovnávací paměti textu. Vystavení rozhraní pro textové vyrovnávací paměti pomocí `IConnectionPointContainer` rozhraní ve vyrovnávací paměti textu pro příjem oznámení změn řádků z vyrovnávací paměti. Další informace najdete v tématu [Postup: registrace pro události textové vyrovnávací paměti pomocí starší verze rozhraní API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). V případě `IVsTextStreamEvents` `IVsTextLinesEvents` rozhraní nebo jsou změny vráceny buď na jednu nebo dvojrozměrné souřadnice, v uvedeném pořadí.  
  
## <a name="text-buffer-interfaces"></a>Rozhraní textové vyrovnávací paměti  
 Následují rozhraní implementovaná objektem textové vyrovnávací paměti.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umožňuje vytváření složených akcí (tj. akcí, které jsou seskupeny v jedné jednotce zpět/znovu).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Umožňuje trvalá data dokumentu spravovaná vyrovnávací pamětí textu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Poskytuje základní služby; používá mnoho klientů.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Poskytuje funkce pro čtení a zápis pomocí dvourozměrných souřadnic. Dědí z `IVsTextBuffer` .|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Poskytuje rychlý a sekvenční přístup k textu ve vyrovnávací paměti, který je orientovaný na proud.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Poskytuje funkce pro čtení a zápis s použitím jednorozměrné souřadnice. Dědí z `IVsTextBuffer` .|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Poskytuje přístup k obecné kolekci vlastností. Nejdůležitější vlastností je název nebo moniker vyrovnávací paměti. Vlastní náhodná data můžete do vyrovnávací paměti ukládat pomocí tohoto rozhraní tak, že vytvoříte identifikátor GUID a použijete ho jako klíč.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Podporuje body připojení pro události.|  
  
## <a name="text-buffer-event-interfaces"></a>Rozhraní událostí pro ukládání textu do vyrovnávací paměti  
 Níže jsou uvedené rozhraní pro oznamování událostí pro textové vyrovnávací paměti.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Upozorní klienty, když je k textové vyrovnávací paměti přidružena nová jazyková služba.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Upozorní klienty, když dojde k inicializaci textové vyrovnávací paměti a kdy se změny provedou v datech ve vyrovnávací paměti textu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Upozorňuje klienty na změny v podkladové textové vyrovnávací paměti v jednorozměrném souřadnicích.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Upozorňuje klienty na změny v podkladové textové vyrovnávací paměti v dvojrozměrné souřadnicích.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Upozorňuje klienty na změny dat uživatelů.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Upozorní klienty na poslední gesto potvrzení o aktivaci události a změnu rozsahu textu. `IVsPreliminaryTextChangeCommitEvents`Rozhraní se neaktivuje v reakci na příkazy k vrácení zpět nebo opakování. Události se aktivují pouze pro vyrovnávací paměti, které mají správce vrácení zpět. `IVsPreliminaryTextChangeCommitEvents` je aktivována před jinými událostmi, jako je například hodně prospekt, aby se zajistilo, že ostatní události nemění text před potvrzením změn. Vaše VSPackage musí monitorovat buď `IVsPreliminaryTextChangeCommitEvents` rozhraní, nebo `IVsFinalTextChangeCommitEvents` rozhraní, ale ne obojí.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Upozorní klienty na poslední gesto potvrzení o aktivaci události a změnu rozsahu textu. `IVsFinalTextChangeCommitEvents`Rozhraní se neaktivuje v reakci na příkazy k vrácení zpět nebo opakování. Události se aktivují pouze pro vyrovnávací paměti, které mají správce vrácení zpět. `IVsFinalTextChangeCommitEvents` je určeno pro použití pouze pro jazykové služby nebo jiné objekty, které mají úplnou kontrolu nad úpravou. Vaše VSPackage musí monitorovat buď `IVsPreliminaryTextChangeCommitEvents` rozhraní, nebo `IVsFinalTextChangeCommitEvents` rozhraní, ale ne obojí.|  
  
## <a name="see-also"></a>Viz také  
 [Přístup k textové vyrovnávací paměti pomocí starší verze rozhraní API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Postupy: Registrace událostí vyrovnávací paměti textu pomocí zastaralého rozhraní API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
