---
title: Dokončování příkazů ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4c813052892c21a6a3e04560452b503205df117
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723224"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Dokončování příkazů ve službě starší verze jazyka
Dokončování příkazů je proces, pomocí kterého služba jazyka pomáhá uživatelům dokončit klíčové slovo jazyka nebo element, které začali psát v základním editoru. Toto téma popisuje, jak funguje dokončování příkazů a jak ho implementovat ve vaší jazykové službě.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Chcete-li získat další informace o novém způsobu implementace příkazu, přečtěte si [Návod: zobrazení dokončování příkazů](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="implementing-statement-completion"></a>Implementace dokončování příkazů
 V základním editoru dokončování příkazů aktivuje speciální uživatelské rozhraní, které vám interaktivně pomůže snadněji a rychle psát kód. Dokončování příkazů pomáhá zobrazit relevantní objekty nebo třídy, pokud jsou potřeba, což zabrání, abyste si zapamatovali určité prvky nebo museli hledat v tématu Referenční informace nápovědy.

 Aby bylo možné implementovat dokončování příkazů, musí mít váš jazyk Trigger dokončování příkazů, který lze analyzovat. Například [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] používá operátor tečky (.), zatímco [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] používá operátor šipky (->). Služba jazyka může použít více než jednu Trigger k zahájení dokončování příkazů. Tyto triggery jsou naprogramovány ve filtru příkazů.

## <a name="command-filters-and-triggers"></a>Filtry příkazů a triggery
 Filtry příkazů zachycují výskyty triggeru nebo triggerů. Chcete-li přidat filtr příkazů do zobrazení, implementujte rozhraní <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> a připojte ho k zobrazení voláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>. Stejný filtr příkazů (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) můžete použít pro všechny aspekty vaší jazykové služby, jako je například dokončování příkazů, značky chyb a tipy metod. Další informace najdete v tématu [zachycení příkazů služby starší verze jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Při zadání triggeru v editoru – konkrétně do vyrovnávací paměti textu – vaše jazyková služba pak zavolá metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>. To způsobí, že editor zobrazí uživatelské rozhraní, aby si uživatel mohl vybrat z kandidátů na dokončení příkazu. Tato metoda vyžaduje, abyste implementovali <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> a jako parametry <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> příznaky. Seznam položek dokončení se zobrazí v rozevíracím seznamu. Když uživatel pokračuje v psaní, výběr v rámci seznamu se aktualizuje tak, aby odrážel nejbližší typ posledních znaků. Základní editor implementuje uživatelské rozhraní pro dokončování příkazů, ale jazyková služba musí implementovat rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> pro definování sady položek pro dokončení kandidátů pro daný příkaz.

## <a name="see-also"></a>Viz také:
- [Příkazy zachytávání služby starší verze jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md)