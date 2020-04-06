---
title: Syntaxe Zbarvení ve vlastních editorech | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699341"
---
# <a name="syntax-coloring-in-custom-editors"></a>Barevné zvýrazňování syntaxe ve vlastních editorech
Editory sady Visual Studio Environment SDK, včetně editoru jádra, používají jazykové služby k identifikaci konkrétních syntaktických položek a zobrazují je s určenými barvami pro dané zobrazení dokumentu.

## <a name="colorization-requirements"></a>Požadavky na vybarvení
 Všechny editory, které implementují kolorizátor služby jazyka, musí:

1. Pomocí objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementujícího ke správě textu, který <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> má být obarven, a objektem implementujícím k vytvoření zobrazení dokumentu textu.

2. Získejte rozhraní pro konkrétní jazykovou službu dotazem na poskytovatele služeb VSPackage pomocí identifikačního identifikátoru GUID služby jazyky.

3. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody objektu implementující <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Tato metoda přidruží <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> jazykovou službu k implementaci, kterou VSPackage používá ke správě textu, který má být obarven.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Core Editor Použití colorizer služby jazyka
 Pokud je jazyková služba s colorizérem získána instancí editoru jádra, analýza a vykreslování textu probarvách služby jazyka se provádí automaticky bez nutnosti dalšího zásahu z vaší strany.

 IDE transparentně:

- Volá colorizer podle potřeby analyzovat a analyzovat text, jak je <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>přidán nebo změněn v implementaci .

- Zajišťuje, že zobrazení poskytované zobrazení dokumentu poskytované <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementací je aktualizována a překreslena pomocí informací vrácených colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Použití nejádrového editoru colorizátoru jazykové služby
 Instance editoru mimo jádro můžete také použít službu syntaxe vybarvení jazyka, ale musí explicitně načíst a použít služby colorizer a překreslit jejich zobrazení dokumentu sami.

 Chcete-li to provést, musí editor nejádrových procesorů:

1. Získejte jazyk služby colorizer objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>(který implementuje a ). VSPackage to provádí voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody na rozhraní služby jazyka.

2. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody požadovat, aby určité rozpětí textu být colorized.

     Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> vrátí pole hodnot, jeden pro každé písmeno v textu rozpětí je obarven. Také identifikuje rozsah textu jako určitý typ barevné položky, například komentář, klíčové slovo nebo datový typ.

3. Pomocí informací o vybarvení vrácených změnou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> barvy přemalujte a zobrazte jejich text.

> [!NOTE]
> Kromě použití colorizer služby jazyka VSPackage můžete použít univerzální Visual Studio prostředí SDK text omalovánky mechanismus. Další informace o tomto mechanismu naleznete v [tématu Použití písem a barev](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="see-also"></a>Viz také

- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementace barevného zvýrazňování syntaxe](../extensibility/internals/implementing-syntax-coloring.md)
- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Vlastní položky, které lze zabarvit](../extensibility/internals/custom-colorable-items.md)
