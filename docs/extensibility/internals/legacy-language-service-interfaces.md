---
title: Rozhraní služby starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e195862ae2cd164a2c62ac16eb17c7a2f07e5c09
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821601"
---
# <a name="legacy-language-service-interfaces"></a>Rozhraní služby starší verze jazyka
Pro konkrétní programovací jazyk může být pouze jedna instance služby jazyka v čase. Jeden jazyk služby ale může sloužit více než jeden editoru.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Služba jazyka nepřidruží k žádné konkrétní editoru. Proto pokud požádáte o operaci služby jazyka, je nutné určit vhodného editoru jako parametr.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Společné rozhraní přidružené k jazykových služeb  
 Editor voláním získá vaše služba jazyka <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> na odpovídající VSPackage. Na službu, kterou toto volání předané ID (SID) určuje požadované služby jazyka.  
  
 Rozhraní služeb jazyka core můžete implementovat v libovolném počtu samostatné třídy. Běžným přístupem je však implementovat následující rozhraní do jedné třídy:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (volitelné)  
  
  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Na všech jazykových služeb musí implementovat rozhraní. Poskytuje informace o vaší služby jazyka, jako je například lokalizovaný název jazyka, přípony názvů souborů, který je přidružený k službě jazyka a jak načíst colorizer.  
  
## <a name="additional-language-service-interfaces"></a>Rozhraní služeb další jazyk  
 Jiná rozhraní lze zadat ve vaší službě jazyka. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] požádá o samostatnou instanci tato rozhraní pro každou instanci textové vyrovnávací paměti. Proto se každá z těchto rozhraní by měly implementovat na vlastní objekt. V následující tabulce jsou uvedeny rozhraní, které vyžadují jednu instanci a instanci vyrovnávací paměti textu.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Spravuje vylepšení okna kódu, jako je například panel rozevíracího seznamu. Toto rozhraní můžete získat pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody. Existuje jedna <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> za okna kódu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Vybarví oddělovače a klíčová slova jazyka. Toto rozhraní můžete získat pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> je volána v době Malování. Vyhněte se práce náročné na výpočty uvnitř <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> nebo může trpět výkon.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Poskytuje popisy parametrů technologie IntelliSense. Když služba jazyka rozpozná znak, který označuje, tato metoda data by měla být zobrazena, jako je otevřena závorka, volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metoda oznámit text zobrazení, které služba jazyka je připravený k zobrazení popisu informace o parametru. Zobrazení textu pak zavolá služba jazyka podle použití metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> rozhraní získat požadované informace zobrazit v popisu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Poskytuje doplňování technologie IntelliSense. Služba jazyka je připravený k zobrazení seznamu dokončení, zavolá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodu pro zobrazení textu. Zobrazení textu pak zavolá zpět do služby jazyka podle pomocí metod na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> objektu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Umožňuje úpravu zobrazení textu pomocí obslužné rutiny příkazu. Třída, ve kterém je implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> musí implementovat také rozhraní <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Načte zobrazení textu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objektu pomocí dotazu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objektu, který je předán do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody. Měl by existovat jeden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objekt pro každé zobrazení.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Zachycuje příkazy, že uživatel zadá do okna kódu. Sledovat výstup z vaší <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementace poskytují informace o vlastních dokončení a zobrazit změny<br /><br /> K předání vašeho <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objektu k zobrazení textu, volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Viz také  
 [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Kontrolní seznam: Vytvoření služby starší verze jazyka](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)