---
title: 'CA1823: Vyhněte se nepoužitým soukromým polím | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 01f2ef59ceb6d10cc33276fdd3e5388f39175f8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545298"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Vyhněte se nepoužitým privátním polím
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Toto pravidlo je hlášeno, když existuje soukromé pole v kódu, ale není používáno žádnou cestou kódu.

## <a name="rule-description"></a>Popis pravidla
 Byla zjištěna soukromá pole, která v rámci sestavení zjevně nejsou přístupná.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte pole nebo přidejte kód, který ho používá.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění.

## <a name="related-rules"></a>Související pravidla
 [CA1812: Vyhněte se nevytvořeným instancím interních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Zkontrolujte nepoužité parametry](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Odeberte nepoužívané lokální hodnoty](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Vyhněte se nevolanému privátnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)
