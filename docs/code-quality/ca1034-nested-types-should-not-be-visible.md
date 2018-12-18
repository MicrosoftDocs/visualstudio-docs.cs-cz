---
title: 'CA1034: Vnořené typy by neměly být viditelné'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 14c0837d482341e1ba60191c8b6bb3f5bd8e6dd4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550944"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Vnořené typy by neměly být viditelné

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Externě viditelný typ obsahuje externě viditelný typ deklarace. Chráněné typy a výčty vnořené jsou z tohoto pravidla vyjmuty.

## <a name="rule-description"></a>Popis pravidla
 Vnořený typ je typ deklarovaný v rámci oboru jiného typu. Vnořené typy jsou užitečné pro zapouzdření soukromých podrobností implementace v nadřazeného typu. Jsou-li vnořené typy používány za tímto účelem, neměly by být externě viditelné.

 Nepoužívejte externě viditelné typy vnořených logického seskupení nebo vyhnete kolize názvů; Místo toho použijte obory názvů.

 Vnořené typy zahrnují informace o usnadnění přístupu člena, který není srozumitelný jasně některé programátory.

 Chráněné typy lze použít v podtřídy třídy a vnořené typy ve scénářích přizpůsobení zálohy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud už nebudete vnořený typ externě viditelný, změňte přístupnost typu. V opačném případě odeberte vnořený typ ze svého nadřazeného objektu. Pokud účel vnořování je do kategorií vnořeného typu, použijte místo toho vytvářet hierarchii oboru názvů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který porušuje pravidla.

 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]