---
title: Rozšiřitelnost služby staršíverze jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707410"
---
# <a name="legacy-language-service-extensibility"></a>Rozšíření služeb starší verze jazyka
Jazyková služba poskytuje jazykově specifickou podporu pro úpravy zdrojového kódu v rozhraní IDE.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace jazykové služby naleznete v [tématu Editor and Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

 Tato část popisuje strukturu a implementaci služby staršíverze jazyka.

## <a name="in-this-section"></a>V tomto oddílu
- [Migrace služby starší verze jazyka](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Vysvětluje, jak aktualizovat jazykovou službu z visual studia 2008 na nejnovější verzi.

- [Základy služby starší verze jazyka](../../extensibility/internals/legacy-language-service-essentials.md)

 Obsahuje důležité informace o vývoji jazykových služeb pro integraci programovacího jazyka do sady Visual Studio.

- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)

 Obsahuje odkazy na témata, která vám mohou pomoci vytvořit jazykovou službu.

- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Obsahuje informace o podpoře zvýraznění syntaxe v jazykové službě.

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Obsahuje informace o tom, jak používat rozhraní spravovaného balíčku (MPF) k implementaci plnohodnotné jazykové služby ve spravovaném kódu.

- [Podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Popisuje knihovny a nástroje, které umožňují procházet stromová zobrazení symbolů v ide.

## <a name="related-sections"></a>Související oddíly
- [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)

 Obsahuje přehled editorů sady Visual Studio.

- [Podpora služby jazyka pro ladění](../../extensibility/internals/language-service-support-for-debugging.md)

 Obsahuje informace a odkaz na sadu SDK ladění sady Visual Studio, která obsahuje informace potřebné k vytvoření a přizpůsobení součástí ladicího programu používaných k ladění programů.
