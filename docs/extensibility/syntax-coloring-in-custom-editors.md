---
title: Barevné zvýrazňování syntaxe ve vlastních editorech | Microsoft Docs
description: Seznamte se s barvami barev v sadě Visual Studio Environment SDK vlastní editory, která zobrazuje zadané barvy pro dané zobrazení dokumentu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 06cd4ae1db1187cc650a4fd9486f4b1686c6b015
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063692"
---
# <a name="syntax-coloring-in-custom-editors"></a>Barevné zvýrazňování syntaxe ve vlastních editorech
Editory sady SDK prostředí sady Visual Studio, včetně základního editoru, používají jazykové služby k identifikaci konkrétních syntaktických položek a jejich zobrazení se zadanými barvami pro dané zobrazení dokumentu.

## <a name="colorization-requirements"></a>Požadavky na zabarvení
 Všechny editory implementující Colorizer jazykové služby musí:

1. Použijte objekt implementující <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> ke správě textu, který má být zabarvení, a objekt, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> který implementuje k poskytnutí zobrazení dokumentu textu.

2. Získejte rozhraní pro konkrétní jazykovou službu pomocí dotazování poskytovatele služeb VSPackage pomocí identifikačního identifikátoru GUID služby jazyka.

3. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodu implementující objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Tato metoda přidruží službu jazyka k <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementaci, kterou VSPackage používá ke správě textu, který se má obarvit.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Základní použití editoru Colorizer jazykové služby
 Když se služba jazyka s Colorizer získá instancí základního editoru, analyzuje a vykresluje text pomocí Colorizer služby jazyka automaticky, aniž by to vyžadovalo další zásah na vaší straně.

 Integrované vývojové prostředí (IDE) transparentně:

- Volá Colorizer podle potřeby pro analýzu a analýzu textu při jeho přidání nebo úpravě v implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .

- Zajistí, aby se zobrazení dodané zobrazením dokumentu, které poskytuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementace, aktualizovalo a překresleno s použitím informací vrácených colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Nezákladní použití editoru Colorizer jazykové služby
 Instance nezákladního editoru můžou také používat službu barevného zabarvení syntaxe služby jazyka, ale musí explicitně načítat a používat Colorizer služby a převádět jejich zobrazení dokumentů sami.

 K tomu je potřeba, aby editor bez jádra:

1. Získejte objekt Colorizer jazykové služby (který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). VSPackage to dělá voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody v rozhraní jazykové služby.

2. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodu, aby požádala o barevné zabarvení konkrétního rozsahu textu.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Metoda vrátí pole hodnot, jednu pro každé písmeno v rozsahu textu, který je barevně barevný. Určuje také rozsah textu jako konkrétní typ barevné položky, jako je například komentář, klíčové slovo nebo datový typ.

3. Použijte informace o vybarvení vrácené funkcí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> k překreslení a zobrazení jejího textu.

> [!NOTE]
> Kromě použití Colorizer jazykové služby se sada VSPackage může rozhodnout použít mechanismus barevného zvýraznění textu sady Visual Studio pro obecné účely. Další informace o tomto mechanismu najdete v tématu [Použití písem a barev](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Viz také

- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementace barevného zvýrazňování syntaxe](../extensibility/internals/implementing-syntax-coloring.md)
- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Vlastní položky, které lze zabarvit](../extensibility/internals/custom-colorable-items.md)