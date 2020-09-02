---
title: Dokončování příkazů ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 163eb0f23716fa2f036d07612b741c0c9419b92e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64803869"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Dokončování příkazů ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dokončování příkazů je proces, pomocí kterého služba jazyka pomáhá uživatelům dokončit klíčové slovo jazyka nebo element, které začali psát v základním editoru. Toto téma popisuje, jak funguje dokončování příkazů a jak ho implementovat ve vaší jazykové službě.  
  
 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Chcete-li získat další informace o novém způsobu implementace příkazu, přečtěte si [Návod: zobrazení dokončování příkazů](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.  
  
## <a name="implementing-statement-completion"></a>Implementace dokončování příkazů  
 V základním editoru dokončování příkazů aktivuje speciální uživatelské rozhraní, které vám interaktivně pomůže snadněji a rychle psát kód. Dokončování příkazů pomáhá zobrazit relevantní objekty nebo třídy, pokud jsou potřeba, což zabrání, abyste si zapamatovali určité prvky nebo museli hledat v tématu Referenční informace nápovědy.  
  
 Aby bylo možné implementovat dokončování příkazů, musí mít váš jazyk Trigger dokončování příkazů, který lze analyzovat. Například [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] používá operátor tečky (.), zatímco [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] používá operátor šipky (->). Služba jazyka může použít více než jednu Trigger k zahájení dokončování příkazů. Tyto triggery jsou naprogramovány ve filtru příkazů.  
  
## <a name="command-filters-and-triggers"></a>Filtry příkazů a triggery  
 Filtry příkazů zachycují výskyty triggeru nebo triggerů. Chcete-li přidat filtr příkazů do zobrazení, implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a připojte jej k zobrazení voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody. Stejný filtr příkazů () můžete použít <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pro všechny aspekty vaší jazykové služby, jako je například dokončování příkazů, značky chyb a tipy metod. Další informace najdete v tématu [zachycení příkazů služby starší verze jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Při zadání triggeru v editoru – konkrétně do vyrovnávací paměti textu – vaše jazyková služba pak zavolá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodu. To způsobí, že editor zobrazí uživatelské rozhraní, aby si uživatel mohl vybrat z kandidátů na dokončení příkazu. Tato metoda vyžaduje, abyste implementovali <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> a <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> příznaky jako parametry. Seznam položek dokončení se zobrazí v rozevíracím seznamu. Když uživatel pokračuje v psaní, výběr v rámci seznamu se aktualizuje tak, aby odrážel nejbližší typ posledních znaků. Základní editor implementuje uživatelské rozhraní pro dokončování příkazů, ale jazyková služba musí implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> rozhraní pro definování sady položek pro dokončení kandidátů pro daný příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy zachytávání služby starší verze jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
