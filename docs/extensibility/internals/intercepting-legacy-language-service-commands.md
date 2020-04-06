---
title: Zachycení příkazů služby starších jazyků | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707441"
---
# <a name="intercepting-legacy-language-service-commands"></a>Příkazy zachytávání služby starší verze jazyka
Pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]rozhraní můžete mít příkazy pro zachycení služby jazyka, které by jinak zpracovat textové zobrazení. To je užitečné pro chování specifické pro jazyk, které nespravuje zobrazení textu. Tyto příkazy můžete zachytit přidáním jednoho nebo více filtrů příkazů do textového zobrazení ze služby jazyka.

## <a name="getting-and-routing-the-command"></a>Získání a směrování příkazu
 Filtr příkazů je <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objekt, který monitoruje určité sekvence znaků nebo příkazy kláves. K jednomu textovému zobrazení můžete přidružit více než jeden filtr příkazů. Každé textové zobrazení udržuje řetězec filtrů příkazů. Po vytvoření nového filtru příkazů přidáte filtr do řetězce pro příslušné textové zobrazení.

 Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> přidat příkazový filtr do řetězce. Při volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vrátí jiný filtr příkazů, ke kterému můžete předat příkazy, které filtr příkazu nezpracovává.

 Pro zpracování příkazů máte následující možnosti:

- Zpracovat příkaz a poté jej předat dalšímu příkazu filtru v řetězci.

- Zpracovat příkaz a nepředávat příkaz na další příkaz filtr.

- Nezpracovat příkaz, ale předat příkaz na další příkaz filtr.

- Ignorujte příkaz. Nemanipulujte s ním v aktuálním filtru a nepředávají jej dalšímu filtru.

  Informace o tom, které příkazy by měla služba jazyka zpracovávat, naleznete [v tématu Důležité příkazy pro filtry jazykové služby](../../extensibility/internals/important-commands-for-language-service-filters.md).
