---
title: 'CA2214: Nevolejte přepsatelné metody v konstruktorech | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ad467e880b3281a75db2627108af0e0b2f90ea99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534456"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Nevolejte přepisovatelné metody v konstruktorech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Konstruktor nezapečetěného typu volá virtuální metodu definovanou ve své třídě.

## <a name="rule-description"></a>Popis pravidla
 Při volání virtuální metody není skutečný typ, který spouští metodu, vybrán do doby běhu. Když konstruktor volá virtuální metodu, je možné, že konstruktor instance, která volá metodu, není proveden.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, Nevolejte virtuální metody typu v rámci konstruktorů typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Konstruktor by měl být přepracován, aby se vyloučilo volání virtuální metody.

## <a name="example"></a>Příklad
 Následující příklad ukazuje účinek porušení tohoto pravidla. Testovací aplikace vytvoří instanci `DerivedType` , která způsobí spuštění konstruktoru základní třídy ( `BadlyConstructedType` ). `BadlyConstructedType`konstruktor nesprávně volá virtuální metodu `DoSomething` . Jak výstup ukazuje, je `DerivedType.DoSomething()` spuštěn a provede se, než se `DerivedType` spustí konstruktor.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Tento příklad vytvoří následující výstup.

 **Volání základního konstruktoru ctor.** 
 **Odvozená DoSomething se nazývá inicializovaná? Žádné** 
 **volání odvozeného konstruktoru ctor.**
