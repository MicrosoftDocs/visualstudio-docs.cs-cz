---
title: Funkce služby staršíjazykové služby1 | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707389"
---
# <a name="legacy-language-service-features"></a>Funkce služby starší verze jazyka
Služba jazyka MPF (Managed Package Framework) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] může podporovat jednu nebo více funkcí, jako je například zvýraznění syntaxe, technologie IntelliSense a ověřování zarážky. Každá funkce může být implementována nezávisle na ostatních, ale všechny vyžadují analyzátor a skener s výjimkou zvýraznění syntaxe, které vyžaduje pouze skener.

## <a name="in-this-section"></a>V tomto oddílu
- [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu párování jazyků, označované také jako porovnávání složených závorek.

- [Kód komentářů ve službě starší verze jazyka](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu komentování a odkomentování vybraného kódu.

- [Vlastní vlastnosti dokumentu ve službě starší verze jazyka](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu vlastností dokumentu, které jsou vloženy do zdrojového souboru.

- [Osnova ve službě starší verze jazyka](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu osnovy prostřednictvím provádění skrytých oblastí.

- [Přeformátování kódu ve službě starší verze jazyka](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu přeformátování kódu.

- [Podpora pro fragmenty kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu fragmenty kódu, které jsou segmenty kódu, které jsou vloženy a lze upravovat.

- [Informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Popisuje, co je nutné pro podporu operace IntelliSense Parameter Info pro zobrazení podpisu metody při psaní metody.

- [Rychlé informace ve službě starší verze jazyka](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu operace IntelliSense Quick Info pro zobrazení informací o identifikátoru.

- [Dokončování členů ve službě starší verze jazyka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu operace dokončení členů Technologie IntelliSense pro výběr člena oboru názvů ze seznamu.

- [Dokončování slov ve službě starší verze jazyka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu operace IntelliSense Complete Word pro dokončení částečně zadaných slov.

- [Podpora okna Automatické hodnoty ve službě starší verze jazyka](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Popisuje, co může jazyková služba provést pro podporu okna **Autos** při ladění.

- [Podpora navigačního panelu ve službě starší verze jazyka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Popisuje, jak pomocí **navigačního panelu** v horní části zobrazení editoru poskytnout rychlou navigaci na libovolný typ nebo člen v souboru zobrazeném v tomto zobrazení..

- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Popisuje, co je nutné pro podporu zvýraznění syntaxe zdrojového kódu.

- [Ověřování zarážek ve službě starší verze jazyka](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Popisuje, co může jazyková služba udělat pro podporu ověřování zarážek mimo ladicí program.

## <a name="related-sections"></a>Související oddíly
- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Popisuje analyzátor a skener, které jsou nutné k implementaci všech funkcí jazykové služby, která používá rozhraní spravovaného balíčku.

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Popisuje, co je nutné implementovat službu jazyka pomocí MPF.

- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Popisuje kroky, které jsou nutné k registraci jazykové [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]služby založené na MPF s .

- [Používání atributu IntelliSense](../../ide/using-intellisense.md)

 Vysvětluje, jak technologie IntelliSense usnadňuje přístup k jazykovým odkazům.

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Obsahuje informace o tom, jak používat rozhraní spravovaného balíčku (MPF) k implementaci plnohodnotné jazykové služby ve spravovaném kódu.
