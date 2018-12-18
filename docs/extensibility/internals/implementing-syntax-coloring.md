---
title: Implementace barevné zvýrazňování syntaxe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5502bd30378130e5977d427acb9df5b73226a05b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131852"
---
# <a name="implementing-syntax-coloring"></a>Implementace barevné zvýrazňování syntaxe
Když služba jazyka poskytuje zabarvení syntaxe, analyzátor převede na řádku textu do pole colorable položek a vrátí odpovídající tyto colorable položky pro typy tokenů. Analyzátor by měl vrátit typy tokenů, které patří do colorable položek seznamu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zobrazuje každou colorable položku v okně kód podle atributy přiřazené objektem colorizer odpovídající typ tokenu.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neurčuje analyzátor rozhraní, a analyzátor implementace je zcela na vás. Výchozí implementaci analyzátor však je k dispozici v projektu jazyka balíček Visual Studio. Pro spravovaný kód rozhraní spravované balíčku (MPF) podporuje dokončení barevné text.  
  
 Starší verze jazyka služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkce služby jazyk je použití MEF rozšíření. Další informace o nový způsob implementace zvýrazňování syntaxe, najdete v tématu [návod: zvýraznění textu](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat co nejdříve editoru nové rozhraní API. Tím zvýšit výkon služby jazyk a umožňují využívat výhod nových funkcí editoru.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Kroky, za nímž následuje editoru Kolorovat Text  
  
1.  Editor voláním získá colorizer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objektu.  
  
2.  Editor volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> metoda k určení, zda colorizer musí stav každého řádku být zachován mimo colorizer.  
  
3.  Pokud colorizer vyžaduje stav, který má být zachován mimo colorizer, editor volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> metoda získat stav prvního řádku.  
  
4.  Pro každý řádek ve vyrovnávací paměti editoru volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodu, která provede následující kroky:  
  
    1.  Řádek textu je předán skener převést text do tokenů. Každý token Určuje text tokenu a typ tokenu.  
  
    2.  Typ tokenu je převést na index do colorable položky seznamu.  
  
    3.  Informace o tokenu se používá k vyplnění pole tak, aby každý element pole odpovídá znak v řádku. Hodnoty uložené v poli jsou indexy do colorable položky seznamu.  
  
    4.  Stav na konci řádku se vrátí pro každý řádek.  
  
5.  Pokud colorizer vyžaduje stav, který má být zachována, editor ukládá do mezipaměti, stav daného řádku.  
  
6.  Editor vykreslí řádek textu s použitím vrácených z informací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda. To vyžaduje následující kroky:  
  
    1.  Pro každý znak v řádku získáte index colorable položky.  
  
    2.  Pokud používáte výchozí colorable položky, přístup k seznamu colorable položky editoru.  
  
    3.  Jinak volání služby jazyk <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metoda získat colorable položky.  
  
    4.  Pomocí informací v položce colorable k vykreslení text do zobrazení.  
  
## <a name="managed-package-framework-colorizer"></a>Colorizer Framework spravované balíčku  
 Rozhraní framework spravované balíčku (MPF) poskytuje všechny třídy, které jsou nutné k implementaci colorizer. Třídě jazyka služby musí dědit <xref:Microsoft.VisualStudio.Package.LanguageService> třídy a implementovat požadované metody. Musíte zadat skeneru a analyzátor implementací <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní a vrátit instanci tohoto rozhraní <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> – metoda (jednu z metod, které musí být implementován v <xref:Microsoft.VisualStudio.Package.LanguageService> – třída). Další informace najdete v tématu [syntaxe barevné ve službě jazyk starší](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití předdefinované Colorable položek](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Vlastní Colorable položky](../../extensibility/internals/custom-colorable-items.md)   
 [Vývoj služby jazyk starší verze](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)