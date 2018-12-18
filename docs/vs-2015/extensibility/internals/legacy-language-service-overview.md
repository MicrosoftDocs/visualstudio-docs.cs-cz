---
title: Přehled služby starší verze jazyka | Dokumentace Microsoftu
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
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 10c464532872e8fc337fda1bf0cd0bf0be374618
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758941"
---
# <a name="legacy-language-service-overview"></a>Přehled služby starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Služba jazyka podporuje editor, který umožňuje implementovat určité [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] funkce. Třídy služeb Managed Package Framework (MPF) jazyka poskytují úplnou podporu pro často používané funkce a částečně se podporuje další funkce.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Plně podporované funkce v MPF  
 Třídy MPF language service podporují následující funkce:  
  
-   Zvýrazňování syntaxe  
  
-   Sbalování  
  
-   Při psaní komentářů bloky kódu  
  
-   Párování závorek  
  
-   Fragmenty kódu  
  
-   Vlastní vlastnosti dokumentu  
  
-   Informace o parametrech technologie IntelliSense  
  
-   Informace o parametru technologie IntelliSense  
  
-   Doplňování technologie IntelliSense člena  
  
-   Doplňování technologie IntelliSense aplikace word  
  
## <a name="partially-supported-features-in-the-mpf"></a>Částečně podporované funkce v MPF  
 MPF poskytuje jenom částečnou podporu pro následující funkce. To znamená, že je nutné implementovat metody, které jsou volány MPF.  
  
-   Přeformátování kódu. Zadáte kód, který implementuje přeformátování.  
  
-   Ověřování zarážek určením platný kód zahrnuje. Zadáte kód, který identifikuje kódu rozpětí.  
  
-   Podpora ladicího programu **automatické hodnoty** okno pro zobrazení proměnné. Zadáte kód, který určuje, co se má zobrazit v okně.  
  
-   Podpora **navigační panel** pro rychlou navigaci mezi typy a členy. Implementace a vracet pomocnou třídu, která naplní seznamy v **navigační panel** polích se seznamem.  
  
## <a name="implementation"></a>Implementace  
 Musíte dokončit několik kroků při implementaci samotnou službu jazyka a tato služba nabízí jazyka, které chcete zajistit podporu pro jazyk. Tyto kroky jsou popsány v následujících tématech:  
  
-   [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
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
  
-   [Informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Rychlé informace ve službě starší verze jazyka](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Podpora okna Automatické hodnoty ve službě starší verze jazyka](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Ověřování zarážek ve službě starší verze jazyka](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Viz také  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Rozšíření služeb starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md)

