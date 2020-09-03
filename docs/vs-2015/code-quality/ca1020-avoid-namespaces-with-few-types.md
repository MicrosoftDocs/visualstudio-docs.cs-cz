---
title: 'CA1020: Vyhněte se oborům názvů s malým počtem typů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ddd69c62eb4d6b818410a588967c1e23f164f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546728"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Vyhněte se oborům názvu s malým množstvím typů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Obor názvů jiný než globální obor názvů obsahuje méně než pět typů.

## <a name="rule-description"></a>Popis pravidla
 Ujistěte se, že každý z vašich oborů názvů má logickou organizaci a že existuje platný důvod pro vložení typů do zhuštěně naplněných oborů názvů. Obory názvů by měly obsahovat typy, které se ve většině scénářů používají společně. Pokud se jejich aplikace vzájemně vylučují, typy by měly být umístěny v samostatných oborech názvů. Například <xref:System.Web.UI> obor názvů obsahuje typy, které se používají ve webových aplikacích, a <xref:System.Windows.Forms> obor názvů obsahuje typy, které jsou používány v [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] aplikacích založených na aplikaci. I když oba obory názvů mají typy, které řídí aspekty uživatelského rozhraní, tyto typy nejsou navrženy pro použití ve stejné aplikaci. Proto jsou umístěny v samostatných oborech názvů. Pečlivé uspořádání oboru názvů může být užitečné také proto, že zvyšuje zjistitelnost funkce. Po prozkoumání hierarchie oboru názvů by příjemci knihovny měli být schopni najít typy, které implementují funkci.

> [!NOTE]
> Typy a oprávnění v době návrhu by neměly být sloučeny do jiných oborů názvů, aby bylo možné tyto zásady dodržovat. Tyto typy patří do svých vlastních oborů názvů pod hlavním oborem názvů a obory názvů by měly končit `.Design` a `.Permissions` , v uvedeném pořadí.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zkuste kombinovat obory názvů, které obsahují pouze pár typů, do jednoho oboru názvů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že obor názvů neobsahuje typy, které se používají s typy v jiných oborech názvů, je bezpečné potlačit upozornění od tohoto pravidla.
