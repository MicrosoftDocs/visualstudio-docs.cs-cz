---
title: Barevné zvýrazňování syntaxe ve službě starší verze jazyka | Dokumentace Microsoftu
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
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 99082388534e39d02731e065bf586d6d221c67aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784062"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Barevné zvýrazňování syntaxe ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] barevné zvýrazňování služby se používá k identifikaci prvky jazyka a jejich zobrazení pomocí zadaného barev v editoru.  
  
## <a name="colorizer-model"></a>Colorizer modelu  
 Implementuje služba jazyka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní, které se pak použije v editorech. Tato implementace je samostatný objekt ze služby jazyka, jak je znázorněno na následujícím obrázku.  
  
 ![Obrázek SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Jednoduché colorizer modelu  
  
> [!NOTE]
>  Je oddělená od hlavní služby barevného označování syntaxe [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mechanismus pro barevné zvýrazňování textu. Další informace o Obecné [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] mechanismus podporuje barevné zvýrazňování, naleznete v tématu [pomocí písma a barvy](../../extensibility/using-fonts-and-colors.md).  
  
 Kromě colorizer služba jazyka můžete zadat vlastní které lze zabarvit položky, které jsou používány reklamy, že poskytuje vlastní, které lze zabarvit položky pomocí editoru. Můžete to provést prostřednictvím implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> na stejný objekt, který implementuje rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní. Vrátí počet položek, které lze zabarvit vlastní, když volá editoru <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metoda a vrací jednotlivé položky vlastní které lze zabarvit při volání editoru <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metody.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Metoda vrátí objekt, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> rozhraní. Pokud služba jazyka podporuje barevné 24-bit nebo vysoké hodnoty, musí implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní na stejný objekt jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> rozhraní.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak VSPackage používá Colorizer služby jazyka  
  
1.  Sady VSPackage, musíte získat příslušné jazykové služby, který vyžaduje službu jazyka VSPackage provést následující kroky:  
  
    1.  Použijte implementaci objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> rozhraní se získat text, který má být obarveny.  
  
         Text obvykle bývá zobrazen, použití objektu, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní.  
  
    2.  Získáte službu jazyka pomocí dotazu na poskytovatele služeb balíčku VSPackage pro službu jazyka identifikátor GUID. Jazykové služby jsou označeny v registru příponu souboru.  
  
    3.  Přidružit služba jazyka s <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> voláním jeho <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metoda.  
  
2.  Sady VSPackage teď můžete získat a používat objekt colorizer následujícím způsobem:  
  
    > [!NOTE]
    >  Rozšíření VSPackages, které používají základní editor není potřeba získat jazyk služby colorizer objekty explicitně. Jakmile instance základní editor získá služby příslušný jazyk, provádět všechny úlohy barevné zvýraznění je vidět tady.  
  
    1.  Získání objektu colorizer jazyková služba, která implementuje `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> rozhraní voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metoda na službě jazyka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objektu.  
  
    2.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda colorizer informace pro konkrétní rozsah textu.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Vrátí pole hodnot, jeden pro každý znak v rozsahu textu se barevně zvýrazněné. Hodnoty jsou indexů do seznamu které lze zabarvit položek, které lze zabarvit položky seznamu výchozích udržuje základní editor nebo které lze zabarvit vlastní položky seznamu udržuje samotnou službu jazyka.  
  
    3.  Zabarvení informace vrácené <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodu pro zobrazení vybraného textu.  
  
> [!NOTE]
>  Kromě použití colorizer služby jazyka, VSPackage můžete také použít pro obecné účely [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] text obarvení mechanismus. Další informace o tomto mechanizmu, naleznete v tématu [pomocí písma a barvy](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Implementace barevného zvýrazňování syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)  
 Tento článek popisuje, jak editor přistupuje k službě jazyka barevné zvýrazňování syntaxe a služba jazyka musí implementovat pro podporu syntaxe barevné zvýrazňování.  
  
 [Postupy: Použití předdefinovaných položek, které lze zabarvit](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Ukazuje, jak používat integrované které lze zabarvit položky ze služby jazyka.  
  
 [Vlastní položky, které lze zabarvit](../../extensibility/internals/custom-colorable-items.md)  
 Popisuje, jak implementovat vlastní, které lze zabarvit položky.  
  
## <a name="see-also"></a>Viz také  
 [Použití písem a barev](../../extensibility/using-fonts-and-colors.md)

