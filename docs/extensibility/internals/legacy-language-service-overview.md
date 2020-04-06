---
title: Přehled služby starší verze jazyků | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707360"
---
# <a name="legacy-language-service-overview"></a>Přehled služby starší verze jazyka
Jazyková služba poskytuje podporu editoru, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] která umožňuje implementovat určité funkce. Třídy jazykových služeb Rozhraní spravovaného balíčku (MPF) poskytují plnou podporu pro často používané funkce a částečnou podporu pro další funkce.

## <a name="fully-supported-features-in-the-mpf"></a>Plně podporované funkce v MPF
 Třídy jazykových služeb MPF podporují následující funkce:

- Zvýraznění syntaxe

- Sbalování

- Komentování bloků kódu

- Shoda složených závorek

- Fragmenty kódu

- Vlastní vlastnosti dokumentu

- Informace o parametru IntelliSense

- Rychlé informace technologie IntelliSense

- Dokončení člena technologie IntelliSense

- Dokončení slova IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Částečně podporované funkce v MPF
 MPF poskytuje pouze částečnou podporu pro následující funkce. To znamená, že je nutné implementovat metody, které jsou volány MPF.

- Přeformátování kódu. Zadáte kód, který implementuje přeformátování.

- Ověření zarážek určením platných rozsahů kódu. Zadáte kód, který identifikuje rozsahy kódu.

- Podpora **okna** automatického ladicího programu pro zobrazení proměnných. Zadáte kód, který určuje, co se má zobrazit v okně.

- Podpora **navigačního panelu** pro rychlou navigaci mezi typy a členy. Implementovat a vrátit pomocné třídy, která naplní seznamy v polích se seznamem **navigační panel.**

## <a name="implementation"></a>Implementace
 Je nutné provést několik kroků k implementaci samotné jazykové služby a funkcí služby jazyka, které chcete podporovat pro váš jazyk. Tyto kroky jsou popsány v následujících tématech:

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Osnova ve službě starší verze jazyka](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Kód komentářů ve službě starší verze jazyka](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Přeformátování kódu ve službě starší verze jazyka](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Vlastní vlastnosti dokumentu ve službě starší verze jazyka](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Podpora pro fragmenty kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Podpora navigačního panelu ve službě starší verze jazyka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Dokončování slov ve službě starší verze jazyka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Dokončování členů ve službě starší verze jazyka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Rychlé informace ve službě starší verze jazyka](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Podpora okna Automatické hodnoty ve službě starší verze jazyka](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Ověřování zarážek ve službě starší verze jazyka](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Viz také
- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Rozšíření služeb starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md)
