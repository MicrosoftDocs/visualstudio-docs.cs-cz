---
title: 'CA1009: Deklarujte správně obslužné rutiny událostí'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e923730213ca31a4429d8547fdaaf980692f9a96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236480"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Deklarujte správně obslužné rutiny událostí

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Delegát, který zpracovává veřejnou nebo chráněnou událost, nemá správný podpis, návratový typ nebo názvy parametrů.

## <a name="rule-description"></a>Popis pravidla
Metody zpracování událostí přebírají dva parametry. První je typu <xref:System.Object?displayProperty=fullName> a má název Sender. Je jím objekt, který vyvolal událost. Druhý parametr je typu <xref:System.EventArgs?displayProperty=fullName> a má název "e". Představuje data přidružená k události. Například pokud je událost vyvolána při každém otevření souboru, data události obvykle obsahují název souboru.

Metody obslužné rutiny událostí by neměly vracet hodnotu. V C# programovacím jazyce je tento typ označen návratovým typem `void`. Obslužná rutina události může vyvolat více metod ve více objektech. Pokud metody mohly vracet hodnotu, pro každou událost by se měly vyskytovat více návratových hodnot a k dispozici je jenom hodnota posledního vyvolané metody.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, opravte podpis, návratový typ nebo názvy parametrů delegáta. Podrobnosti najdete v následujícím příkladu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje delegáta, který je vhodný pro zpracování událostí. Metody, které mohou být vyvolány touto obslužnou rutinou události, jsou v rozporu s signaturou, která je uvedena v pokynech pro návrh. `AlarmEventHandler`je název typu delegáta. `AlarmEventArgs`je odvozen ze základní třídy pro data <xref:System.EventArgs>události a obsahuje data události alarmu.

[!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
[!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
[!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA2109: Kontrola viditelných obslužných rutin událostí](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Viz také:

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [Zpracování a vyvolávání událostí](/dotnet/standard/events/index)