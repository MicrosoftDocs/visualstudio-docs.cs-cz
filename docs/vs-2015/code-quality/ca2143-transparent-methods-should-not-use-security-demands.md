---
title: 'CA2143: transparentní metody by neměly používat požadavky zabezpečení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca8f049da83b99da7d36ebf74e756dd95f738d64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546468"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Transparentní metody by neměly používat požadavky zabezpečení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Typ nebo metoda Tranparent je deklarativně označena <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` poptávkou nebo metoda volá <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> metodu.

## <a name="rule-description"></a>Popis pravidla
 Kód transparentní z hlediska zabezpečení by neměl být odpovědný za ověření zabezpečení operace, a proto by neměl požadovat oprávnění. Kód transparentní z hlediska zabezpečení by měl k učinění rozhodnutí o zabezpečení používat úplné požadavky a bezpečně kritický kód by neměl spoléhat na to, že transparentní kód tyto úplné požadavky provede. Jakýkoli kód, který provádí kontroly zabezpečení, jako třeba požadavky na zabezpečení, by měl být místo toho kritický.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Obecně platí, že chcete-li opravit porušení tohoto pravidla, označte metodu <xref:System.Security.SecuritySafeCriticalAttribute> atributem. Můžete také odebrat poptávku.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Soubory pravidla v následujícím kódu, protože transparentní metoda vytvoří deklarativní požadavek zabezpečení.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>Viz také
 [CA2142: Transparentní kód by neměl být chráněn pomocí LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
