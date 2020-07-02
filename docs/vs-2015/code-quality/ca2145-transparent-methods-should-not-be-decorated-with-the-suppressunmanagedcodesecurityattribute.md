---
title: 'CA2145: transparentní metody by neměly být dekorované s použitím SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d5eb16130aef42abcf9fddf533d0253864a75114
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546403"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Transparentní metody by neměly být doplněny o SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Transparentní metoda, metoda, která je označena <xref:System.Security.SecuritySafeCriticalAttribute> metodou, nebo typem, který obsahuje metodu, je označena <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributem.

## <a name="rule-description"></a>Popis pravidla
 Metody dekorované s <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributem mají implicitní LinkDemand umístěný na jakékoli metodě, která ji volá. Tento LinkDemand vyžaduje, aby byl volající kód kritický z hlediska zabezpečení. Označením metody, která používá SuppressUnmanagedCodeSecurity s <xref:System.Security.SecurityCriticalAttribute> atributem, je tento požadavek jasnější pro volající metody.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, označte metodu nebo typ s <xref:System.Security.SecurityCriticalAttribute> atributem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Komentáře
