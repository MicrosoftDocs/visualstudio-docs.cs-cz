---
title: 'CA1032: Implementujte standardní konstruktory výjimky | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b471387db3ce52944ffad3841dc7e946c4d44873
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661878"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementujte standardní konstruktory výjimky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Typ rozšiřuje <xref:System.Exception?displayProperty=fullName> a nedeklaruje všechny požadované konstruktory.

## <a name="rule-description"></a>Popis pravidla
 Typy výjimek musí implementovat následující konstruktory:

- veřejné NewException ()

- Public NewException (řetězec)

- Public NewException (řetězec, výjimka)

- Protected nebo Private NewException (SerializationInfo, StreamingContext)

  Není-li dodána úplná sada konstruktorů, může být obtížné správně ošetřit výjimky. Například konstruktor, který má signaturu `NewException(string, Exception)`, slouží k vytváření výjimek, které jsou způsobeny jinými výjimkami. Bez tohoto konstruktoru nelze vytvořit a vyvolat instanci vlastní výjimky, která obsahuje vnitřní (vnořenou) výjimku, což znamená, jaký spravovaný kód by v takové situaci měl dělat. První tři konstruktory výjimky jsou veřejnými úmluvami. Čtvrtý konstruktor je chráněn v nezapečetěných třídách a soukromý v zapečetěných třídách. Další informace najdete v tématu [CA2229: implementace serializacch konstruktorů.](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte do výjimky chybějící konstruktory a ujistěte se, že mají správné přístupnost.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud je porušení způsobeno použitím jiné úrovně přístupu pro veřejné konstruktory, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad obsahuje typ výjimky, který porušuje toto pravidlo a typ výjimky, který je správně implementován.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
