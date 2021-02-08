---
title: Zachycení příkazů služby starší verze jazyka | Microsoft Docs
description: Naučte se používat filtry příkazů v aplikaci Visual Studio k zachycení příkazů služby starší verze jazyka a k přidání chování specifického pro jazyk.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6a759f0cef7329d14d7d1472d38f662c0206448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839791"
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
