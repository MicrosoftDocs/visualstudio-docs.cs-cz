---
title: 'CA1020: Vyhněte se oborům názvu s malým množstvím typů'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e5c50f607253304b05dd7ab9350646a0df05e70
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236233"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Vyhněte se oborům názvu s malým množstvím typů

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Obor názvů jiný než globální obor názvů obsahuje méně než pět typů.

## <a name="rule-description"></a>Popis pravidla

Ujistěte se, že každý z vašich oborů názvů má logickou organizaci a že existuje platný důvod pro vložení typů do zhuštěně naplněných oborů názvů. Obory názvů by měly obsahovat typy, které se ve většině scénářů používají společně. Pokud se jejich aplikace vzájemně vylučují, typy by měly být umístěny v samostatných oborech názvů. Například <xref:System.Web.UI> obor názvů obsahuje typy, které se používají ve webových aplikacích, <xref:System.Windows.Forms> a obor názvů obsahuje typy, které jsou používány v [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]aplikacích založených na aplikaci. I když oba obory názvů mají typy, které řídí aspekty uživatelského rozhraní, tyto typy nejsou navrženy pro použití ve stejné aplikaci. Proto jsou umístěny v samostatných oborech názvů. Pečlivé uspořádání oboru názvů může být užitečné také proto, že zvyšuje zjistitelnost funkce. Po prozkoumání hierarchie oboru názvů by příjemci knihovny měli být schopni najít typy, které implementují funkci.

> [!NOTE]
> Typy a oprávnění v době návrhu by neměly být sloučeny do jiných oborů názvů, aby bylo možné tyto zásady dodržovat. Tyto typy patří do svých vlastních oborů názvů pod hlavním oborem názvů a obory názvů by `.Design` měly `.Permissions`končit a, v uvedeném pořadí.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, zkuste kombinovat obory názvů, které obsahují pouze pár typů, do jednoho oboru názvů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

V případě, že obor názvů neobsahuje typy, které se používají s typy v jiných oborech názvů, je bezpečné potlačit upozornění od tohoto pravidla.