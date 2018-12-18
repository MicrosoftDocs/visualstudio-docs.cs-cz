---
title: 'CA2121: Statické konstruktory by měly být privátní'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f20115d694657053e3e687b4e399df463957e9c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923924"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Statické konstruktory by měly být privátní

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Typ má statický konstruktor, který není privátní.

## <a name="rule-description"></a>Popis pravidla

Statický konstruktor, označované také jako konstruktor třídy, slouží k inicializaci typu. Systém volá statický konstruktor před vytvořením první instance typu nebo předtím, než jsou odkazovány jakékoli statické členy. Uživatel nemá žádnou kontrolu nad tím, kdy je volána statický konstruktor. Pokud statický konstruktor není soukromý, může být volán jiným kódem než kódem systému. V závislosti na operacích, které jsou provedeny v konstruktoru, to může způsobit neočekávané chování.

Toto pravidlo je vynuceno kompilátory C# a Visual Basic.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Porušení jsou obvykle způsobeno jedním z následujících akcí:

- Definice statického konstruktoru pro váš typ a nebyly provedeny je privátní.

- Kompilátor programovacího jazyka přidány výchozí statický konstruktor do typu a nebyly provedeny je privátní.

Chcete-li vyřešit první druh porušení, soukromá statický konstruktor. Chcete-li vyřešit druhý typ, přidejte privátní statický konstruktor do typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte těchto porušení. Pokud váš návrh softwaru vyžaduje explicitní volání konstruktoru statický konstruktor, je pravděpodobné, že návrh obsahuje závažné chyby a byste měli zkontrolovat.