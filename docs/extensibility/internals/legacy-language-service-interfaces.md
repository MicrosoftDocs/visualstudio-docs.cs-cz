---
title: Rozhraní služby starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 065ef972709ca78b516a9acc5f4a737d2963e4b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726849"
---
# <a name="legacy-language-service-interfaces"></a>Rozhraní služby starší verze jazyka
V případě libovolného konkrétního programovacího jazyka může být v jednu chvíli dostupná jenom jedna instance jazykové služby. Jedna služba jazyka ale může obsluhovat více než jeden editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nepřiřazuje službu jazyka k žádnému konkrétnímu editoru. Proto když požadujete operaci služby jazyka, je nutné určit odpovídající editor jako parametr.

## <a name="common-interfaces-associated-with-language-services"></a>Společná rozhraní přidružená k jazykovým službám
 Editor vrátí jazykovou službu voláním <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> na příslušné VSPackage. ID služby (SID) předané v tomto volání identifikuje požadovanou jazykovou službu.

 Rozhraní základní jazykové služby můžete implementovat na libovolný počet samostatných tříd. Nicméně běžným přístupem je implementace následujících rozhraní v jedné třídě:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (volitelné)

  Rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> musí být implementováno pro všechny jazykové služby. Poskytuje informace o vaší jazykové službě, jako je například lokalizovaný název jazyka, přípony názvů souborů přidružené ke službě jazyka a postup načtení colorizer.

## <a name="additional-language-service-interfaces"></a>Další rozhraní služby jazyka
 K dispozici jsou další rozhraní s vaší jazykovou službou. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] požádá o samostatnou instanci těchto rozhraní pro každou instanci textové vyrovnávací paměti. Proto byste měli implementovat každé z těchto rozhraní na svém vlastním objektu. V následující tabulce jsou uvedena rozhraní, která vyžadují jednu instanci každé instance vyrovnávací paměti textu.

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Spravuje doplňky okna kódu, například rozevírací panel. Toto rozhraní můžete získat pomocí metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. Existuje jeden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> pro každé okno kódu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Vybarvuje klíčová slova a oddělovače jazyka. Toto rozhraní můžete získat pomocí metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> se volá v době vykreslování. Vyhněte se práci náročné na výpočetní výkon v rámci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> nebo může dojít ke zhoršení výkonu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Poskytuje popisy parametrů technologie IntelliSense. Když služba jazyka rozpozná znak, který označuje, že by se měla zobrazit data metody, jako je například levá kulatá závorka, volá metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> pro oznámení zobrazení textu, že je služba jazyka připravena k zobrazení popisu parametru informace. Textové zobrazení pak volá zpět do jazykové služby pomocí metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> rozhraní, aby se zobrazily požadované informace pro zobrazení popisu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Poskytuje dokončování příkazů IntelliSense. Když je jazyková služba připravena k zobrazení seznamu pro doplňování, zavolá metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> v zobrazení text. Textové zobrazení pak volá zpět do jazykové služby pomocí metod objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Umožňuje úpravu zobrazení textu pomocí obslužné rutiny příkazu. Třída, ve které implementujete rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>, musí také implementovat rozhraní <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Zobrazení text načte objekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> dotazem na objekt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, který je předán metodě <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>. Pro každé zobrazení by měl existovat jeden objekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Zachycuje příkazy, které uživatel zadá do okna Code (kód). Monitorujte výstup z implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> a poskytněte vlastní informace o dokončení a Prohlédněte si úpravy.<br /><br /> Chcete-li předat objekt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> do textového zobrazení, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|

## <a name="see-also"></a>Viz také:
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Kontrolní seznam: Vytvoření služby starší verze jazyka](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)