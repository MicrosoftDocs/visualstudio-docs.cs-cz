---
title: 'Postupy: podpora sbalení ve službě starší verze jazyka | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707909"
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
