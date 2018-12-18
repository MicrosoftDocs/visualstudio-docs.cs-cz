---
title: 'CA1721: Názvy vlastností by neměly odpovídat metodám Get'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 26f6e23a340ec018f766477f0bdce089a43ca3e4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549674"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Názvy vlastností by neměly odpovídat metodám Get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategorie|Microsoft.Naming|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Název soukromého nebo chráněného členu začíná na "Get" a shoduje s názvem veřejné nebo chráněné vlastnosti. Typ, který obsahuje metodu s názvem 'Getcolor –' a vlastnost s názvem 'Color' Příklad poruší toto pravidlo.

## <a name="rule-description"></a>Popis pravidla
 Metody GET a vlastnosti by měly mít názvy, které zřetelně rozliší jejich funkce.

 Zásady vytváření názvů poskytují obecný vzhled knihovnám využívajících common language runtime. Taková konzistence snižuje čas, který vyžaduje další nové knihovny softwaru a zvyšuje důvěru zákazníků, že byla vyvinuta knihovny někdo, kdo má odborných znalostí v vývoj spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Změňte název tak, aby neodpovídá názvu metody, která je s předponou "Get".

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

> [!NOTE]
> Toto upozornění může vyloučit, je-li metodu Get implementací rozhraní IExtenderProvider.

## <a name="example"></a>Příklad
 Následující příklad obsahuje metody a vlastnosti, která toto pravidlo porušují.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Související pravidla
 [CA1024: Použijte vlastnosti, kde je to vhodné](../code-quality/ca1024-use-properties-where-appropriate.md)