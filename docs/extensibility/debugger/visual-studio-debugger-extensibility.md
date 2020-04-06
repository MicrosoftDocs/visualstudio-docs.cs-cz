---
title: Rozšiřitelnost ladicího programu sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712503"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozšiřitelnost ladicího programu visual studio
Visual Studio obsahuje plně interaktivní ladicí program zdrojového kódu, který poskytuje výkonný a snadno použitelný nástroj pro sledování chyb v programu. Ladicí program má úplnou podporu pro Visual Basic, C#, C/C++ a JavaScript. Však s [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], který je k dispozici v [centru pro stahování Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=21835), další programovací jazyky mohou být podporovány v ladicím programu se stejnými bohatými funkcemi.

 Ladicí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] program je společný front-end (to znamená uživatelské rozhraní) ladicí součásti, které jsou zase specifické pro jazyk, který je laděn. Pro nové jazyky vše, co [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je nezbytné pro podporu ladicího programu je vytvořit nezbytné back-endové součásti, jako je například ladicí modul (DE). V tomto bodě [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] je místo, kde přichází.

 Obsahuje [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] úplný odkaz na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] všechny prvky potřebné k vytvoření novéde. Kromě toho existují ukázky a výukové programy, které vám pomohou začít.

 Úplný vzorek systému projektu jazyka s podporou ladění naleznete v [ukázce IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Následující části popisují, jak rozšířit ladicí [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]program pomocí .

## <a name="in-this-section"></a>V tomto oddílu
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Popisuje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] co ladění nabízí a jak nainstalovat sadu SDK.

 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md) Dokumentuje vlastní proces DE, od přípravy programu pro DE k odpojení DE.

 [Napsat vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Vysvětluje, zda je nutné napsat vyhodnocení výrazu.

 [Zvolte strategii implementace ladicího modulu](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Popisuje, jak implementovat de.

 [Odkaz](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumentuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění rozhraní API.

 [Vzorky](../../extensibility/debugger/visual-studio-debugging-samples.md) Obsahuje odkazy na ukázku vyhodnocení exprese modulu runtime společného jazyka a ukázku ladicího modulu.
