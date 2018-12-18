---
title: 'CA1804: Odeberte nepoužívané místní hodnoty | Dokumentace Microsoftu'
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
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4d7982ad4fd7e9785634b3b729af4057b8179381
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928409"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Odeberte nepoužívané místní hodnoty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategorie|Microsoft.Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Metoda deklaruje místní proměnnou, ale nepoužívá proměnnou s výjimkou pravděpodobně jako příjemce příkazu přiřazení. Pro analýzu tímto pravidlem testované sestavení musí být sestaveny s ladicími informacemi a přidružené programového souboru databáze (PDB) musí být k dispozici.

## <a name="rule-description"></a>Popis pravidla
 Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte nebo použijte místní proměnnou. Všimněte si, že kompilátor jazyka C#, která je součástí [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] odebere nepoužívané místní proměnné při `optimize` je povolená možnost.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla, je-li proměnná byla kompilátoru, protože ho. Je také bezpečné upozornění tohoto pravidla můžete potlačit nebo zakážete pravidlo, pokud výkon a údržba kódu nejsou primární obavy.

## <a name="example"></a>Příklad
 Následující příklad ukazuje několik nepoužívané místní proměnné.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1809: Vyhněte se nadměrným místním hodnotám](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Vyhněte se nevolanému místnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Vyhněte se nevytvořeným instancím vnitřních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Revize nepoužitých parametrů](../code-quality/ca1801-review-unused-parameters.md)



