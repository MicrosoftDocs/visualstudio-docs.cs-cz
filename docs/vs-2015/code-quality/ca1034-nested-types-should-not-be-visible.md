---
title: 'CA1034: Vnořené typy by neměly být viditelné | Dokumentace Microsoftu'
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
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c246f80907ae72673df3471f0dff8e6afa4e4b2f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814908"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Vnořené typy by neměly být viditelné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]



