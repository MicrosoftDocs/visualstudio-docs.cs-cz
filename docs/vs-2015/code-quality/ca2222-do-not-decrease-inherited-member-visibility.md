---
title: 'CA2222: nezmenšuje zděděnou viditelnost členů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04109e821d3a739b96ad63e1a441089a5d479cd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540774"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Nesnižujte viditelnost zděděného členu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Soukromá metoda v nezapečetěném typu má signaturu, která je shodná s veřejnou metodou deklarovanou v základním typu. Soukromá metoda není finální.

## <a name="rule-description"></a>Popis pravidla
 Modifikátor přístupu byste neměli měnit u zděděných členů. Změna zděděného členu na soukromý nezabrání volajícím v přístupu k implementaci základní třídy dané metody. Pokud je člen vytvořen jako soukromý a typ je nezapečetěný, dědění typů může zavolat poslední veřejnou implementaci metody v hierarchii dědičnosti. Pokud je nutné změnit modifikátor přístupu, buď by měla být metoda označena jako konečná, nebo její typ by měl být zapečetěný, aby se zabránilo přepsání metody.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte přístup na neprivátní. Případně, pokud je váš programovací jazyk podporován, můžete nastavit metodu jako konečnou.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je v rozporu s tímto pravidlem.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]
