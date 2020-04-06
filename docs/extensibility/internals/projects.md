---
title: Projekty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706215"
---
# <a name="projects"></a>Projekty
V sadě Visual Studio jsou projekty kontejnery, které vývojáři používají k uspořádání souborů zdrojového kódu a dalších prostředků, které se zobrazí v **Průzkumníku řešení**. Projekty jsou obvykle soubory (například soubor .csproj pro projekt Jazyka C#), které ukládají odkazy na soubory zdrojového kódu a prostředky, jako jsou bitmapové soubory. Projekty umožňují organizovat, vytvářet, ladit a nasazovat zdrojový kód, odkazy na webové služby a databáze a další prostředky. VSPackages můžete rozšířit systém projektu sady Visual Studio ve třech hlavních směrech: *typy projektů*, *podtypy projektu*a vlastní *nástroje*.

## <a name="in-this-section"></a>V tomto oddílu
- [Typy projektů](../../extensibility/internals/project-types.md)

 *Typy projektů* přidat podporu pro nové druhy projektů, jako jsou například programovací jazyky. Například každý jazyk, který podporuje Visual Studio má svůj vlastní typ projektu a ukázka integrace IronPython obsahuje typ projektu pro jazyk IronPython. Chcete-li přizpůsobit způsob vytváření, odlabení, nasazení a zobrazení položek v **Průzkumníku řešení**, je nutné vytvořit typ projektu pro jiné jazyky než C# nebo Visual Basic. Další informace naleznete [v tématu Typy projektů](../../extensibility/internals/project-types.md).

- [Podtypy projektů](../../extensibility/internals/project-subtypes.md)

 *Podtypy projektu* jsou založeny na typech projektů a lze je přizpůsobit způsobu, jakým jsou projekty sestaveny, laděny a nasazovány. Visual Studio používá podtypy projektů s projekty inteligentních zařízení; přizpůsobují nasazení zkopírováním nově vytvořeného programu z vývojového počítače do cílového zařízení. C# a Visual Basic typy projektů lze použít jako základ pro podtypy projektu; Typy projektů jazyka C++ nelze. Vlastní typy projektů lze také použít jako základ pro podtypy projektu. Další informace naleznete [v tématu Podtypy projektu](../../extensibility/internals/project-subtypes.md).

- [Webové projekty](../../extensibility/internals/web-projects.md)

 Vysvětluje webový projekt, který zase vytváří webové aplikace.

- [Nový projekt Generace: Pod kapotou, část první](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) a [nový projekt Generace: Pod kapotou, část druhá](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Vysvětluje, co skutečně dochází při vytváření nového projektu.

- [VSSDK Vzorky](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Obsahuje ukázky v VSSDK, které se zabývají projekty a řešení.

## <a name="related-sections"></a>Související oddíly
- [Práce se sadou Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Vysvětlete různé aspekty rozšiřitelnosti sady Visual Studio.
