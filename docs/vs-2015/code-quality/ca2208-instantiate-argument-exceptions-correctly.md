---
title: 'CA2208: Vytvořte instance výjimky argumentu správně | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 55789b7d5b4b1e462b715649b7583299b9f02e6b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825600"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Vytvořte správně instance výjimky argumentu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Možné příčiny následujících situacích:

-   Je provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, které jsou, nebo je odvozena z [System.ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

-   Je předán nesprávný řetězcový argument do konstruktoru s parametry typu výjimky, které jsou, nebo je odvozena z [System.ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Popis pravidla
 Namísto volání výchozího konstruktoru, volání jednoho z přetížení konstruktoru, které umožňuje lépe vystihuje zpráva o výjimce poskytované. Zpráva o výjimce musí cílit na vývojáře a jasně vysvětlit chybovou podmínku a tom, jak opravit nebo vyhnout výjimku.

 Podpisy jeden a dva řetězce konstruktory <xref:System.ArgumentException> a jeho odvozených typů nejsou konzistentní s ohledem na `message` a `paramName` parametry. Zajistěte, aby že tyto konstruktory jsou volány pomocí správné řetězcové argumenty. Podpisy jsou následující:

 <xref:System.ArgumentException>(řetězce `message`)

 <xref:System.ArgumentException>(řetězec `message`, řetězec `paramName`)

 <xref:System.ArgumentNullException>(řetězce `paramName`)

 <xref:System.ArgumentNullException>(řetězec `paramName`, řetězec `message`)

 <xref:System.ArgumentOutOfRangeException>(řetězce `paramName`)

 <xref:System.ArgumentOutOfRangeException>(řetězec `paramName`, řetězec `message`)

 <xref:System.DuplicateWaitObjectException>(řetězce `parameterName`)

 <xref:System.DuplicateWaitObjectException>(řetězec `parameterName`, řetězec `message`)

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, volat konstruktor, který přijímá zprávy, název parametru nebo obojí a ujistěte se, že jsou správné typu pro argumenty <xref:System.ArgumentException> volána.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla pouze v případě konstruktorem je volána s argumenty správný řetězec.

## <a name="example"></a>Příklad
 Následující příklad ukazuje konstruktor, který se nesprávně vytvoří instanci typu ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Příklad
 V následujícím příkladu řeší výše porušení přepnutím argumenty konstruktoru.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]



