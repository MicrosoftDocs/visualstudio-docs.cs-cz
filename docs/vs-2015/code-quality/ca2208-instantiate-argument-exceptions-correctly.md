---
title: 'CA2208: správně se vytvoří instance výjimek argumentu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5b5e1525d1ee706f9cd46a58c022763d2ed234bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662688"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Vytvořte správně instance výjimky argumentu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Mezi možné příčiny patří následující situace:

- Bylo provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, která je nebo je odvozena z [System. ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

- Do parametrizovaného konstruktoru typu výjimky, který je nebo je odvozený z [System. ArgumentException.], je předán nesprávný řetězcový argument. (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Popis pravidla
 Namísto volání výchozího konstruktoru volejte jedno z přetížení konstruktoru, které umožňuje poskytnout smysluplnou zprávu o výjimce. Zpráva o výjimce by měla cílit na vývojáře a jasně vysvětlit chybový stav a způsob, jak tuto výjimku opravit nebo vyhnout.

 Signatury jednoho a dvou konstruktorů řetězce <xref:System.ArgumentException> a jeho odvozených typů nejsou konzistentní s ohledem na parametry `message` a `paramName`. Ujistěte se, že jsou tyto konstruktory volány se správnými řetězcovými argumenty. Signatury jsou následující:

 <xref:System.ArgumentException> (řetězec `message`)

 <xref:System.ArgumentException> (řetězec `message`, řetězec `paramName`)

 <xref:System.ArgumentNullException> (řetězec `paramName`)

 <xref:System.ArgumentNullException> (řetězec `paramName`, řetězec `message`)

 <xref:System.ArgumentOutOfRangeException> (řetězec `paramName`)

 <xref:System.ArgumentOutOfRangeException> (řetězec `paramName`, řetězec `message`)

 <xref:System.DuplicateWaitObjectException> (řetězec `parameterName`)

 <xref:System.DuplicateWaitObjectException> (řetězec `parameterName`, řetězec `message`)

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte konstruktor, který přijímá zprávu, název parametru nebo obojí, a ujistěte se, že jsou argumenty správné pro typ <xref:System.ArgumentException> volání.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Upozornění z tohoto pravidla je bezpečné potlačit pouze v případě, že je volán parametrizovaný konstruktor se správnými řetězcovými argumenty.

## <a name="example"></a>Příklad
 Následující příklad ukazuje konstruktor, který nesprávně vytvoří instanci instance typu ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Příklad
 Následující příklad opravuje výše uvedené porušení přepnutím argumentů konstruktoru.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
