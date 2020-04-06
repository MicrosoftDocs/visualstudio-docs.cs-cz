---
title: Dokončení výpisu ve službě staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704933"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Dokončování příkazů ve službě starší verze jazyka
Dokončení výkazu je proces, kterým služba jazyka pomáhá uživatelům dokončit klíčové slovo jazyka nebo prvek, který začali psát v editoru jádra. Toto téma popisuje, jak funguje dokončování příkazů a jak jej implementovat ve vaší jazykové službě.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace dokončování příkazů naleznete v [tématu Návod: Zobrazení dokončení výkazu](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="implementing-statement-completion"></a>Dokončení prováděcího výkazu
 V editoru jádra prohlášení dokončování aktivuje speciální ui, které interaktivně pomáhá snadněji a rychleji psát kód. Dokončení výkazu pomáhá zobrazením relevantních objektů nebo tříd v případě potřeby, což zabraňuje nutnosti pamatovat si určité prvky nebo je muset vyhledat v referenčním tématu nápovědy.

 Chcete-li implementovat dokončení příkazu, musí mít váš jazyk aktivační událost dokončení příkazu, který lze analyzovat. Například [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] používá operátor tečka (.), [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] zatímco používá operátor šipky (>). Služba jazyka může k zahájení dokončování výkazu použít více aktivační ch od se k dispozici více aktivační ch od sekcích. Tyto aktivační události jsou naprogramovány ve filtru příkazů.

## <a name="command-filters-and-triggers"></a>Filtry a aktivační události příkazů
 Filtry příkazů zachycují výskyty aktivační události nebo aktivačních událostí. Chcete-li přidat filtr příkazů do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zobrazení, implementujte rozhraní a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> připojte jej k zobrazení voláním metody. Stejný filtr příkazů (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) můžete použít pro všechny aspekty služby jazyka, jako je například dokončování příkazů, značky chyb a tipy metod. Další informace naleznete [v tématu Intercepting Legacy Language Service Commands](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Když je aktivační událost zadána do editoru – konkrétně do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> textové vyrovnávací paměti – vaše jazyková služba pak volá metodu. To způsobí, že editor vyvolat uživatelské rozhraní tak, aby uživatel může vybrat z kandidátů doplnění příkazu. Tato metoda vyžaduje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> a příznaky jako parametry. Seznam položek dokončení se zobrazí v poli rolovacího seznamu. Jak uživatel pokračuje v psaní, výběr v seznamu se aktualizuje tak, aby odrážel nejbližší shodu s nejnovějšími zadanými znaky. Základní editor implementuje uživatelské rozhraní pro dokončení příkazu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> ale služba jazyka musí implementovat rozhraní k definování sady položek dokončení kandidáta pro příkaz.

## <a name="see-also"></a>Viz také
- [Příkazy zachytávání služby starší verze jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
