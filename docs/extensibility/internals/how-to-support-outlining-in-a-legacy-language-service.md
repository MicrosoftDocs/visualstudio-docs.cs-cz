---
title: 'Postupy: podpora sbalení ve službě starší verze jazyka | Microsoft Docs'
description: Naučte se poskytovat podporu pro sbalení, rozbalení nebo sbalení různých oblastí textu ve službě starší verze jazyka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 0c275a6a466cc58187293f6ebd84a39fdf8064e6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078682"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Postupy: podpora sbalení ve službě starší verze jazyka
K rozbalení nebo sbalení různých oblastí textu se používá osnova. Způsob, jakým se používá sbalení, lze definovat odlišně podle různých jazyků. Další informace najdete v tématu [popisujícím sbalení](../../ide/outlining.md).

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Chcete-li získat další informace o novém způsobu implementace sbalení, přečtěte si téma [Návod: sbalení](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

 Následující příklad ukazuje, jak tento příkaz podporovat pro službu jazyka.

## <a name="to-support-outlining"></a>Podpora sbalení

1. Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> u objektu jazykové služby.

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>Chcete-li přidat nové oblasti osnovy, zavolejte na aktuální objekt relace pro sbalení.

## <a name="robust-programming"></a>Robustní programování
 Když uživatel vybere **sbalit do definice** v nabídce **Osnova** , rozhraní IDE zavolá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> vaši jazykovou službu.

 Při volání této metody rozhraní IDE předává <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> ukazatel (ukazatel na vyrovnávací paměť textu) a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (ukazatel na aktuální relaci sbalení).

 Můžete zavolat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metodu pro více oblastí osnovy zadáním těchto oblastí v `rgOutlnReg` parametru. `rgOutlnReg`Parametr je <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> Struktura. Tento proces vám umožní určit různé charakteristiky skryté oblasti, například zda je konkrétní oblast rozbalená nebo sbalená.

> [!NOTE]
> Při skrývání znaků na novém řádku buďte opatrní. Skrytý text by měl být od začátku prvního řádku až k poslednímu znaku posledního řádku v oddílu, takže se zobrazí poslední znak na novém řádku.

## <a name="see-also"></a>Viz také
- [Postupy: poskytování podpory skrytého textu ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Postupy: poskytování rozšířené podpory sbalení ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
