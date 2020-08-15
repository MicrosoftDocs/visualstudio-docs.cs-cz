---
title: Features1 služby starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f2a4010529d3d9727ceb76d6a34f2cbc41b959
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238476"
---
# <a name="legacy-language-service-features-1"></a>Funkce služby starší verze jazyka 1
Služba jazyka Managed Package Framework (MPF) může podporovat jednu nebo více funkcí, jako je například [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zvýrazňování syntaxe, technologie IntelliSense a ověřování zarážek. Jednotlivé funkce je možné implementovat nezávisle na ostatních, ale všechny vyžadují analyzátor a skener s výjimkou zvýrazňování syntaxe, který vyžaduje jenom skener.

## <a name="in-this-section"></a>V tomto oddílu
- [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Popisuje, co je potřeba k podpoře párování dvojic jazyků, označovaného také jako párování složených závorek.

- [Kód komentářů ve službě starší verze jazyka](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Popisuje, co je potřeba k podpoře přidávání komentářů a odkomentování vybraného kódu.

- [Vlastní vlastnosti dokumentu ve službě starší verze jazyka](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Popisuje, co je potřeba k podpoře vlastností dokumentu, které jsou vložené ve zdrojovém souboru.

- [Osnova ve službě starší verze jazyka](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Popisuje, co je potřeba k podpoře sbalení při implementaci skrytých oblastí.

- [Přeformátování kódu ve službě starší verze jazyka](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Popisuje, co je potřeba pro podporu přeformátování kódu.

- [Podpora pro fragmenty kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Popisuje, co je potřeba k podpoře fragmentů kódu, které jsou segmenty vloženého kódu a které lze upravovat.

- [Informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Popisuje, co je potřeba k podpoře operace informací o parametrech technologie IntelliSense pro zobrazení signatury metody při zadání metody.

- [Rychlé informace ve službě starší verze jazyka](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Popisuje, co je potřeba k podpoře rychlé operace technologie IntelliSense pro zobrazení informací o identifikátoru.

- [Dokončování členů ve službě starší verze jazyka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Popisuje, co je potřeba k podpoře operace dokončení členů technologie IntelliSense pro výběr člena oboru názvů ze seznamu.

- [Dokončování slov ve službě starší verze jazyka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Popisuje, co je potřeba k podpoře operace se slovem dokončení aplikace IntelliSense při dokončování částečně typovaného slova.

- [Podpora okna Automatické hodnoty ve službě starší verze jazyka](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Popisuje, co služba jazyka může při ladění podporovat okno **Automatické** hodnoty.

- [Podpora navigačního panelu ve službě starší verze jazyka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Popisuje, jak použít **navigační panel** v horní části zobrazení editoru k zajištění rychlé navigace libovolného typu nebo člena v souboru zobrazeném v tomto zobrazení..

- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Popisuje, co je potřeba pro podporu zvýrazňování syntaxe zdrojového kódu.

- [Ověřování zarážek ve službě starší verze jazyka](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Popisuje, co může služba jazyka provést, aby podporovala ověřování zarážek mimo ladicí program.

## <a name="related-sections"></a>Související oddíly
- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Popisuje analyzátor a skener, které jsou vyžadovány k implementaci všech funkcí jazykové služby, které používají rozhraní Managed Package Framework.

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Popisuje, co je potřeba k implementaci jazykové služby pomocí formátu MPF.

- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Popisuje kroky, které jsou požadovány k registraci služby jazyka založeného na formátu MPF pomocí nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Pomocí technologie IntelliSense](../../ide/using-intellisense.md)

 Vysvětluje, jak technologie IntelliSense usnadňuje přístup k jazykovým odkazům.

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Poskytuje informace o tom, jak použít sadu Managed Package Framework (MPF) k implementaci plně funkční jazykové služby ve spravovaném kódu.
