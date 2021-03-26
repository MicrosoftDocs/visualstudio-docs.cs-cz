---
title: Rozšiřitelnost služby starší verze jazyka | Microsoft Docs
description: Přečtěte si o struktuře, implementaci a rozšiřitelnosti starších jazykových služeb v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f22d6997d932884e5aeb8d794b7884b40a8d5dab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074493"
---
# <a name="legacy-language-service-extensibility"></a>Rozšíření služeb starší verze jazyka
Jazyková služba poskytuje podporu pro konkrétní jazyk pro úpravu zdrojového kódu v integrovaném vývojovém prostředí.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace jazykové služby najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).

 Tato část popisuje strukturu a implementaci služby starší verze jazyka.

## <a name="in-this-section"></a>V tomto oddílu
- [Migrace služby starší verze jazyka](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Vysvětluje, jak aktualizovat službu jazyka ze sady Visual Studio 2008 na nejnovější verzi.

- [Základy služby starší verze jazyka](../../extensibility/internals/legacy-language-service-essentials.md)

 Poskytuje důležité informace o tom, jak vyvíjet jazykové služby pro integraci programovacího jazyka do sady Visual Studio.

- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)

 Obsahuje odkazy na témata, která vám pomůžou vytvořit službu jazyka.

- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Poskytuje informace o podpoře zvýrazňování syntaxe ve službě jazyka.

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Poskytuje informace o tom, jak použít sadu Managed Package Framework (MPF) k implementaci plně funkční jazykové služby ve spravovaném kódu.

- [Podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Popisuje knihovny a nástroje, které umožňují procházet stromová zobrazení symbolů v integrovaném vývojovém prostředí (IDE).

## <a name="related-sections"></a>Související oddíly
- [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)

 Poskytuje přehled editorů sady Visual Studio.

- [Podpora služby jazyka pro ladění](../../extensibility/internals/language-service-support-for-debugging.md)

 Obsahuje informace o a odkaz na sadu SDK pro ladění sady Visual Studio, která obsahuje informace potřebné k vytvoření a přizpůsobení komponent ladicího programu používaných pro ladění programů.
