---
title: 'CA1020: Vyvarujte se oborům názvu s malým množstvím typů'
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
ms.openlocfilehash: d13f4e9308e77cc723703394a4295273b5facef1
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441631"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Vyvarujte se oborům názvu s malým množstvím typů

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategorie|Microsoft. Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Obor názvů jiný než globální obor názvů obsahuje méně než pět typů.

## <a name="rule-description"></a>Popis pravidla

Ujistěte se, že každý z vašich oborů názvů má logickou organizaci a že existuje platný důvod pro vložení typů do zhuštěně naplněných oborů názvů. Obory názvů by měly obsahovat typy, které se ve většině scénářů používají společně. Pokud se jejich aplikace vzájemně vylučují, typy by měly být umístěny v samostatných oborech názvů. Například obor názvů <xref:System.Web.UI> obsahuje typy, které se používají ve webových aplikacích, a obor názvů <xref:System.Windows.Forms> obsahuje typy, které se používají v aplikacích založených na @no__t -2. I když oba obory názvů mají typy, které řídí aspekty uživatelského rozhraní, tyto typy nejsou navrženy pro použití ve stejné aplikaci. Proto jsou umístěny v samostatných oborech názvů. Pečlivé uspořádání oboru názvů může být užitečné také proto, že zvyšuje zjistitelnost funkce. Po prozkoumání hierarchie oboru názvů by příjemci knihovny měli být schopni najít typy, které implementují funkci.

> [!NOTE]
> Typy a oprávnění v době návrhu by neměly být sloučeny do jiných oborů názvů, aby bylo možné tyto zásady dodržovat. Tyto typy patří do svých vlastních oborů názvů pod hlavním oborem názvů a obory názvů by měly končit `.Design` a `.Permissions` v uvedeném pořadí.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, zkuste kombinovat obory názvů, které obsahují pouze pár typů, do jednoho oboru názvů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

V případě, že obor názvů neobsahuje typy, které se používají s typy v jiných oborech názvů, je bezpečné potlačit upozornění od tohoto pravidla.
