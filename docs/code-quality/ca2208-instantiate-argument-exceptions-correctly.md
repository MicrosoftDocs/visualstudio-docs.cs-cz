---
title: 'CA2208: Vytvořte správně instance výjimky argumentu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9f9425ab1ea9eadd3bd06d950118ce83ba5c35f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231646"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Vytvořte správně instance výjimky argumentu

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Mezi možné příčiny patří následující situace:

- Volání je provedeno na výchozí konstruktor (bez parametrů) typu výjimky, který je nebo je odvozen z, <xref:System.ArgumentException>.

- Do parametrizovaného konstruktoru typu výjimky, který je nebo je odvozen z, <xref:System.ArgumentException>, je předán nesprávný řetězcový argument.

## <a name="rule-description"></a>Popis pravidla

Namísto volání výchozího konstruktoru volejte jedno z přetížení konstruktoru, které umožňuje poskytnout smysluplnou zprávu o výjimce. Zpráva o výjimce by měla cílit na vývojáře a jasně vysvětlit chybový stav a způsob, jak tuto výjimku opravit nebo vyhnout.

Signatury jednoho a dvou konstruktorů <xref:System.ArgumentException> řetězce a jeho odvozených typů nejsou konzistentní vzhledem k umístění `message` a `paramName` parametrům. Ujistěte se, že jsou tyto konstruktory volány se správnými řetězcovými argumenty. Signatury jsou následující:

- <xref:System.ArgumentException>(String `message`)
- <xref:System.ArgumentException>(řetězec `message`, řetězec `paramName`)
- <xref:System.ArgumentNullException>(String `paramName`)
- <xref:System.ArgumentNullException>(řetězec `paramName`, řetězec `message`)
- <xref:System.ArgumentOutOfRangeException>(String `paramName`)
- <xref:System.ArgumentOutOfRangeException>(řetězec `paramName`, řetězec `message`)
- <xref:System.DuplicateWaitObjectException>(String `parameterName`)
- <xref:System.DuplicateWaitObjectException>(řetězec `parameterName`, řetězec `message`)

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, zavolejte konstruktor, který přijímá zprávu, název parametru nebo obojí, a ujistěte se, že jsou argumenty správné pro typ <xref:System.ArgumentException> , který je volán.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Upozornění z tohoto pravidla je bezpečné potlačit pouze v případě, že je volán parametrizovaný konstruktor se správnými řetězcovými argumenty.

## <a name="example"></a>Příklad

Následující kód ukazuje konstruktor, který nesprávně vytvoří instanci instance <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Následující kód opravuje předchozí porušení přepnutím argumentů konstruktoru.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Související pravidla

- [CA1507: Použít nameof místo řetězce](ca1507.md)