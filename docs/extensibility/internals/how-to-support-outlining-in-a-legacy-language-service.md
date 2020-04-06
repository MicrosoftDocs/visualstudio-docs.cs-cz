---
title: 'Postup: Podpora osnovy ve službě starší jazyk | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707909"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Postup: Podpora osnovy ve starší jazykové službě
Osnova se používá k rozbalení nebo sbalení různých oblastí textu. Způsob, jakým se osnova používá, lze definovat odlišně různými jazyky. Další informace naleznete [v tématu Osnova](../../ide/outlining.md).

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace osnovy najdete v [tématu Návod: Osnova](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

 Následující ukazuje, jak podporovat tento příkaz pro službu jazyka.

## <a name="to-support-outlining"></a>Chcete-li podpořit osnovu

1. Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> objekt služby jazyka.

2. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> aktuálního objektu relace osnovy přidejte nové oblasti osnovy.

## <a name="robust-programming"></a>Robustní programování
 Když uživatel vybere **sbalit definice v** nabídce **Osnova,** rozhraní IDE zavolá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> na vaši jazykovou službu.

 Při volání této metody ide předá v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> ukazatel (ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> vyrovnávací paměť textu) a (ukazatel na aktuální relaci osnovy).

 Metodu pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> více oblastí osnovy můžete volat `rgOutlnReg` zadáním těchto oblastí v parametru. Parametr `rgOutlnReg` je <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> struktura. Tento proces umožňuje určit různé charakteristiky skryté oblasti, například zda je určitá oblast rozbalená nebo sbalená.

> [!NOTE]
> Buďte opatrní při skrývání znaků nového řádku. Skrytý text by měl přesahovat od začátku prvního řádku do posledního znaku posledního řádku v oddílu, přičemž konečný znak nového řádku by měl být viditelný.

## <a name="see-also"></a>Viz také
- [Postup: Poskytnutí skryté textové podpory ve službě starších jazyků](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Postup: Poskytování rozšířené podpory ve starší jazykové službě](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
