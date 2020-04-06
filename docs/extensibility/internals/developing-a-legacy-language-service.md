---
title: Vývoj služby staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708674"
---
# <a name="develop-a-legacy-language-service"></a>Vývoj služby starších jazyků
Tato část odkazuje na témata, která vám pomohou vytvořit službu staršíverze jazyka.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace jazykové služby naleznete v [tématu Editor a rozšíření o jazykovou službu](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="in-this-section"></a>V tomto oddílu
- [Model služby staršího jazyka](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Poskytuje model služby minimální jazyk [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pro editor jádra. Tento model můžete použít jako vodítko pro vytvoření vlastní jazykové služby.

- [Rozhraní starších jazykových služeb](../../extensibility/internals/legacy-language-service-interfaces.md)

 Popisuje objekty potřebné k implementaci služby jazyka a poskytuje seznam dalších objektů, které můžete použít k poskytování zvýraznění syntaxe, dat metod a dalších funkcí.

- [Zachycení starších příkazů služby jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Popisuje, jak vložit filtr příkazů do služby jazyka zachytit příkazy, které by jinak zpracování textového zobrazení.

- [Registrace služby staršího jazyka](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Obsahuje informace o tom, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zaregistrovat jazykovou službu pomocí aplikace .

- [Podpora jazykových služeb pro ladění](../../extensibility/internals/language-service-support-for-debugging.md)

 Popisuje, jak může jazyková služba poskytovat funkce pro podporu ladicího programu.

- [Kontrolní seznam: Vytvoření služby starších jazyků](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Obsahuje podrobné pokyny pro vytvoření a integraci jazykové služby pro základní editor.

## <a name="related-sections"></a>Související oddíly
- [Vybarvení syntaxe ve službě starších jazyků](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Popisuje, jak implementovat zvýraznění syntaxe ve vaší jazykové službě.

- [Dokončení výkazu ve starší jazykové službě](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Popisuje dokončení příkazu, proces, kterým služba jazyka pomáhá uživatelům dokončit klíčové slovo jazyka nebo prvek, který začali psát.

- [Informace o parametrech ve starší jazykové službě](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Popisuje, jak poskytnout tipy metody pro přetížené funkce a metody.

- [Postup: Poskytnutí skryté textové podpory ve službě starších jazyků](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Vysvětluje účel oblasti skrytý text a poskytuje pokyny o tom, jak implementovat oblast skrytý text.

- [Postup: Poskytování rozšířené podpory ve starší jazykové službě](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Vysvětluje dvě možnosti, které rozšiřují nastínit podporu pro váš jazyk mimo podporu *sbalit definice* příkazu.
