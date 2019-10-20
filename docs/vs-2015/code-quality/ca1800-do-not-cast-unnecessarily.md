---
title: 'CA1800: Nepřetypujte zbytečně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 466309cef8905faa9b659e2d3652975d815767fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663108"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Nepřetypujte zbytečně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Metoda provádí duplicitní přetypování na jednom z jeho argumentů nebo místních proměnných. Pro úplnou analýzu podle tohoto pravidla musí být testované sestavení sestaveno pomocí informací o ladění a přidružený soubor databáze programu (PDB) musí být k dispozici.

## <a name="rule-description"></a>Popis pravidla
 Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace. U explicitních operací přetypování uložte výsledek přetypování do místní proměnné a místo duplicitních operací přetypování použijte místní proměnnou.

 Pokud operátor C# `is` slouží k otestování, zda bude přetypování úspěšné před samotným přetypováním, zvažte místo toho testování výsledku operátoru `as`. To poskytuje stejné funkce bez operace implicitního přetypování, které provádí operátor `is`.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, upravte implementaci metody tak, aby minimalizovala počet operací přetypování.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění nebo pravidlo ignorovat, pokud výkon nezáleží na výkonu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která porušuje pravidlo pomocí operátoru C# `is`. Druhá metoda splňuje pravidlo tím, že nahrazuje operátor `is` s testem proti výsledku operátoru `as`, který snižuje počet operací přetypování na iteraci od dvou k jednomu.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, `start_Click`, která má více duplicitní explicitní přetypování, které porušuje pravidlo a metodu, `reset_Click`, která splňuje pravidlo uložením přetypování do místní proměnné.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Viz také
 [jak](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [je](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
