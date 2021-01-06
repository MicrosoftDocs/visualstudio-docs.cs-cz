---
title: Projekty | Microsoft Docs
description: Přečtěte si o způsobech, kterými můžou sady VSPackage roztáhnout systém projektů Visual studia, včetně typů projektu, podtypů projektů a vlastních nástrojů.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ffc2dc28ed3d45194ba7738da58fa36dd022c79f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878050"
---
# <a name="projects"></a>Projekty
V aplikaci Visual Studio jsou projekty kontejnery, které vývojáři používají k uspořádání souborů zdrojového kódu a dalších prostředků, které se zobrazí v **Průzkumník řešení**. Projekty jsou typicky soubory (například soubor. csproj pro projekt C#), které ukládají odkazy na soubory zdrojového kódu a prostředky, jako jsou rastrové soubory. Projekty umožňují organizovat, sestavovat, ladit a nasazovat zdrojový kód, odkazy na webové služby a databáze a další prostředky. Sady VSPackage mohou roztáhnout systém projektu sady Visual Studio třemi hlavními způsoby: *typy projektů*, *podtypy projektů* a *vlastní nástroje*.

## <a name="in-this-section"></a>V tomto oddílu
- [Typy projektů](../../extensibility/internals/project-types.md)

 *Typy projektů* přidávají podporu pro nové druhy projektů, například programovací jazyky. Například každý jazyk, který podporuje Visual Studio, má svůj vlastní typ projektu a Ironpythonu Integration Sample zahrnuje typ projektu pro jazyk Ironpythonu. Musíte vytvořit typ projektu pro jiné jazyky než C# nebo Visual Basic, abyste mohli přizpůsobit způsob, jakým jsou položky sestaveny, laděny, nasazeny a zobrazovány v **Průzkumník řešení**. Další informace naleznete v tématu [typy projektů](../../extensibility/internals/project-types.md).

- [Podtypy projektů](../../extensibility/internals/project-subtypes.md)

 *Podtypy projektů* jsou založeny na typech projektů a lze je použít k přizpůsobení způsobu, jakým jsou projekty sestaveny, laděny a nasazeny. Visual Studio používá podtypy projektu s projekty inteligentních zařízení; přizpůsobují nasazení kopírováním nově sestaveného programu z vývojového počítače do cílového zařízení. Typy projektů C# a Visual Basic lze použít jako základ pro podtypy projektu; Typy projektů C++ nemůžou. Vlastní typy projektů lze také použít jako základ pro podtypy projektu. Další informace naleznete v tématu [podtypy projektu](../../extensibility/internals/project-subtypes.md).

- [Webové projekty](../../extensibility/internals/web-projects.md)

 Vysvětluje webový projekt, který zase vytvoří webové aplikace.

- [Nová generace projektů: pod digestoří, první částí](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) a [novou výrobou projektů: pod digestoří, druhá část](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Vysvětluje, co se skutečně děje při vytváření nového projektu.

- [Ukázky VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Obsahuje ukázky v VSSDK, které se týkají projektů a řešení.

## <a name="related-sections"></a>Související oddíly
- [Práce se sadou Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Vysvětlete různé aspekty rozšiřitelnosti sady Visual Studio.
