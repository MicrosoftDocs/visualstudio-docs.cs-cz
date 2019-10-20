---
title: 'CA2233: operace by neměly přetečení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 70a0bab8cfb3bf14a763f759e0e44a754ad878d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662783"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Operace by neměly přetéct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Metoda provede aritmetickou operaci a předem neověřuje operandy, aby se zabránilo přetečení.

## <a name="rule-description"></a>Popis pravidla
 Aritmetické operace by se neměly provádět bez prvotního ověření operandů, aby se zajistilo, že výsledek operace není mimo rozsah možných hodnot datových typů, které jsou v provozu. V závislosti na kontextu spuštění a na zahrnutých datových typech může aritmetické přetečení způsobit <xref:System.OverflowException?displayProperty=fullName> nebo nejvýznamnější bity výsledku.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, před provedením operace ověřte operandy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění, pokud možné hodnoty operandů nebudou nikdy způsobit přetečení aritmetické operace.

## <a name="example-of-a-violation"></a>Příklad porušení

### <a name="description"></a>Popis
 Metoda v následujícím příkladu zpracovává celé číslo, které toto pravidlo porušuje. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] vyžaduje, aby byla zablokována možnost **Odebrat** přetečení celého čísla, aby se aktivovala.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Komentáře
 Pokud je metoda v tomto příkladu předána <xref:System.Int32.MinValue?displayProperty=fullName>, operace by měla podtečení. To způsobí, že je nejvýznamnější bit výsledku zahozen. Následující kód ukazuje, jak se to stane.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 JAZYK

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Výstup

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Opravit se vstupním parametrem ověřování

### <a name="description"></a>Popis
 Následující příklad opravuje předchozí porušení ověřením hodnoty vstup.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Oprava pomocí kontrolovaného bloku

### <a name="description"></a>Popis
 Následující příklad opravuje předchozí porušení tím, že zabalí operaci do kontrolovaného bloku. Pokud operace způsobí přetečení, bude vyvolána <xref:System.OverflowException?displayProperty=fullName>.

 Všimněte si, že zaškrtnuté bloky nejsou v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] podporovány.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Zapnout kontrolované aritmetické přetečení nebo podtečení
 Pokud zapnete kontrolované aritmetické přetečení nebo podtečení C#v, je ekvivalentem zabalení každé celočíselné operace do kontrolovaného bloku.

 **Zapnutí kontrolovaného aritmetického přetečení nebo podtečení vC#**

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **vlastnosti**.

2. Vyberte kartu **sestavení** a klikněte na **Upřesnit**.

3. Vyberte možnost **kontrolovat aritmetické přetečení a podtečení** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také
 <xref:System.OverflowException?displayProperty=fullName> [ C# operátory](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) byly [zkontrolovány a nezaškrtnutoy](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e) .
