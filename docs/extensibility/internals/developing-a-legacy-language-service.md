---
title: Vývoj služby starší verze jazyka | Microsoft Docs
description: Seznamte se s implementací starší verze jazykové služby jako součásti sady VSPackage nebo pomocí rozšíření Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5f61337b6dbdef158c7fb7ebe42d0af9f79822fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959529"
---
# <a name="develop-a-legacy-language-service"></a>Vývoj služby starší verze jazyka
Tato část obsahuje odkazy na témata, která vám pomůžou vytvořit službu starší verze jazyka.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace jazykové služby najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="in-this-section"></a>V této části
- [Model služby starší verze jazyka](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Poskytuje model minimální jazykové služby pro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] základní editor. Tento model můžete použít jako vodítko pro vytvoření vlastní jazykové služby.

- [Rozhraní služby starší verze jazyka](../../extensibility/internals/legacy-language-service-interfaces.md)

 Popisuje objekty potřebné k implementaci jazykové služby a poskytuje seznam dalších objektů, které lze použít k poskytnutí zvýrazňování syntaxe, dat metody a dalších funkcí.

- [Zachytávání příkazů služby starší verze jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 V této části najdete popis postupu vložení filtru příkazů do služby jazyka pro zachycení příkazů, které by jinak zpracovával zobrazení textu.

- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Poskytuje informace o tom, jak zaregistrovat jazykovou službu pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Podpora jazykové služby pro ladění](../../extensibility/internals/language-service-support-for-debugging.md)

 Popisuje, jak může služba jazyka poskytovat funkce pro podporu ladicího programu.

- [Kontrolní seznam: vytvoření služby starší verze jazyka](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Poskytuje podrobné pokyny pro vytvoření a integraci jazykové služby pro základní editor.

## <a name="related-sections"></a>Související oddíly
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Popisuje, jak implementovat zvýrazňování syntaxe ve službě jazyka.

- [Dokončování příkazů ve službě starší verze jazyka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Popisuje dokončování příkazů, což je proces, při kterém služba jazyka pomáhá uživatelům dokončit klíčové slovo jazyka nebo prvek, který začali psát.

- [Informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Popisuje, jak poskytnout popisy metod pro přetížené funkce a metody.

- [Postupy: poskytování podpory skrytého textu ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Vysvětluje účel skryté oblasti textu a obsahuje pokyny k implementaci oblasti skrytého textu.

- [Postupy: poskytování rozšířené podpory sbalení ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Vysvětluje dvě možnosti, které rozšiřuje podporu osnovy pro váš jazyk nad rámec podpory příkazu *sbalit na definice* .
