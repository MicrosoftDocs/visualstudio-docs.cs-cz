---
title: Vývoj služby starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d92c07742dcc4433aa96071d655f58d938a1f80
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497827"
---
# <a name="develop-a-legacy-language-service"></a>Vývoj služby starší verze jazyka
Tento oddíl obsahuje odkazy na témata, které umožňují vytvoření služby starší verze jazyka.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace o nový způsob implementace služby jazyka najdete v tématu [jazyk a Editor rozšíření služeb](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Model služby starší verze jazyka](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Poskytuje služby minimální jazyka pro model [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] základní editor. Tento model jako vodítko můžete použít k vytváření vlastních služeb jazyka.  
  
 [Rozhraní služby starší verze jazyka](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Tento článek popisuje objekty nezbytné k implementaci služby jazyka a poskytuje seznam další objekty, které můžete použít k zajištění zvýrazňování syntaxe, metoda dat a další funkce.  
  
 [Zachytit příkazy služby starší verze jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Popisuje, jak vložit příkaz filtru do služby jazyka pro příkazy zachycení, které by jinak zpracovat zobrazení textu.  
  
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Poskytuje informace o tom, jak zaregistrovat vaše služba jazyka pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Podpora služby jazyka pro ladění](../../extensibility/internals/language-service-support-for-debugging.md)  
 Popisuje, jak služba jazyka může poskytovat funkce pro podporu ladicího programu.  
  
 [Kontrolní seznam: Vytvoření služby starší verze jazyka](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Poskytuje podrobné pokyny pro vytváření a integrace language service pro základní editor.  
  
## <a name="related-sections"></a>Související oddíly  
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Popisuje, jak implementovat, zvýrazňování syntaxe ve vaší službě jazyka.  
  
 [Dokončování příkazů ve službě starší verze jazyka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Tento článek popisuje dokončování příkazů, proces, podle kterého služba jazyka pomáhá uživatelům dokončit – klíčové slovo jazyka nebo element, kterou zahájil psát.  
  
 [Informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Popisuje, jak získat tipy metodu přetížených funkcí a metod.  
  
 [Postupy: Zadejte skrytého textu podporují ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Vysvětluje účel oblasti skrytého textu a poskytuje pokyny o tom, jak implementovat oblasti skrytého textu.  
  
 [Postupy: Rozšířená podpora osnovy ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Vysvětluje dvě možnosti, které rozšiřují podpora osnovy pro váš jazyk nad rámec podpora *sbalit do definic* příkazu.