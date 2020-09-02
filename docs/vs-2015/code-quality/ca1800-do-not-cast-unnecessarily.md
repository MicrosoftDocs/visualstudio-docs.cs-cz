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
ms.openlocfilehash: 757d66ef719b3a1f39a9164dfd50ce1fcf8799db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547794"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Nepřetypujte zbytečně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Metoda provádí duplicitní přetypování na jednom z jeho argumentů nebo místních proměnných. Pro úplnou analýzu podle tohoto pravidla musí být testované sestavení sestaveno pomocí informací o ladění a přidružený soubor databáze programu (PDB) musí být k dispozici.

## <a name="rule-description"></a>Popis pravidla
 Duplicitní přetypování snižuje výkon, zvláště když jsou přetypování vykonána v příkazech kompaktní iterace. U explicitních operací přetypování uložte výsledek přetypování do místní proměnné a místo duplicitních operací přetypování použijte místní proměnnou.

 Pokud operátor jazyka C# `is` slouží k otestování, zda bude přetypování úspěšné před samotným přetypováním, zvažte místo toho testování výsledku `as` operátoru. To poskytuje stejnou funkčnost bez operace implicitního přetypování, kterou provádí `is` operátor.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, upravte implementaci metody tak, aby minimalizovala počet operací přetypování.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění nebo pravidlo ignorovat, pokud výkon nezáleží na výkonu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která porušuje pravidlo pomocí `is` operátoru jazyka C#. Druhá metoda splňuje pravidlo tím, že nahrazuje `is` operátor s testem proti výsledku `as` operátoru, což snižuje počet operací přetypování na iteraci od dvou k jednomu.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, `start_Click` , která má více duplicitní explicitní přetypování, které porušují pravidlo a metodu, `reset_Click` která splňuje pravidlo uložením přetypování do místní proměnné.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Viz také
 [jak](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [je](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
