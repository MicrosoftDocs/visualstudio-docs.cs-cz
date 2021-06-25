---
title: 'Postupy: Podpora osnovy ve službě starší verze jazyka | Microsoft Docs'
description: Naučte se poskytovat podporu pro osnovu, rozšiřování nebo sbalení různých oblastí textu ve službě starší verze jazyka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 028d1a9aae21aae8c6368e4eea3820aabd200be6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901796"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Postupy: Podpora osnovy ve službě starší verze jazyka
Osnova slouží k rozbalení nebo sbalení různých oblastí textu. Způsob použití osnovy lze definovat různě v různých jazycích. Další informace najdete v tématu [Osnova](../../ide/outlining.md).

 Služby starší verze jazyka jsou implementovány jako součást balíčku VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace osnovy najdete v tématu [Názorný postup: Osnova](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Doporučujeme, abyste nové rozhraní API editoru začali používat co nejdříve. Tím se zlepší výkon služby jazyka a umožní vám to využívat nové funkce editoru.

 Následující příklad ukazuje, jak tento příkaz podporovat pro službu jazyka.

## <a name="to-support-outlining"></a>Podpora osnovy

1. Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> na objekt služby jazyka.

2. Voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metody pro aktuální objekt relace osnovy přidáte nové oblasti osnovy.

## <a name="robust-programming"></a>Robustní programování
 Když uživatel vybere v **nabídce**  Osnova možnost Sbalit do definic, integrované vývojové prostředí (IDE) zavolá ve vaší <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> jazykové službě.

 Při volání této metody předá integrované vývojové prostředí ukazatel (ukazatel na vyrovnávací paměť textu) a (ukazatel na aktuální relaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> osnovy).

 Metodu pro více oblastí osnovy můžete volat zadáním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> těchto oblastí v `rgOutlnReg` parametru . Parametr `rgOutlnReg` je <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> struktura. Tento proces umožňuje určit různé charakteristiky skryté oblasti, například to, jestli je konkrétní oblast rozbalená nebo sbalená.

> [!NOTE]
> Při skrývání znaků nového řádku buďte opatrní. Skrytý text by měl být od začátku prvního řádku až po poslední znak posledního řádku v oddílu, takže poslední znak nového řádku by měl být viditelný.

## <a name="see-also"></a>Viz také
- [Postupy: Poskytování podpory skrytého textu ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Postupy: Rozšířená podpora osnovy ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
