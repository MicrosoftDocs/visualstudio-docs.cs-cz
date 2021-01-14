---
title: Přehled služby starší verze jazyka | Microsoft Docs
description: Seznamte se se staršími jazykovými službami v aplikaci Visual Studio a funkcemi podporovanými třídami služeb jazyka Managed Package Framework (MPF).
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c1ec349e38acbdb0271ecfb0c081b4f1aadadcd9
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204940"
---
# <a name="legacy-language-service-overview"></a>Přehled služby starší verze jazyka
Jazyková služba poskytuje podporu editoru, která umožňuje implementovat určité [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkce. Třídy služby jazyka Managed Package Framework (MPF) poskytují plnou podporu pro často používané funkce a částečnou podporu pro další funkce.

## <a name="fully-supported-features-in-the-mpf"></a>Plně podporované funkce v poli MPF
 Třídy služby jazyka MPF podporují následující funkce:

- Zvýrazňování syntaxe

- Sbalování

- Komentování bloků kódu

- Spárování složených závorek

- Fragmenty kódu

- Vlastní vlastnosti dokumentu

- Informace o parametrech IntelliSense

- Rychlé informace technologie IntelliSense

- Dokončení členů IntelliSense

- Dokončování slov IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Částečně podporované funkce v poli MPF
 MPF poskytuje pouze částečnou podporu pro následující funkce. To znamená, že je nutné implementovat metody, které jsou volány pomocí MPF.

- Přeformátování kódu. Zadejte kód, který implementuje přeformátování.

- Ověřování zarážek určením platných rozsahů kódu. Zadejte kód, který identifikuje rozsah kódu.

- Podpora okna **Automatické** hodnoty ladicího programu pro zobrazení proměnných Zadejte kód, který určuje, co se má zobrazit v okně.

- Podpora **navigačního panelu** pro rychlou navigaci mezi typy a členy. Implementujete a vrátíte pomocnou třídu, která vyplní seznamy do polí se seznamem **navigačního panelu** .

## <a name="implementation"></a>Implementace
 Je nutné provést několik kroků k implementaci samotné jazykové služby a funkcí jazykové služby, které chcete pro svůj jazyk podporovat. Tyto kroky jsou popsány v následujících tématech:

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
