---
title: Přehled služby starší verze jazyka | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8641a3e009cb5a7b61d8334b6dcb2440d186f4f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131734"
---
# <a name="legacy-language-service-overview"></a>Přehled služby starší verze jazyka
Služba jazyka poskytuje podporu editor, který umožňuje implementovat určité [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkce. Třídy spravované Framework balíčku (MPF) jazyk služby poskytují plnou podporu pro často používané funkce a částečné podporu pro další funkce.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Plně podporované funkce v MPF  
 Třídy sady MPF jazyk služeb podporují následující funkce:  
  
-   zvýraznění syntaxe  
  
-   Sbalování  
  
-   Při psaní komentářů bloky kódu  
  
-   Související závorky  
  
-   Fragmenty kódu  
  
-   Vlastní vlastnosti dokumentu  
  
-   Informace o parametrech IntelliSense  
  
-   Informace o rychlé IntelliSense  
  
-   Člen doplňování IntelliSense  
  
-   Dokončení slova IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Částečně podporovaných funkcích v MPF  
 Sady MPF poskytuje pouze částečný podporu pro následující funkce. To znamená, že musí implementovat metody, které jsou volány MPF.  
  
-   Přeformátování kód. Můžete zadat kód, který implementuje přeformátování.  
  
-   Ověřování zarážky určením platný kód zahrnuje. Můžete zadat kód, který identifikuje kódu rozpětí.  
  
-   Podpora ladicího programu **automobily** okno pro zobrazení proměnné. Můžete zadat kód, který určuje, co se zobrazí v okně.  
  
-   Podpora **navigační panel** rychlé navigace mezi typy a členy. Můžete implementovat a pomocná třída, která naplní seznamy v **navigační panel** pole se seznamem.  
  
## <a name="implementation"></a>Implementace  
 Je třeba provést několik kroky pro implementaci samotnou službu jazyka a jazykové funkce služby, které chcete zajistit podporu pro svůj jazyk. Tyto kroky jsou popsané v následujících tématech:  
  
-   [Implementace služby jazyk starší verze](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrace služby jazyk starší verze](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Osnova ve službě starší verze jazyka](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Kód komentářů ve službě starší verze jazyka](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Přeformátování kódu ve službě starší verze jazyka](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Vlastní vlastnosti dokumentu ve službě starší verze jazyka](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Podpora pro fragmenty kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Podpora navigačního panelu ve službě starší verze jazyka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Dokončování slov ve službě starší verze jazyka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Dokončování členů ve službě starší verze jazyka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Informace o parametrech ve službě jazyk starší verze](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Rychlé informace ve službě starší verze jazyka](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Podpora okna Automatické hodnoty ve službě starší verze jazyka](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Ověřování zarážek ve službě starší verze jazyka](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Viz také  
 [Implementace služby jazyk starší verze](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Rozšíření služeb starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md)