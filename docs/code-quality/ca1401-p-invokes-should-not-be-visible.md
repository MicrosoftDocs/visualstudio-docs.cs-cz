---
title: 'CA1401: Volání nespravovaných kódů by neměla být viditelná'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d4a0a1c001407d947988497c422fdb8e88dd7c83
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234900"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: Volání nespravovaných kódů by neměla být viditelná

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Veřejná nebo chráněná metoda ve veřejném typu má <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atribut (také implementováno `Declare` klíčovým slovem [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]v).

## <a name="rule-description"></a>Popis pravidla
Metody označené <xref:System.Runtime.InteropServices.DllImportAttribute> atributem (nebo metodami, které jsou definovány `Declare` pomocí klíčového slova v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) používají pro přístup k nespravovanému kódu služby vyvolání platformy. Tyto metody by neměly být vystaveny. Udržováním těchto metod jako soukromých nebo interních se ujistěte, že vaše knihovna nemůže být použita k porušení zabezpečení tím, že umožňuje volajícím přístup k nespravovaným rozhraním API, která by nemohly volat jinak.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte úroveň přístupu metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad deklaruje metodu, která porušuje toto pravidlo.

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]