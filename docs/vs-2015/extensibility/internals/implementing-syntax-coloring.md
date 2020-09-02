---
title: Implementace Obarvení syntaxe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90ff340efb4cbdbe6e2ac43b5b459642120cc099
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64800866"
---
# <a name="implementing-syntax-coloring"></a>Implementace barevného zvýrazňování syntaxe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Když jazyková služba poskytuje barevné zvýrazňování syntaxe, analyzátor převede řádek textu na pole barevně vydaných položek a vrátí typy tokenů odpovídající těmto barevně vydaným položkám. Analyzátor by měl vracet typy tokenů, které patří do seznamu barevně vydaných položek. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zobrazí každou barevnou položku v okně kódu podle atributů přiřazených objektem Colorizer příslušnému typu tokenu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] neurčuje rozhraní analyzátoru a implementace analyzátoru je zcela na vás. Výchozí implementace analyzátoru je však k dispozici v projektu balíčku jazyka sady Visual Studio. Pro spravovaný kód poskytuje rozhraní Managed Package Framework (MPF) úplnou podporu pro Colorizing text.  
  
 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace Obarvení syntaxe naleznete v tématu [Návod: zvýraznění textu](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Postup následovaný editorem, který zabarvovat text  
  
1. Editor získá Colorizer voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objektu.  
  
2. Editor volá metodu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> aby určil, zda Colorizer potřebuje stav každého řádku, aby bylo možné zachovat mimo colorizer.  
  
3. Pokud colorizer vyžaduje, aby byl stav udržován mimo Colorizer, volá Editor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> metodu, aby získala stav prvního řádku.  
  
4. Pro každý řádek ve vyrovnávací paměti volá Editor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodu, která provádí následující kroky:  
  
    1. Řádek textu se předává skeneru, který převede text na tokeny. Každý token Určuje text tokenu a typ tokenu.  
  
    2. Typ tokenu je převeden na index do seznamu položek, které jsou barevně nabarvené.  
  
    3. Informace o tokenu slouží k vyplnění pole tak, aby každý prvek pole odpovídal znaku na řádku. Hodnoty uložené v poli jsou indexy do seznamu barevně napsaných položek.  
  
    4. Stav na konci řádku se vrátí pro každý řádek.  
  
5. Pokud colorizer vyžaduje, aby byl stav udržován, editor ukládá do mezipaměti stav pro daný řádek.  
  
6. Editor vykreslí řádek textu pomocí informací vrácených z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody. To vyžaduje následující kroky:  
  
    1. Pro každý znak na řádku Získá index položky barvy.  
  
    2. Pokud použijete výchozí barevně vybarvené položky, přejděte k seznamu barevně vydaných položek editoru.  
  
    3. V opačném případě zavolejte metodu jazykové služby <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> , abyste získali barevnou položku.  
  
    4. Použijte informace v položce barev k vykreslení textu do zobrazení.  
  
## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Colorizer  
 Sada Managed Package Framework (MPF) poskytuje všechny třídy, které jsou vyžadovány k implementaci rozhraní colorizer. Třída služby jazyka by měla dědit <xref:Microsoft.VisualStudio.Package.LanguageService> třídu a implementovat požadované metody. Je nutné dodat skener a analyzátor implementací <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní a vrátit instanci tohoto rozhraní z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody (jednu z metod, které musí být implementovány ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě). Další informace najdete v tématu [syntaxe Colorizing ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití vestavěných barevných položek](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Vlastní barevné položky](../../extensibility/internals/custom-colorable-items.md)   
 [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
