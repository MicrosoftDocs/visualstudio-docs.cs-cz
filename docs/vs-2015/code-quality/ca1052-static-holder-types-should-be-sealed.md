---
title: 'CA1052: statické typy držitelů by měly být zapečetěné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14231cc4dcde5aed5cabc2d8a6172a002c0ba6bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539747"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Statické typy vlastníků by měly být zapečetěné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejný nebo chráněný typ obsahuje pouze statické členy a není deklarován s modifikátorem [sealed](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)).

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo předpokládá, že typ, který obsahuje pouze statické členy, není navržen tak, aby byl zděděn, protože typ neposkytuje žádné funkce, které mohou být přepsány v odvozeném typu. Typ, který není určen k dědění, by měl být označen `sealed` modifikátorem, aby bylo možné jeho použití jako základní typ zakázat.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, označte typ jako `sealed` . Pokud cílíte na [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 nebo starší, lepším přístupem je označit typ jako `static` . Tímto způsobem se vyhnete nutnosti deklarovat privátní konstruktor, aby se zabránilo vytváření třídy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla pouze v případě, že je typ navržen tak, aby byl zděděn. Absence `sealed` modifikátoru naznačuje, že typ je užitečný jako základní typ.

## <a name="example-of-a-violation"></a>Příklad porušení

### <a name="description"></a>Popis
 Následující příklad ukazuje typ, který je v rozporu s pravidlem.

### <a name="code"></a>Kód
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Oprava pomocí modifikátoru static

### <a name="description"></a>Popis
 Následující příklad ukazuje, jak opravit porušení tohoto pravidla označením typu s `static` modifikátorem.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1053: Statické typy vlastníků by neměly mít konstruktory](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
