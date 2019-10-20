---
title: 'CA2133: Delegáti musí být vázáni k metodám s konzistentní transparentností | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 487047b7dd3096e65a6e287d79d91d3029f3dc5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608984"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Delegáti musejí být připojeni k metodám s konzistentní transparentností
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

> [!NOTE]
> Toto upozornění je použito pouze pro kód, na kterém je spuštěn CoreCLR (verze modulu CLR, která je specifická pro webové aplikace Silverlight).

## <a name="cause"></a>příčina
 Toto upozornění se aktivuje u metody, která váže delegáta, který je označený pomocí <xref:System.Security.SecurityCriticalAttribute>, k metodě, která je průhledná nebo která je označena <xref:System.Security.SecuritySafeCriticalAttribute>. Upozornění je také vyvoláno na metodě, která vytvoří vazbu transparentního delegáta nebo bezpečně kritického delegáta na kritickou metodu.

## <a name="rule-description"></a>Popis pravidla
 Typy delegátů a metody, které jsou vázány na, musí mít konzistentní transparentnost. Transparentní a bezpečně kritické delegáti mohou být vázáni pouze na jiné transparentní nebo bezpečné metody kritické. Podobně, kritické delegáti mohou být vázáni pouze na kritické metody. Tato pravidla vazby zajišťují, že jediný kód, který může vyvolat metodu prostřednictvím delegáta, by mohl také vyvolat stejnou metodu přímo. Například pravidla vazby zabraňují transparentnímu kódu ve volání kritického kódu přímo prostřednictvím transparentního delegáta.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto upozornění, změňte průhlednost delegáta nebo metody, kterou sváže, aby transparentnost těchto dvou je ekvivalentní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
