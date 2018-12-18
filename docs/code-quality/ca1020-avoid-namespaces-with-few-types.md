---
title: 'CA1020: Vyvarujte se oborům názvu s malým množstvím typů'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc7a691cb5c5626ea096046e277ec3d1655db0b6
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546217"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Vyvarujte se oborům názvu s malým množstvím typů

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Obor názvů než globální obor názvů obsahuje méně než pět typů.

## <a name="rule-description"></a>Popis pravidla

Ujistěte se, že všechny obory názvů mají logické uspořádání a, existuje platný důvod do typů do řídce zaplněných oborů názvů. Obory názvů by měl obsahovat typy, které se používají společně ve většině scénářů. Když své aplikace se vzájemně vylučují, typy musí nacházet v samostatných oborů názvů. Například <xref:System.Web.UI> obor názvů obsahuje typy, které se používají ve webových aplikacích a <xref:System.Windows.Forms> obor názvů obsahuje typy, které se používají v [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]– aplikace založené na. I když oba obory názvů mají typy, které řídí aspekty uživatelského rozhraní, nejsou tyto typy určený k použití ve stejné aplikaci. Proto se nacházejí v samostatných oborů názvů. Pozor, obor názvů organizace může být také užitečné vzhledem k tomu, že jeho hodnota se zvyšuje zjistitelnost funkce. Prozkoumáním hierarchii obor názvů spotřebitelé knihovny by měli být schopen najít typy, které implementují funkce.

> [!NOTE]
> Typy návrhu a oprávnění by neměl sloučeny do jiných oborech názvů pro dosažení souladu s toto pravidlo. Tyto typy patří do své vlastní obory názvů pod hlavním obor názvů a obory názvů by měl končit `.Design` a `.Permissions`v uvedeném pořadí.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, zkuste kombinovat obory názvů, které obsahují typy, několika do jednoho oboru názvů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění tohoto pravidla, pokud obor názvů obsahuje typy, které se používají s typy v jiných obory názvů.