---
title: Implementace Obarvení syntaxe | Microsoft Docs
description: Naučte se implementovat barevné zvýrazňování syntaxe v aplikaci Visual Studio pomocí funkcí jazykové služby spravovaného balíčku rozhraní (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c46cea481eceadef5118388633f84402870a209
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069605"
---
# <a name="implementing-syntax-coloring"></a>Implementace barevného zvýrazňování syntaxe
Když jazyková služba poskytuje barevné zvýrazňování syntaxe, analyzátor převede řádek textu na pole barevně vydaných položek a vrátí typy tokenů odpovídající těmto barevně vydaným položkám. Analyzátor by měl vracet typy tokenů, které patří do seznamu barevně vydaných položek. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zobrazí každou barevnou položku v okně kódu podle atributů přiřazených objektem Colorizer příslušnému typu tokenu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neurčuje rozhraní analyzátoru a implementace analyzátoru je zcela na vás. Výchozí implementace analyzátoru je však k dispozici v projektu balíčku jazyka sady Visual Studio. Pro spravovaný kód poskytuje rozhraní Managed Package Framework (MPF) úplnou podporu pro Colorizing text.

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
- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Vlastní položky, které lze zabarvit](../../extensibility/internals/custom-colorable-items.md)
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
