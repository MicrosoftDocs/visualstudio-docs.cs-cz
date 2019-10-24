---
title: Barevné zvýrazňování syntaxe ve vlastních editorech | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4302f463d93776d17be0251e6194375c15adc19
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718758"
---
# <a name="syntax-coloring-in-custom-editors"></a>Barevné zvýrazňování syntaxe ve vlastních editorech
Editory sady SDK prostředí sady Visual Studio, včetně základního editoru, používají jazykové služby k identifikaci konkrétních syntaktických položek a jejich zobrazení se zadanými barvami pro dané zobrazení dokumentu.

## <a name="colorization-requirements"></a>Požadavky na zabarvení
 Všechny editory implementující Colorizer jazykové služby musí:

1. Použijte objekt implementující <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> ke správě textu, který má být zabarvení, a objekt implementující <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> k poskytnutí zobrazení dokumentu textu.

2. Získejte rozhraní pro konkrétní jazykovou službu pomocí dotazování poskytovatele služeb VSPackage pomocí identifikačního identifikátoru GUID služby jazyka.

3. Zavolejte metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> objektu, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Tato metoda přidruží službu jazyka k <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementaci, kterou VSPackage používá ke správě textu, který se má obarvit.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Základní použití editoru Colorizer jazykové služby
 Když se služba jazyka s Colorizer získá instancí základního editoru, analyzuje a vykresluje text pomocí Colorizer služby jazyka automaticky, aniž by to vyžadovalo další zásah na vaší straně.

 Integrované vývojové prostředí (IDE) transparentně:

- Volá Colorizer podle potřeby pro analýzu a analýzu textu při jeho přidání nebo úpravě v implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

- Zajistí, aby se displej dodaný zobrazením dokumentu, který poskytuje implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, aktualizoval a překreslí pomocí informací vrácených colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Nezákladní použití editoru Colorizer jazykové služby
 Instance nezákladního editoru můžou také používat službu barevného zabarvení syntaxe služby jazyka, ale musí explicitně načítat a používat Colorizer služby a převádět jejich zobrazení dokumentů sami.

 K tomu je potřeba, aby editor bez jádra:

1. Získejte objekt Colorizer jazykové služby (který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). VSPackage to provede voláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> v rozhraní jazykové služby.

2. Zavolejte metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, aby požádala o barevné zabarvení konkrétního rozsahu textu.

     Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> vrátí pole hodnot, jednu pro každé písmeno v rozsahu textu, který je barevně barevný. Určuje také rozsah textu jako konkrétní typ barevné položky, jako je například komentář, klíčové slovo nebo datový typ.

3. Použijte informace o zabarvení vrácené <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> k překreslení a zobrazení jejího textu.

> [!NOTE]
> Kromě použití Colorizer jazykové služby se sada VSPackage může rozhodnout použít mechanismus barevného zvýraznění textu sady Visual Studio pro obecné účely. Další informace o tomto mechanismu najdete v tématu [Použití písem a barev](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Viz také:

- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementace barevného zvýrazňování syntaxe](../extensibility/internals/implementing-syntax-coloring.md)
- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Vlastní položky, které lze zabarvit](../extensibility/internals/custom-colorable-items.md)