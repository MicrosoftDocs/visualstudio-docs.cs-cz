---
title: 'CA1032: Implementujte standardní konstruktory výjimky'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6cd6922cae5e2d182a279e2d1637a19f8572468
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454749"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementujte standardní konstruktory výjimky

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina

Typ rozšiřuje <xref:System.Exception?displayProperty=fullName> , ale není deklarovat všechny požadované konstruktory.

## <a name="rule-description"></a>Popis pravidla

Typy výjimek musí implementovat následující tři konstruktory:

- veřejné NewException()

- veřejné NewException(string)

- veřejné NewException (string, výjimka)

Kromě toho, pokud používáte starší verzi analýza statické kódu FxCop jako nikoli [na základě Roslyn FxCop analyzátorů](../code-quality/roslyn-analyzers-overview.md), absence čtvrtý konstruktor vytvoří také narušení:

- chráněný nebo privátní NewException (položku SerializationInfo, StreamingContext)

Není-li dodána úplná sada konstruktorů, může být obtížné správně ošetřit výjimky. Například konstruktor, který má podpis `NewException(string, Exception)` se používá k vytvoření výjimky, které jsou způsobeny další výjimky. Bez tohoto konstruktoru nelze vytvořit a throw instanci vaše vlastní výjimka, která obsahuje vnitřní výjimky (vnořené), která je, jaké spravovaného kódu má provést v této situaci.

První tři výjimka konstruktory jsou veřejné podle konvence. Čtvrtý konstruktor je chráněný v nezapečetěných třídy a privátní v zapečetěné třídy. Další informace najdete v tématu [CA2229: implementovat Serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Opravit porušení toto pravidlo, přidejte chybějící konstruktory výjimku a ujistěte se, jestli mají nastavená správná usnadnění.

## <a name="when-to-suppress-warnings"></a>Při potlačení upozornění

Je bezpečné při porušení je způsobena pomocí úrovní různý přístup pro veřejné konstruktory potlačit upozornění na toto pravidlo. Kromě toho je v pořádku pro toto upozornění potlačit `NewException(SerializationInfo, StreamingContext)` konstruktor Pokud vytváříte přenosných třída knihovny PCL ().

## <a name="example"></a>Příklad

Následující příklad obsahuje typ výjimky, která porušuje toto pravidlo a typ výjimky, která je implementovaná správně.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Viz také

[CA2229: Implementovat serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)