---
title: 'CA2142: transparentní kód by neměl být chráněn pomocí LinkDemands | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa6bd9dcacc5fb863199c740a71c824f14739052
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546429"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Transparentní kód by neměl být chráněn pomocí LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Transparentní metoda vyžaduje <xref:System.Security.Permissions.SecurityAction> nebo jiné požadavky na zabezpečení.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je vyvoláno na transparentních metodách, které vyžadují pro přístup k nim pravidla LinkDemand. Kód transparentní z hlediska zabezpečení by neměl být odpovědný za ověření zabezpečení operace, a proto by neměl požadovat oprávnění. Vzhledem k tomu, že transparentní metody by měly být z důvodu zabezpečení neutrální, neměli byste provádět žádná bezpečnostní rozhodnutí. Navíc bezpečný kritický kód, který provádí rozhodnutí o zabezpečení, by neměl být závislý na transparentním kódu, aby byl takovým rozhodnutím dříve proveden.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte požadavek propojení na transparentní metodě nebo označte metodu <xref:System.Security.SecuritySafeCriticalAttribute> atributem, pokud provádí kontroly zabezpečení, jako třeba požadavky na zabezpečení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 V následujícím příkladu je pravidlo aktivováno pro metodu, protože metoda je transparentní a je označena pomocí LinkDemand <xref:System.Security.PermissionSet> , který obsahuje <xref:System.Security.Permissions.SecurityAction> .

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 Nepotlačujte upozornění na toto pravidlo.
