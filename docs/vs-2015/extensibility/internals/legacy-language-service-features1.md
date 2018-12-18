---
title: Features1 služby starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb66895066d0af1259c3509c40ec9fa4458e3f79
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774053"
---
# <a name="legacy-language-service-features"></a>Funkce služby starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Služba jazyka spravovaného balíčku rozhraní framework (MPF) může podporovat jeden nebo více [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] funkce, jako je zvýrazňování syntaxe, IntelliSense a ověřování zarážku. Jednotlivé funkce je možné implementovat nezávisle na ostatních, ale všechny vyžadují analyzátor a skener kromě zvýrazňování syntaxe, která vyžaduje pouze skeneru.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba pro podporu jazyka pár párování, označované také jako závorky.  
  
 [Kód komentářů ve službě starší verze jazyka](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba pro podporu přidávání poznámek a odstraňuje se komentování z vybraného kódu.  
  
 [Vlastní vlastnosti dokumentu ve službě starší verze jazyka](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba pro podporu vlastnosti dokumentu, které jsou vloženy do zdrojového souboru.  
  
 [Osnova ve službě starší verze jazyka](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba k podpoře sbalování prostřednictvím implementace skryté regiony.  
  
 [Přeformátování kódu ve službě starší verze jazyka](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba k podpoře přeformátování kódu.  
  
 [Podpora pro fragmenty kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba k podpoře fragmenty kódu, které jsou segmenty kódů, které jsou vloženy a lze ho upravovat.  
  
 [Informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Popisuje, co je potřeba k podpoře operace informace o parametru technologie IntelliSense pro zobrazení podpis metody zadávání metody.  
  
 [Rychlé informace ve službě starší verze jazyka](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba k podpoře operace rychlé informace technologie IntelliSense pro zobrazení informací o identifikátor.  
  
 [Dokončování členů ve službě starší verze jazyka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba k podpoře operace člen doplňování technologie IntelliSense pro výběr člena oboru názvů ze seznamu.  
  
 [Dokončování slov ve službě starší verze jazyka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba k podpoře operaci dokončit slovo technologie IntelliSense pro dokončení částečně napsané slova.  
  
 [Podpora okna Automatické hodnoty ve službě starší verze jazyka](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Popisuje, co můžete dělat služba jazyka pro podporu **automatické hodnoty** okno během ladění.  
  
 [Podpora navigačního panelu ve službě starší verze jazyka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Popisuje způsob použití **navigační panel** v horní části zobrazení editoru zajistit rychlou navigaci na libovolný typ nebo člen v souboru je znázorněno v tomto zobrazení...  
  
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Popisuje, co je potřeba pro podporu, zvýrazňování syntaxe kódu ze zdrojového kódu.  
  
 [Ověřování zarážek ve službě starší verze jazyka](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Popisuje, co můžete dělat služba jazyka pro podporu ověřování zarážek mimo ladicí program.  
  
## <a name="related-sections"></a>Související oddíly  
 [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Popisuje analyzátor a skener, které jsou nutné k implementaci všech funkcí jazyka služby, který používá rozhraní spravovaného balíčku.  
  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Popisuje, co je potřeba implementovat služba jazyka pomocí MPF.  
  
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Popisuje kroky, které jsou nutné k registraci služby jazyka založeného na MPF s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Používání atributu IntelliSense](../../ide/using-intellisense.md)  
 Vysvětluje, jak technologie IntelliSense usnadňuje jazyk pro přístup k.  
  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Poskytuje informace o tom, jak používat rozhraní spravovaného balíčku (MPF) k implementaci jazyka plně funkční služba ve spravovaném kódu.

