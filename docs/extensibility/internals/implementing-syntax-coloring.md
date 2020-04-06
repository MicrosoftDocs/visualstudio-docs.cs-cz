---
title: Implementace zbarvení syntaxe | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707637"
---
# <a name="implementing-syntax-coloring"></a>Implementace barevného zvýrazňování syntaxe
Pokud služba jazyka poskytuje zbarvení syntaxe, analyzátor převede řádek textu na pole barevných položek a vrátí typy tokenů odpovídající těmto barevným položkám. Analyzátor by měl vrátit typy tokenů, které patří do seznamu colorable položek. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zobrazí každou barevnou položku v okně kódu podle atributů přiřazených objektem colorizer příslušnému typu tokenu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]neurčuje rozhraní analyzátoru a implementace analyzátoru je zcela na vás. Výchozí implementace analyzátoru je však k dispozici v projektu Visual Studio Language Package. Pro spravovaný kód poskytuje rozhraní spravovaného balíčku (MPF) úplnou podporu pro vybarvení textu.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace barevného kódu syntaxe naleznete v [tématu Návod: Zvýraznění textu](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Kroky následované editorem pro vybarvení textu

1. Editor získá colorizer voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> na objektu.

2. Editor volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> metodu k určení, zda colorizer potřebuje stav každého řádku, který má být udržován mimo colorizer.

3. Pokud colorizer vyžaduje, aby byl stav udržován mimo colorizer, editor zavolá metodu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> aby získal stav prvního řádku.

4. Pro každý řádek ve vyrovnávací paměti <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> editor volá metodu, která provádí následující kroky:

    1. Řádek textu je předán do skeneru převést text na tokeny. Každý token určuje text tokenu a typ tokenu.

    2. Typ tokenu je převeden na index do seznamu barevných položek.

    3. Informace o tokenu se používá k vyplnění pole tak, aby každý prvek pole odpovídá znaku v řádku. Hodnoty uložené v poli jsou indexy do seznamu barevných položek.

    4. Stav na konci řádku je vrácena pro každý řádek.

5. Pokud colorizer vyžaduje, aby byl zachován stav, editor uloží stav pro tento řádek.

6. Editor vykreslí řádek textu pomocí informací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> vrácených z metody. To vyžaduje následující kroky:

    1. Pro každý znak v řádku získáte index barevných položek.

    2. Pokud používáte výchozí barevné položky, přezouvat seznam barevných položek editoru.

    3. V opačném případě volejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodu služby jazyka k získání colorable položky.

    4. Pomocí informací v barvitelné položce vykreslte text do zobrazení.

## <a name="managed-package-framework-colorizer"></a>Colorizátor architektury spravovaného balíčku
 Architektura spravovaného balíčku (MPF) poskytuje všechny třídy, které jsou nutné k implementaci colorizer. Vaše třída služby <xref:Microsoft.VisualStudio.Package.LanguageService> jazyka by měla zdědit třídu a implementovat požadované metody. Je nutné zadat skener a analyzátor <xref:Microsoft.VisualStudio.Package.IScanner> implementací rozhraní a vrátit instanci tohoto rozhraní z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody (jedna z metod, které musí být implementovány ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě). Další informace naleznete [v tématu Syntax colorizing in a Legacy Language Service](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Viz také
- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Vlastní položky, které lze zabarvit](../../extensibility/internals/custom-colorable-items.md)
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
