---
title: 'CA2132: výchozí konstruktory musí být alespoň tak kritické jako výchozí konstruktory základního typu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ae271b116b372d4ae732d97ff3f9651ff9db426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643303"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Výchozí konstruktory nesmějí být méně kritické než výchozí konstruktory základního typu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

> [!NOTE]
> Toto upozornění je použito pouze pro kód, na kterém je spuštěn CoreCLR (verze modulu CLR, která je specifická pro webové aplikace Silverlight).

## <a name="cause"></a>příčina
 Atribut transparentnosti výchozího konstruktoru odvozené třídy není tak důležitý jako průhlednost základní třídy.

## <a name="rule-description"></a>Popis pravidla
 Typy a členy, které mají <xref:System.Security.SecurityCriticalAttribute>, nelze použít v kódu aplikace Silverlight. Typy a členy kritické z hlediska zabezpečení lze použít pouze prostřednictvím důvěryhodného kódu v knihovně tříd rozhraní .NET Framework aplikace Silverlight. Protože veřejné nebo chráněné konstrukce v odvozené třídě musí mít stejnou nebo větší transparentnost než jejich základní třída, nelze třídu v aplikaci odvodit z třídy označené jako SecurityCritical.

 Pro kód platformy CoreCLR, pokud má základní typ veřejný nebo chráněný netransparentní výchozí konstruktor, musí odvozený typ dodržovat pravidla dědičnosti výchozího konstruktoru. Odvozený typ musí mít také výchozí konstruktor a tento konstruktor musí být alespoň v kritickém výchozím konstruktoru základního typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení, odeberte typ nebo neodvozujte z netransparentního typu zabezpečení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla Porušení tohoto pravidla pomocí kódu aplikace způsobí, že CoreCLR načítá typ s <xref:System.TypeLoadException>.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Komentáře
