---
title: Vývoj služby starší verze jazyka | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 36ff8335bfaf99b5826d217a48910bfd581321e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805201"
---
# <a name="developing-a-legacy-language-service"></a>Vývoj služby starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato část obsahuje odkazy na témata, která vám pomůžou vytvořit službu starší verze jazyka.  
  
 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace jazykové služby najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Model služby starší verze jazyka](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Poskytuje model minimální jazykové služby pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] základní editor. Tento model můžete použít jako vodítko pro vytvoření vlastní jazykové služby.  
  
 [Rozhraní služby starší verze jazyka](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Popisuje objekty potřebné k implementaci jazykové služby a poskytuje seznam dalších objektů, které lze použít k poskytnutí zvýrazňování syntaxe, dat metody a dalších funkcí.  
  
 [Příkazy zachytávání služby starší verze jazyka](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 V této části najdete popis postupu vložení filtru příkazů do služby jazyka pro zachycení příkazů, které by jinak zpracovával zobrazení textu.  
  
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Poskytuje informace o tom, jak zaregistrovat jazykovou službu pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Podpora služby jazyka pro ladění](../../extensibility/internals/language-service-support-for-debugging.md)  
 Popisuje, jak může služba jazyka poskytovat funkce pro podporu ladicího programu.  
  
 [Kontrolní seznam: Vytvoření služby starší verze jazyka](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Poskytuje podrobné pokyny pro vytvoření a integraci jazykové služby pro základní editor.  
  
## <a name="related-sections"></a>Související oddíly  
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Popisuje, jak implementovat zvýrazňování syntaxe ve službě jazyka.  
  
 [Dokončování příkazů ve službě starší verze jazyka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Popisuje dokončování příkazů, což je proces, při kterém služba jazyka pomáhá uživatelům dokončit klíčové slovo jazyka nebo prvek, který začali psát.  
  
 [Informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Popisuje, jak poskytnout popisy metod pro přetížené funkce a metody.  
  
 [Postupy: Poskytování podpory skrytého textu ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Vysvětluje účel skryté oblasti textu a obsahuje pokyny k implementaci oblasti skrytého textu.  
  
 [Postupy: Rozšířená podpora osnovy ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Vysvětluje dvě možnosti, které rozšiřuje podporu osnovy pro váš jazyk nad rámec podpory příkazu *sbalit na definice* .
