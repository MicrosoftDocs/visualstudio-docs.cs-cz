---
title: 'CA1053: Statický vlastník typů by neměl mít konstruktory'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 43d8af3d592d687064c50fc046c6a7f61d64335f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854792"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Statický vlastník typů by neměl mít konstruktory

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo vnořený veřejný typ deklaruje pouze statické členy a má veřejný nebo chráněný výchozí konstruktor.

## <a name="rule-description"></a>Popis pravidla
 Konstruktor není nutný, protože volání statických členů nevyžaduje instanci typu. Navíc vzhledem k tomu, že typ nemá žádné nestatické členy, vytvoření instance neposkytuje přístup k libovolnému členy tohoto typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte výchozí konstruktor nebo ji učiňte soukromou.

> [!NOTE]
>  Některé kompilátory automaticky vytvořit výchozí veřejný konstruktor, pokud typ nedefinuje žádné konstruktory. Pokud tomu tak s typem, přidejte privátní výchozí konstruktor, chcete-li odstranit porušení zásady.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Přítomnost konstruktoru naznačuje, že typ není statický typ.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který porušuje tato pravidla. Všimněte si, že neexistuje žádný výchozí konstruktor ve zdrojovém kódu. Když tento kód je zkompilován do sestavení, kompilátor jazyka C# vloží výchozí konstruktor, který bude toto pravidlo porušují. Chcete-li opravit, deklarujte soukromý konstruktor.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]