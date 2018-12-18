---
title: Dokončování příkazů ve službě jazyk starší | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d76face8f43bcb428a9c3b997083f8299d332cc8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131324"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Dokončování příkazů ve službě jazyk starší verze
Dokončování příkazů je proces, pomocí kterého služba jazyka pomáhá uživatelům dokončit klíčové slovo jazyka nebo element, který zahájil zadáním v editoru jádra. Toto téma popisuje, jak dokončování funguje a jak implementovat ve službě jazyk.  
  
 Starší verze jazyka služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkce služby jazyk je použití MEF rozšíření. Další informace o nový způsob implementace dokončování příkazů, najdete v tématu [návod: zobrazení dokončování](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat co nejdříve editoru nové rozhraní API. Tím zvýšit výkon služby jazyk a umožňují využívat výhod nových funkcí editoru.  
  
## <a name="implementing-statement-completion"></a>Implementace dokončování příkazů  
 Dokončování příkazů v editoru základní aktivuje speciální uživatelské rozhraní, které interaktivně vám pomůže snadno a rychle psát kód. Dokončování pomáhá zobrazením příslušné objekty nebo třídy když jsou potřeba, což zabraňuje jste si museli pamatovat konkrétní prvky nebo nutnosti jejich vyhledat v referenčním tématu nápovědy.  
  
 Chcete-li implementovat dokončování příkazů, musí mít jazyka aktivační událost dokončení příkazu, který lze analyzovat. Například [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] používá operátor tečky (.), zatímco [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] používá šipka (->) – operátor. Služba jazyka můžete použít více než jedna aktivační událost zahájíte dokončování. Tyto triggery jsou naprogramovaný tak, že v příkazu filtru.  
  
## <a name="command-filters-and-triggers"></a>Příkaz filtry a aktivační události  
 Příkaz filtry intercept výskyty aktivační události nebo aktivační události. Pokud chcete přidat filtr příkaz k zobrazení, implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a připojte ji k zobrazení pomocí volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metoda. Můžete použít stejný příkaz Filtr (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) pro všechny aspekty službě jazyk, jako je například dokončování příkazů, chyba značky a tipy metoda. Další informace najdete v tématu [brání starší verze jazyka služby příkazy](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Při zadání aktivační událost se v editoru – konkrétně textová vyrovnávací paměť – vaše služba jazyka pak zavolá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metoda. To způsobí, že editor zprovoznit uživatelského rozhraní, takže uživatel může vybrat z kandidáty dokončení příkazu. Tato metoda vyžaduje, abyste implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> a <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> příznaky jako parametry. V rozbalovacím seznamu se zobrazí seznam položek dokončení. Uživatel se stále zadáte, vybrat v rámci pole se seznamem aktualizován, aby odrážel zadali nejvíce odpovídá poslední znaky. Implementuje editoru základní uživatelské rozhraní pro dokončování příkazů, ale služba jazyka musí implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> rozhraní k definování sady položek dokončení kandidáta pro příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy zachytávání služby starší verze jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md)