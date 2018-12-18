---
title: Barevné zvýrazňování syntaxe ve vlastních editorech | Dokumentace Microsoftu
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
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc4d7f01a813332665a753a8a2aad54bea8a6980
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778667"
---
# <a name="syntax-coloring-in-custom-editors"></a>Barevné zvýrazňování syntaxe ve vlastních editorech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK prostředí editory, včetně základní editor používání jazykových služeb k identifikaci konkrétní syntaktické položky a jejich zobrazení pomocí zadaného barvy pro daný dokument zobrazit.  
  
## <a name="colorization-requirements"></a>Zabarvení požadavky  
 Musí se všechny editory implementace colorizer služba jazyka:  
  
1.  Použijte implementaci objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> ke správě text, který má být barevně zvýrazněné a implementaci objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> poskytnout dokument zobrazení textu.  
  
2.  Získáte rozhraní službě konkrétní jazyk pomocí dotazu na poskytovatele služeb sady VSPackage pomocí identifikační identifikátor GUID služby jazyky.  
  
3.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metoda implementace objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Tato metoda přidruží služba jazyka s <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementace, která sady VSPackage používá ke správě text, který má být obarveny.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Základní Editor využití Colorizer služba jazyka  
 Když se služba jazyka s colorizer získá instanci základní editor, analýze a vykreslování textu ve službě jazyka colorizer neprovádí automaticky bez dalšího zásahu z vaší strany.  
  
 Rozhraní IDE transparentně:  
  
-   Volá colorizer podle potřeby k analýze a analyzovat text, jak je přidat ani upravit v provádění <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Zajišťuje, že zobrazení poskytnutých poskytované zobrazení dokumentu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> se aktualizují a překreslen pomocí informace vrácené colorizer implementace.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Použití editoru jiné než core Colorizer služba jazyka  
 Instance non základním editoru můžete také použít službu barevné zvýrazňování syntaxe služba jazyka, ale musí explicitně načíst a použít colorizer služby a repaint jejich zobrazení dokumentů, sami.  
  
 Provedete to tak vyžaduje jiné než core editor:  
  
1.  Získání objektu colorizer služba jazyka (která implementuje `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Vaše VSPackage toho dosahuje pomocí volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodu na službě jazyka rozhraní.  
  
2.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda požádat o zbarveny konkrétní rozsah textu.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Metoda vrátí pole hodnot, jeden pro každé písmeno v textu span se barevně zvýrazněné. Také identifikuje rozpětí textu jako konkrétního typu, které lze zabarvit položky, jako je například komentář, klíčové slovo nebo datového typu.  
  
3.  Zabarvení informace vrácené <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> repaint a zobrazení jeho textu.  
  
> [!NOTE]
>  Kromě použití služba jazyka colorizer VSPackage můžete použít pro obecné účely barvy textu mechanismus prostředí sady Visual Studio SDK. Další informace o tomto mechanizmu, naleznete v tématu [pomocí písma a barvy](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Viz také  
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementace barevného zvýrazňování syntaxe](../extensibility/internals/implementing-syntax-coloring.md)   
 [Postupy: použití předdefinovaných položek které lze zabarvit](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Vlastní položky, které lze zabarvit](../extensibility/internals/custom-colorable-items.md)

