---
title: Zachycení příkazy služby starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 669d03043ad36ad1e96084cb4cc8833ab20f0998
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832853"
---
# <a name="intercepting-legacy-language-service-commands"></a>Příkazy zachytávání služby starší verze jazyka
S [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], můžete použít příkazy zachycení služby jazyka, které by jinak zpracovávají zobrazení textu. To je užitečné pro konkrétní jazyk chování, které nespravuje zobrazení textu. Tyto příkazy je možné zachytit přidáním jednoho nebo více filtrů příkaz k zobrazení textu z vaší služby jazyka.  
  
## <a name="getting-and-routing-the-command"></a>Získání a směrování příkazu  
 Příkaz Filtr je <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objekt, který sleduje některé sekvence znaků nebo klíče příkazy. Více než jeden filtr příkazu můžete přidružit jeden textové zobrazení. Každé zobrazení textu udržuje příkaz z řetězu filtrů. Po vytvoření nového filtru příkaz přidáte filtr do řetězce pro zobrazení odpovídající text.  
  
 Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> přidat příkaz filtr do řetězce. Při volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vrátí jiný filtr příkaz, ke kterému lze předat příkazy, které filtr příkaz nezpracovává.  
  
 Máte následující možnosti pro zpracování příkazu:  
  
- Zpracování příkazu a pak předejte příkazu dalšímu příkazu filtru v řetězci.  
  
- Zpracování příkazu a nelze předat příkazu dalšímu filtru příkazu.  
  
- Ke zpracování příkazu, ale příkaz dalšímu filtru příkazu předat.  
  
- Ignorujte příkazu. Nezpracuje v aktuální filtr a nepředávejte dalšímu filtru.  
  
  Informace o příkazech, které by měl zpracovat služby jazyka najdete v tématu [důležité příkazy pro filtry služby jazyka](../../extensibility/internals/important-commands-for-language-service-filters.md).