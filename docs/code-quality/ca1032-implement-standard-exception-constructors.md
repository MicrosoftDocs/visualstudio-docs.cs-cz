---
title: 'CA1032: Implementujte standardní konstruktory výjimky'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06fdc566abd9bd16758f224f8a9fe805cddb2c61
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236050"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementujte standardní konstruktory výjimky

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ rozšiřuje <xref:System.Exception?displayProperty=fullName> , ale nedeklaruje všechny požadované konstruktory.

## <a name="rule-description"></a>Popis pravidla

Typy výjimek musí implementovat následující tři konstruktory:

- public NewException()

- Public NewException (řetězec)

- Public NewException (řetězec, výjimka)

Kromě toho, pokud používáte starší analýzu FxCop na rozdíl od [analyzátorů FxCop založených na .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md), neexistence čtvrtého konstruktoru také vygeneruje porušení:

- Protected nebo Private NewException (SerializationInfo, StreamingContext)

Není-li dodána úplná sada konstruktorů, může být obtížné správně ošetřit výjimky. Například konstruktor, který má signaturu `NewException(string, Exception)` , slouží k vytváření výjimek, které jsou způsobeny jinými výjimkami. Bez tohoto konstruktoru nemůžete vytvořit a vyvolat instanci vlastní výjimky, která obsahuje vnitřní (vnořenou) výjimku, která by měla v takové situaci dělat spravovaný kód.

První tři konstruktory výjimky jsou veřejnými úmluvami. Čtvrtý konstruktor je chráněn v nezapečetěných třídách a soukromý v zapečetěných třídách. Další informace najdete v tématu [CA2229: Implementujte konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)serializace.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, přidejte do výjimky chybějící konstruktory a ujistěte se, že mají správné přístupnost.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud je porušení způsobeno použitím jiné úrovně přístupu pro veřejné konstruktory, je bezpečné potlačit upozornění od tohoto pravidla. Kromě toho je v pořádku potlačit upozornění pro `NewException(SerializationInfo, StreamingContext)` konstruktor při vytváření přenositelné knihovny tříd (PCL).

## <a name="example"></a>Příklad

Následující příklad obsahuje typ výjimky, který porušuje toto pravidlo a typ výjimky, který je správně implementován.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Viz také:

[CA2229: Implementovat konstruktory serializace](../code-quality/ca2229-implement-serialization-constructors.md)