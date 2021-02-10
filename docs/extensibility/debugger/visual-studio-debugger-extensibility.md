---
title: Rozšiřitelnost ladicího programu sady Visual Studio | Microsoft Docs
description: Tento článek popisuje rozšiřitelnost ladicího programu sady Visual Studio a obsahuje odkazy na články o ladění sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ebc884d36260ec3a057f75951cdbc4e7cc811079
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965444"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozšiřitelnost ladicího programu sady Visual Studio
Visual Studio obsahuje plně interaktivní ladicí program zdrojového kódu, který poskytuje výkonný a snadno použitelný nástroj pro sledování chyb v programu. Ladicí program má úplnou podporu pro Visual Basic, C#, C/C++ a JavaScript. Pomocí nástroje [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , který je k dispozici na webu [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=21835), ale mohou být v ladicím programu podporovány jiné programovací jazyky se stejnými funkcemi.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Ladicí program je běžný front-end (tj. uživatelské rozhraní) na ladicí komponenty, které jsou následně specifické pro jazyk, který je laděn. Pro nové jazyky, které jsou nezbytné pro podporu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladicího programu, je vytvoření nezbytných back-endové komponenty, jako je například ladicí stroj (de). Tady je místo, kde se nachází [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Obsahuje kompletní odkaz na všechny prvky, které jsou [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nutné k vytvoření nového elementu de. K dispozici jsou také ukázky a kurzy, které vám pomůžou začít.

 Kompletní vzorek jazykového projektového systému s podporou ladění najdete v [ukázce ironpythonu](https://www.microsoft.com/download/details.aspx?id=55984).

 Následující části popisují, jak tento ladicí program rozšíříte pomocí [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>V této části
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Popisuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , jaké nabídky ladění a jak nainstalovat sadu SDK.

 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md) Dokumentuje vlastní DE Process, od přípravy programu až po odpojení od DE.

 [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Vysvětluje, zda je nutné napsat vyhodnocovací filtr výrazů.

 [Zvolit strategii implementace ladicího modulu](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Popisuje, jak implementovat správce DE.

 [Referenční informace](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumentuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní API pro ladění.

 [Ukázky](../../extensibility/debugger/visual-studio-debugging-samples.md) Obsahuje odkazy na ukázku vyhodnocení výrazu společného jazykového modulu runtime a ukázku ladicího stroje.
