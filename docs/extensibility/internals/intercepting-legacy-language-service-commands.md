---
title: Zachycení příkazů služby starší verze jazyka | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707441"
---
# <a name="intercepting-legacy-language-service-commands"></a>Příkazy zachytávání služby starší verze jazyka
Pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] můžete mít službu jazyka k zachycení příkazů, které by jinak zpracovávala zobrazení textu. To je užitečné pro chování specifické pro konkrétní jazyk, které nespravuje textové zobrazení. Tyto příkazy můžete zachytit přidáním jednoho nebo více filtrů příkazů do textového zobrazení z vaší jazykové služby.

## <a name="getting-and-routing-the-command"></a>Získání a směrování příkazu
 Filtr příkazů je <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objekt, který monitoruje určité sekvence znaků nebo klíčové příkazy. K jednomu textovému zobrazení můžete přidružit více než jeden filtr příkazů. Každé zobrazení textu udržuje řetěz filtrů příkazů. Po vytvoření nového filtru příkazů přidejte filtr do řetězce pro příslušné textové zobrazení.

 Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodu pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Přidání filtru příkazů do řetězce. Při volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vrátí jiný filtr příkazu, do kterého můžete předat příkazy, které filtr příkazů nezpracovává.

 Pro zpracování příkazů máte následující možnosti:

- Zpracujte příkaz a potom předejte příkaz do dalšího filtru příkazů v řetězci.

- Zpracujte příkaz a nepředávejte příkaz do dalšího filtru příkazů.

- Nezpracujte příkaz, ale předejte příkaz na další filtr příkazů.

- Ignorujte příkaz. Nezpracujte ho v aktuálním filtru a nepředávejte ho k dalšímu filtru.

  Informace o příkazech, které by měla vaše služba jazyka zpracovat, najdete v tématu [Důležité příkazy pro filtry jazykové služby](../../extensibility/internals/important-commands-for-language-service-filters.md).
