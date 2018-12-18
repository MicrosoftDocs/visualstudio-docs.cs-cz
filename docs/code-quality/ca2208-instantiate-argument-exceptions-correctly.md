---
title: 'CA2208: Vytvořte správně instance výjimky argumentu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f7a10d126d5432a80b146fe2086c01064d83006e
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547432"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Vytvořte správně instance výjimky argumentu

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Možné příčiny následujících situacích:

- Je provedeno volání výchozího konstruktoru (bez parametrů) typu výjimky, které jsou, nebo je odvozena z <xref:System.ArgumentException>.

- Je předán nesprávný řetězcový argument do konstruktoru s parametry typu výjimky, které jsou, nebo je odvozena z <xref:System.ArgumentException>.

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

## <a name="example-1"></a>Příklad 1
 Následující příklad ukazuje konstruktor, který se nesprávně vytvoří instanci typu ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example-2"></a>Příklad 2
 V následujícím příkladu řeší výše porušení přepnutím argumenty konstruktoru.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]