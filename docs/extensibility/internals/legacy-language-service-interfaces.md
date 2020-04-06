---
title: Rozhraní starších jazykových služeb | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707386"
---
# <a name="legacy-language-service-interfaces"></a>Rozhraní služby starší verze jazyka
Pro každý konkrétní programovací jazyk může být pouze jedna instance služby jazyka najednou. Služba jednoho jazyka však může obsluhovat více než jeden editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nepřidružuje jazykovou službu k žádnému konkrétnímu editoru. Proto při žádosti o operaci služby jazyka, je nutné určit příslušný editor jako parametr.

## <a name="common-interfaces-associated-with-language-services"></a>Společná rozhraní přidružená k jazykovým službám
 Editor získá službu jazyka <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> voláním na příslušné VSPackage. ID služby (SID) předané v tomto volání identifikuje požadovanou jazykovou službu.

 Můžete implementovat rozhraní služby základního jazyka na libovolný počet samostatných tříd. Běžným přístupem je však implementace následujících rozhraní v jedné třídě:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (volitelné)

  Rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> musí být implementováno ve všech jazykových službách. Poskytuje informace o službě jazyka, jako je například lokalizovaný název jazyka, přípony názvů souborů přidružené ke službě jazyka a způsob načtení kolorace.

## <a name="additional-language-service-interfaces"></a>Další jazyková rozhraní služeb
 Další rozhraní mohou být poskytnuty s vaší jazykovou službou. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]požaduje samostatnou instanci těchto rozhraní pro každou instanci textové vyrovnávací paměti. Proto byste měli implementovat každé z těchto rozhraní na vlastní objekt. V následující tabulce jsou uvedena rozhraní, která vyžadují jednu instanci na instanci vyrovnávací paměti textu.

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Spravuje vylepšení okna kódu, jako je například rozevírací panel. Toto rozhraní můžete získat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> pomocí metody. Je jeden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> na okno kódu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Omalovánizuje klíčová slova jazyka a oddělovače. Toto rozhraní můžete získat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> pomocí metody. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>je volána v době malování. Vyhněte se práci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> náročné na výpočty uvnitř nebo může dojít k unesení výkonu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Poskytuje popisky parametrů IntelliSense. Pokud služba jazyka rozpozná znak, který označuje, že by měla být zobrazena data metody, například otevřená závorka, zavolá metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> upozornění textového zobrazení, že jazyková služba je připravena k zobrazení popisu informací o parametrech. Zobrazení textu pak volá zpět do služby jazyka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> pomocí metod rozhraní získat požadované informace pro zobrazení popisku.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Poskytuje dokončení příkazu IntelliSense. Když je služba jazyka připravena k zobrazení <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> seznamu dokončení, zavolá metodu v textovém zobrazení. Zobrazení textu pak volá zpět do služby <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> jazyka pomocí metod na objekt.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Umožňuje změnu zobrazení textu pomocí obslužné rutiny příkazu. Třída, ve které <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> implementujete <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní musí také implementovat rozhraní. Zobrazení textu načte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objekt dotazem <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> na objekt, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> který je předán do metody. Pro každé <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> zobrazení by měl být jeden objekt.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Zachytí příkazy, které uživatel zadá do okna kódu. Sledování výstupu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> z implementace za účelem poskytnutí vlastních informací o dokončení a úprav y zobrazení<br /><br /> Chcete-li <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objekt předat do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>textového zobrazení, zavolejte .|

## <a name="see-also"></a>Viz také
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Kontrolní seznam: Vytvoření služby starší verze jazyka](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
