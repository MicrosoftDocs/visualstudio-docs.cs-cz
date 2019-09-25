---
title: 'CA2145: Transparentní metody by neměly být doplněny o SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cca385c346a7daa8aaddb377f999506ffb1abaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232042"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Transparentní metody by neměly být doplněny o SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Transparentní metoda, metoda, která je označena <xref:System.Security.SecuritySafeCriticalAttribute> metodou, nebo typem, který obsahuje metodu, je označena <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributem.

## <a name="rule-description"></a>Popis pravidla

Metody dekorované s <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributem mají implicitní LinkDemand umístěný na jakékoli metodě, která ji volá. Tento LinkDemand vyžaduje, aby byl volající kód kritický z hlediska zabezpečení. Označením metody, která používá SuppressUnmanagedCodeSecurity s <xref:System.Security.SecurityCriticalAttribute> atributem, je tento požadavek jasnější pro volající metody.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, označte metodu nebo typ s <xref:System.Security.SecurityCriticalAttribute> atributem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

### <a name="code"></a>Kód

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]