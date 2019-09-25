---
title: 'CA2149: Transparentní metody nesmí provádět volání nativního kódu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8e75b12b820b3ff3ac5a26f83148a49ca87c12ad
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231957"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Transparentní metody nesmí provádět volání nativního kódu

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Metoda volá nativní funkci prostřednictvím zástupné procedury metody, jako je například volání nespravovaného kódu.

## <a name="rule-description"></a>Popis pravidla
Toto pravidlo je vyvoláno na jakékoli transparentní metodě, která volá přímo do nativního kódu, například prostřednictvím volání nespravovaného kódu. Porušení tohoto pravidla vedou k <xref:System.MethodAccessException> tomu v modelu transparentnosti úrovně 2 a plné poptávce pro <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> model transparentnosti úrovně 1.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, označte metodu, která volá nativní kód s <xref:System.Security.SecurityCriticalAttribute> atributem or. <xref:System.Security.SecuritySafeCriticalAttribute>

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
[!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]