---
title: Starší verze jazyka služby Features1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c931147d20454a920e20cec61e1f6000a9b043d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131729"
---
# <a name="legacy-language-service-features"></a>Funkce služby starší verze jazyka
Spravované balíček služby jazyk framework (MPF) může podporovat jeden nebo více [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkce, jako je zvýraznění syntaxe, IntelliSense a ověřování zarážek. Jednotlivé funkce se dají implementovat navzájem nezávislé, ale všechny vyžadují analyzátor a skener s výjimkou zvýraznění syntaxe, které vyžaduje pouze skener.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytný pro podporu jazyka pár párování, také známé jako závorky.  
  
 [Kód komentářů ve službě starší verze jazyka](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytný pro podporu přidávání poznámek a uncommenting vybrané kódu.  
  
 [Vlastní vlastnosti dokumentu ve službě starší verze jazyka](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytný pro podporu vlastností dokumentu, které jsou vloženy do zdrojového souboru.  
  
 [Osnova ve službě starší verze jazyka](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytný pro podporu osnovy prostřednictvím implementace skrytá oblastí.  
  
 [Přeformátování kódu ve službě starší verze jazyka](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytný pro podporu přeformátování kódu.  
  
 [Podpora pro fragmenty kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytný pro podporu fragmenty kódu, které jsou segmenty kódu, které jsou vloženy a lze ho upravovat.  
  
 [Informace o parametrech ve službě jazyk starší verze](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Popisuje, co je nezbytný pro podporu operaci parametr informace technologie IntelliSense pro zobrazení podpis metody, jako je zadán metodu.  
  
 [Rychlé informace ve službě starší verze jazyka](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytný pro podporu operaci rychlé informace technologie IntelliSense pro zobrazení informací o identifikátor.  
  
 [Dokončování členů ve službě starší verze jazyka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytná pro podporu technologie IntelliSense člen dokončení operace pro výběr člena v oboru názvů ze seznamu.  
  
 [Dokončování slov ve službě starší verze jazyka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytný pro podporu operaci dokončení Word IntelliSense pro dokončení částečně typové slova.  
  
 [Podpora okna Automatické hodnoty ve službě starší verze jazyka](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Popisuje, co můžete dělat služba jazyka pro podporu **automobily** okno při ladění.  
  
 [Podpora navigačního panelu ve službě starší verze jazyka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Popisuje postup použití **navigační panel** v horní části editoru zobrazení umožníte rychlé navigace k žádné typ nebo člen v souboru uvedené v tomto zobrazení...  
  
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Popisuje, co je nezbytný pro podporu zvýraznění syntaxe zdrojového kódu.  
  
 [Ověřování zarážek ve službě starší verze jazyka](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Popisuje, co můžete dělat služba jazyka pro podporu ověřování zarážky mimo ladicí program.  
  
## <a name="related-sections"></a>Související oddíly  
 [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Popisuje analyzátor a skener, které jsou nutné k implementaci všechny funkce jazyka službu, která používá rozhraní spravované balíčku.  
  
 [Implementace služby jazyk starší verze](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Popisuje, co je potřeba implementovat služba jazyka pomocí MPF.  
  
 [Registrace služby jazyk starší verze](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Popisuje kroky, které jsou potřeba k registraci služby jazyk na základě sady MPF s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Používání atributu IntelliSense](../../ide/using-intellisense.md)  
 Vysvětluje, jak IntelliSense usnadňuje jazyk odkazy pro přístup.  
  
 [Implementace služby jazyk starší verze](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Poskytuje informace o tom, jak použít rozhraní spravované balíčku (MPF) k implementaci služby plnohodnotný jazyk ve spravovaném kódu.