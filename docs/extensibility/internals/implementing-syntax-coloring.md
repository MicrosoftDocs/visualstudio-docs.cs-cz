---
title: Implementace Obarvení syntaxe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cab338e253cca8c7f8457752980e7f3624317d9c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727029"
---
# <a name="implementing-syntax-coloring"></a>Implementace barevného zvýrazňování syntaxe
Když jazyková služba poskytuje barevné zvýrazňování syntaxe, analyzátor převede řádek textu na pole barevně vydaných položek a vrátí typy tokenů odpovídající těmto barevně vydaným položkám. Analyzátor by měl vracet typy tokenů, které patří do seznamu barevně vydaných položek. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zobrazuje každou barevnou položku v okně kódu podle atributů přiřazených objektem Colorizer k příslušnému typu tokenu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neurčuje rozhraní analyzátoru a implementace analyzátoru je zcela na vás. Výchozí implementace analyzátoru je však k dispozici v projektu balíčku jazyka sady Visual Studio. Pro spravovaný kód poskytuje rozhraní Managed Package Framework (MPF) úplnou podporu pro Colorizing text.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace Obarvení syntaxe naleznete v tématu [Návod: zvýraznění textu](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Postup následovaný editorem, který zabarvovat text

1. Editor získá Colorizer voláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> na objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>.

2. Editor volá metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>, aby určil, jestli Colorizer potřebuje zachovat stav každého řádku mimo colorizer.

3. Pokud colorizer vyžaduje, aby byl stav udržován mimo Colorizer, volá Editor metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>, aby získal stav prvního řádku.

4. Pro každý řádek ve vyrovnávací paměti volá Editor metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, která provádí následující kroky:

    1. Řádek textu se předává skeneru, který převede text na tokeny. Každý token Určuje text tokenu a typ tokenu.

    2. Typ tokenu je převeden na index do seznamu položek, které jsou barevně nabarvené.

    3. Informace o tokenu slouží k vyplnění pole tak, aby každý prvek pole odpovídal znaku na řádku. Hodnoty uložené v poli jsou indexy do seznamu barevně napsaných položek.

    4. Stav na konci řádku se vrátí pro každý řádek.

5. Pokud colorizer vyžaduje, aby byl stav udržován, editor ukládá do mezipaměti stav pro daný řádek.

6. Editor vykreslí řádek textu pomocí informací vrácených z metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>. To vyžaduje následující kroky:

    1. Pro každý znak na řádku Získá index položky barvy.

    2. Pokud použijete výchozí barevně vybarvené položky, přejděte k seznamu barevně vydaných položek editoru.

    3. Jinak Zavolejte metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> služby jazyka, abyste získali barevnou položku.

    4. Použijte informace v položce barev k vykreslení textu do zobrazení.

## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Colorizer
 Sada Managed Package Framework (MPF) poskytuje všechny třídy, které jsou vyžadovány k implementaci rozhraní colorizer. Třída služby jazyka by měla dědit třídu <xref:Microsoft.VisualStudio.Package.LanguageService> a implementovat požadované metody. Je nutné dodat skener a analyzátor implementací rozhraní <xref:Microsoft.VisualStudio.Package.IScanner> a vrátit instanci tohoto rozhraní z metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (jedna z metod, které musí být implementována ve třídě <xref:Microsoft.VisualStudio.Package.LanguageService>). Další informace najdete v tématu [syntaxe Colorizing ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Viz také:
- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Vlastní položky, které lze zabarvit](../../extensibility/internals/custom-colorable-items.md)
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)