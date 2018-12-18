---
title: Vlastní editorů zvýrazňování syntaxe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e087e82754244b7abda530f733a6047447f4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139458"
---
# <a name="syntax-coloring-in-custom-editors"></a>Vlastní editorů zvýrazňování syntaxe
Visual Studio SDK prostředí editory, včetně editoru základní pomocí služby jazyk identifikovat konkrétní syntaktické položky a jejich zobrazení pomocí zadaného barev pro zobrazení daného dokumentu.

## <a name="colorization-requirements"></a>Požadavky na zabarvení
 Musí být všechny editory implementace colorizer služba jazyka:

1.  Použít implementaci objekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> ke správě text, který má být obarvené a k objektu implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zajistit zobrazení dokumentů textu.

2.  Získejte rozhraní službě konkrétní jazyk pomocí dotazu na poskytovatele služeb VSPackage pomocí služby jazyky identifikační GUID.

3.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metoda implementace objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Tato metoda přidruží službu jazyk s <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementace, která VSPackage používá ke správě text, který má být obarvené.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Použití editoru základní Colorizer služba jazyka
 Když je služba jazyka s colorizer získat instanci editoru jádra, analýze a vykreslování textu ve colorizer služba jazyka probíhá automaticky bez nutnosti zásahu další z vaší strany.

 Prostředí IDE transparentně:

-   Volá colorizer podle potřeby analyzovat a analýza textu, jako je přidat ani upravit v provádění <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

-   Zajišťuje, že zobrazení poskytl dokumentu zobrazených <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementace je aktualizovat a překreslen pomocí informací o vrácený colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Použití editoru vedlejší Colorizer služba jazyka
 Instance editoru vedlejší můžete také použít službu zabarvení syntaxe služba jazyka, ale musí explicitně načíst a použít colorizer služby a překreslit jejich zobrazení dokumentů, sami.

 K tomuto účelu musí vedlejší editoru:

1.  Získejte objekt colorizer služba jazyka (které implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). VSPackage provede voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metoda v rozhraní služba jazyka.

2.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda k vyžádání, že se obarvené konkrétní rozpětí textu.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Metoda vrátí hodnotu pole hodnot, jeden pro každou písmeno v textu span se obarvené. Také identifikuje jako konkrétní typ colorable položkou, například komentáře, – klíčové slovo nebo datový typ rozpětí textu.

3.  Vrácené informace zabarvení <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> překreslit a zobrazit jeho text.

> [!NOTE]
> Kromě používání colorizer služba jazyka, můžete vybrat VSPackage použít pro obecné účely text-barevné zvýrazňování mechanismus SDK prostředí Visual Studio. Další informace o tento mechanismus najdete v tématu [pomocí písma a barev](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Viz také

- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementace barevného zvýrazňování syntaxe](../extensibility/internals/implementing-syntax-coloring.md)
- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Vlastní položky, které lze zabarvit](../extensibility/internals/custom-colorable-items.md)