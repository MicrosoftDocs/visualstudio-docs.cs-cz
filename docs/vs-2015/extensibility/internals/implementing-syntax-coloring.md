---
title: Implementace barevného zvýrazňování syntaxe | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30a53b1fc04bd08835ccf0ff0b0edb2e5d117fcb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775027"
---
# <a name="implementing-syntax-coloring"></a>Implementace barevného zvýrazňování syntaxe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Když služba jazyka nabízí barevné zvýrazňování syntaxe, analyzátor převede řádek textu do pole položek, které lze zabarvit a vrátí odpovídající tyto které lze zabarvit položky pro typy tokenů. Analyzátor by měl vrátit typy tokenů, které patří do seznamu položek, které lze zabarvit. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] které lze zabarvit položky se zobrazí v okně kódu podle atributů přiřazených objektem colorizer odpovídající typ tokenu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] analyzátor rozhraní, neurčuje a implementaci analyzátoru je zcela na vás. Výchozí implementace analyzátor však je součástí projektu Visual Studio jazykový balíček. Pro spravovaný kód framework spravovaného balíčku (MPF) poskytuje úplnou podporu pro barevné zvýrazňování textu.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace o nový způsob implementace barevné zvýrazňování syntaxe, naleznete v tématu [návod: zvýraznění textu](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Kroky, následuje editoru barevně zvýrazňovat Text  
  
1.  Editoru colorizer získá voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objektu.  
  
2.  Editor volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> metodou ke zjištění, zda colorizer potřebuje stavu každého řádku být zachován mimo colorizer.  
  
3.  Pokud colorizer vyžaduje stav, který má být zachován mimo colorizer, zavolá editoru <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> metodu k získání stavu na prvním řádku.  
  
4.  Pro každý řádek ve vyrovnávací paměti volá editoru <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodu, která provede následující kroky:  
  
    1.  Řádek textu je předáno scanner k převodu textu na tokeny. Každý token Určuje text tokenu a typ tokenu.  
  
    2.  Typ tokenu je převést na index do seznamu, které lze zabarvit položky.  
  
    3.  Informace o tokenu se používá k vyplnění pole tak, aby každý prvek pole odpovídá znaku v řádku. Hodnoty uložené v poli se indexy, do které lze zabarvit položky seznamu.  
  
    4.  Stav na konci řádku se vrací pro každý řádek.  
  
5.  Pokud colorizer vyžaduje stav, který má být zachována, editoru ukládá do mezipaměti stavu pro tento řádek.  
  
6.  Editor vykreslí řádek textu s použitím informací vrácených <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody. To vyžaduje následující kroky:  
  
    1.  Pro každý znak na řádku získání index které lze zabarvit položky.  
  
    2.  Pokud používáte výchozí které lze zabarvit položky, přístup k editoru které lze zabarvit položky seznamu.  
  
    3.  V opačném případě volání služby language <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodu k získání které lze zabarvit položky.  
  
    4.  Pomocí informací v které lze zabarvit položky k vykreslení textu do zobrazení.  
  
## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Colorizer  
 Rozhraní spravovaného balíčku (MPF) poskytuje všechny třídy, které jsou nutné k implementaci colorizer. Vaše třída jazyka služby by měla dědit <xref:Microsoft.VisualStudio.Package.LanguageService> třídy a implementuje požadované metody. Musíte zadat analyzátor a skener implementací <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní a vracet instanci rozhraní z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> – metoda (jedné z metod, které je třeba implementovat v <xref:Microsoft.VisualStudio.Package.LanguageService> třídy). Další informace najdete v tématu [barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití předdefinovaných položek které lze zabarvit](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Vlastní položky které lze zabarvit](../../extensibility/internals/custom-colorable-items.md)   
 [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

