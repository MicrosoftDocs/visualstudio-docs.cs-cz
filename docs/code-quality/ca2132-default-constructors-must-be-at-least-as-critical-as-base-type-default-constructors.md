---
title: 'CA2132: Výchozí konstruktory musí být alespoň tak kritické, jako výchozí konstruktory základního typu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c5ca98219444515d01baf670489120238cb8dda
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232327"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Výchozí konstruktory musí být alespoň tak kritické, jako výchozí konstruktory základního typu

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

> [!NOTE]
> Toto upozornění je použito pouze pro kód, na kterém je spuštěn CoreCLR (verze modulu CLR, která je specifická pro webové aplikace Silverlight).

## <a name="cause"></a>příčina

Atribut transparentnosti výchozího konstruktoru odvozené třídy není tak důležitý jako průhlednost základní třídy.

## <a name="rule-description"></a>Popis pravidla

Typy a členy, které mají <xref:System.Security.SecurityCriticalAttribute> rozhraní, nelze použít v kódu aplikace Silverlight. Typy a členy kritické z hlediska zabezpečení lze použít pouze prostřednictvím důvěryhodného kódu v knihovně tříd rozhraní .NET Framework aplikace Silverlight. Protože veřejné nebo chráněné konstrukce v odvozené třídě musí mít stejnou nebo větší transparentnost než jejich základní třída, nelze třídu v aplikaci odvodit z třídy označené jako SecurityCritical.

Pro kód platformy CoreCLR, pokud má základní typ veřejný nebo chráněný netransparentní výchozí konstruktor, musí odvozený typ dodržovat pravidla dědičnosti výchozího konstruktoru. Odvozený typ musí mít také výchozí konstruktor a tento konstruktor musí být alespoň v kritickém výchozím konstruktoru základního typu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení, odeberte typ nebo neodvozujte z netransparentního typu zabezpečení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění z tohoto pravidla Porušení tohoto pravidla podle kódu aplikace způsobí, že CoreCLR bude tento typ načítat pomocí <xref:System.TypeLoadException>.

### <a name="code"></a>Kód

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]