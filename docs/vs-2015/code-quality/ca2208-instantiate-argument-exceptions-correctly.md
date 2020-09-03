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
ms.openlocfilehash: 6a63ebb7f3946926864c4dd882c281b5dcd7c6c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535834"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Vytvořte správně instance výjimky argumentu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Mezi možné příčiny patří následující situace:

- Bylo provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, která je nebo je odvozena z [System. ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

- Do parametrizovaného konstruktoru typu výjimky, který je nebo je odvozený z [System. ArgumentException.], je předán nesprávný řetězcový argument. (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Popis pravidla
 Namísto volání výchozího konstruktoru volejte jedno z přetížení konstruktoru, které umožňuje poskytnout smysluplnou zprávu o výjimce. Zpráva o výjimce by měla cílit na vývojáře a jasně vysvětlit chybový stav a způsob, jak tuto výjimku opravit nebo vyhnout.

 Signatury jednoho a dvou konstruktorů řetězce <xref:System.ArgumentException> a jeho odvozených typů nejsou konzistentní s ohledem na `message` `paramName` parametry a. Ujistěte se, že jsou tyto konstruktory volány se správnými řetězcovými argumenty. Signatury jsou následující:

 <xref:System.ArgumentException>(String `message` )

 <xref:System.ArgumentException>(řetězec `message` , řetězec `paramName` )

 <xref:System.ArgumentNullException>(String `paramName` )

 <xref:System.ArgumentNullException>(řetězec `paramName` , řetězec `message` )

 <xref:System.ArgumentOutOfRangeException>(String `paramName` )

 <xref:System.ArgumentOutOfRangeException>(řetězec `paramName` , řetězec `message` )

 <xref:System.DuplicateWaitObjectException>(String `parameterName` )

 <xref:System.DuplicateWaitObjectException>(řetězec `parameterName` , řetězec `message` )

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte konstruktor, který přijímá zprávu, název parametru nebo obojí, a ujistěte se, že jsou argumenty správné pro typ, který je <xref:System.ArgumentException> volán.

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
