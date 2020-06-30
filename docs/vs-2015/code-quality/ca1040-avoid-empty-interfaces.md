---
title: 'CA1040: Vyhněte se prázdným rozhraním | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ef6dc666cbc3c26d58358c9b59264f93a7bf184
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548249"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Vyhněte se prázdným rozhraním
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Rozhraní nedeklaruje žádné členy ani neimplementuje dvě nebo více jiných rozhraní.

## <a name="rule-description"></a>Popis pravidla
 Rozhraní definují členy ujednávající jejich chování nebo užití. Funkčnost popsaná rozhraním může být osvojena libovolným typem bez ohledu na to, kde se typ vyskytuje v hierarchii dědičnosti. Typ implementuje rozhraní tím, že poskytuje implementace jeho členů. Prázdné rozhraní nedefinuje žádné členy. Proto nedefinuje kontrakt, který lze implementovat.

 Pokud váš návrh obsahuje prázdná rozhraní, u kterých se očekává implementace typů, pravděpodobně použijete rozhraní jako značku nebo způsob, jak identifikovat skupinu typů. Pokud k této identifikaci dojde v době běhu, správný způsob, jak to provést, je použít vlastní atribut. Pro identifikaci cílových typů použijte přítomnost nebo nepřítomnost atributu nebo vlastnosti atributu. Pokud k identifikaci musí dojít v době kompilace, je přijatelné použít prázdné rozhraní.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Odeberte rozhraní nebo přidejte do něj členy. Pokud je prázdné rozhraní použito k označení sady typů, nahraďte rozhraní vlastním atributem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud se rozhraní používá k identifikaci sady typů v době kompilace.

## <a name="example"></a>Příklad
 Následující příklad ukazuje prázdné rozhraní.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
