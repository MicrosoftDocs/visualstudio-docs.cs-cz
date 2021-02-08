---
title: Rozhraní služby starší verze jazyka | Microsoft Docs
description: Přečtěte si o rozhraních dostupných v sadě Visual Studio SDK, která poskytují funkce služby starší verze jazyka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8f6010ffdf6873073eded63c75475115391a3964
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839596"
---
# <a name="legacy-language-service-interfaces"></a>Rozhraní služby starší verze jazyka
V případě libovolného konkrétního programovacího jazyka může být v jednu chvíli dostupná jenom jedna instance jazykové služby. Jedna služba jazyka ale může obsluhovat více než jeden editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nepřiřazuje službu jazyka k žádnému konkrétnímu editoru. Proto když požadujete operaci služby jazyka, je nutné určit odpovídající editor jako parametr.

## <a name="common-interfaces-associated-with-language-services"></a>Společná rozhraní přidružená k jazykovým službám
 Editor načte službu jazyka voláním <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> na příslušný VSPackage. ID služby (SID) předané v tomto volání identifikuje požadovanou jazykovou službu.

 Rozhraní základní jazykové služby můžete implementovat na libovolný počet samostatných tříd. Nicméně běžným přístupem je implementace následujících rozhraní v jedné třídě:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (volitelné)

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>Rozhraní musí být implementováno pro všechny jazykové služby. Poskytuje informace o vaší jazykové službě, jako je například lokalizovaný název jazyka, přípony názvů souborů přidružené ke službě jazyka a postup načtení colorizer.

## <a name="additional-language-service-interfaces"></a>Další rozhraní služby jazyka
 K dispozici jsou další rozhraní s vaší jazykovou službou. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] požádá o samostatnou instanci těchto rozhraní pro každou instanci textové vyrovnávací paměti. Proto byste měli implementovat každé z těchto rozhraní na svém vlastním objektu. V následující tabulce jsou uvedena rozhraní, která vyžadují jednu instanci každé instance vyrovnávací paměti textu.

|Rozhraní|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Spravuje doplňky okna kódu, například rozevírací panel. Toto rozhraní lze získat pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody. V <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> každém okně kódu je jeden.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Vybarvuje klíčová slova a oddělovače jazyka. Toto rozhraní lze získat pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> se volá v době vykreslování. Vyhněte se práci náročné na výpočetní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> výkon uvnitř nebo výkonu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Poskytuje popisy parametrů technologie IntelliSense. Když služba jazyka rozpozná znak, který označuje, že by se měla zobrazit data metody, jako je například levá kulatá závorka, volá metodu, která <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> upozorní zobrazení textu, že je služba jazyka připravena k zobrazení popisu parametru informace. Textové zobrazení pak volá zpět do jazykové služby pomocí metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> rozhraní k získání požadovaných informací pro zobrazení popisu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Poskytuje dokončování příkazů IntelliSense. Když je služba jazyka připravena k zobrazení seznamu pro dokončení, volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodu v zobrazení text. Textové zobrazení pak volá zpět do jazykové služby pomocí metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> objektu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Umožňuje úpravu zobrazení textu pomocí obslužné rutiny příkazu. Třída, ve které implementujete <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> rozhraní, musí implementovat také <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Zobrazení text načte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objekt pomocí dotazu na <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objekt, který je předán <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodě. Pro každé zobrazení by měl existovat jeden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objekt.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Zachycuje příkazy, které uživatel zadá do okna Code (kód). Monitorování výstupu z vaší <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementace za účelem poskytnutí informací o vlastním dokončení a zobrazení úprav<br /><br /> Chcete-li předat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objekt do textového zobrazení, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .|

## <a name="see-also"></a>Viz také
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Kontrolní seznam: Vytvoření služby starší verze jazyka](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
