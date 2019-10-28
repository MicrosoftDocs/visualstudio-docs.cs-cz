---
title: Rozšiřitelnost ladicího programu sady Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58bfec6fa09f6450afb8170d60acad39edacd590
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982457"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozšiřitelnost ladicího programu sady Visual Studio
Visual Studio obsahuje plně interaktivní ladicí program zdrojového kódu, který poskytuje výkonný a snadno použitelný nástroj pro sledování chyb v programu. Ladicí program dokončí podporu Visual Basic, C#, C/C++a JavaScriptu. Avšak s [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], který je k dispozici na webu [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=21835), mohou být v ladicím programu podporovány jiné programovací jazyky se stejnými funkcemi.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladicí program je běžné front-end (tj. uživatelské rozhraní) k ladicím komponentám, které jsou v tuto chvíli specifické pro laděný jazyk. Pro nové jazyky, které jsou nezbytné pro podporu ladicího programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], je vytvoření nezbytných back-endové komponenty, jako je například ladicí stroj (DE). Tady je místo, kde [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] přichází.

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] obsahuje kompletní odkaz na všechny [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prvky, které jsou nutné k vytvoření nového elementu DE. K dispozici jsou také ukázky a kurzy, které vám pomůžou začít.

 Kompletní vzorek jazykového projektového systému s podporou ladění najdete v [ukázce ironpythonu](https://www.microsoft.com/download/details.aspx?id=55984).

 Následující části popisují, jak tento ladicí program rozšíříte pomocí [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>V tomto oddílu
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Popisuje, co [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nabídky ladění a jak nainstalovat sadu SDK.

 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md) Dokumentuje vlastní DE Process, od přípravy programu až po odpojení od DE.

 [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Vysvětluje, zda je nutné napsat vyhodnocovací filtr výrazů.

 [Zvolit strategii implementace ladicího modulu](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Popisuje, jak implementovat správce DE.

 [Referenční informace](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumentuje rozhraní API pro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění.

 [Ukázky](../../extensibility/debugger/visual-studio-debugging-samples.md) Obsahuje odkazy na ukázku vyhodnocení výrazu společného jazykového modulu runtime a ukázku ladicího stroje.
