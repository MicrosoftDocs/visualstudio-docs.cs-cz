---
title: 'CA2233: Operace by neměly přetéct'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 73c0e616eb527a2213c77cdae00c42635d49b130
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938900"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Operace by neměly přetéct

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Metoda provádí aritmetické operace a neověřuje operandy předem, aby zabránil přetečení.

## <a name="rule-description"></a>Popis pravidla

Aritmetické operace není provést bez prvního ověřování operandů, abyste měli jistotu, že výsledek operace není mimo rozsah možných hodnot pro typy dat zapojených. V závislosti na kontextu spuštění a souvisejících datových typech, může způsobit přetečení aritmetické operace v jednom <xref:System.OverflowException?displayProperty=fullName> nebo zahozeny nejvýznamnější části výsledku.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, ověření operandů před provedením operace.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění tohoto pravidla, je-li možné hodnoty z operandů nikdy nezpůsobí Přetečení aritmetické operace.

## <a name="example-of-a-violation"></a>Příkladem porušení

Metoda v následujícím příkladu manipuluje s celým číslem, který porušuje tato pravidla. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] vyžaduje **odebrat** možnost přetečení celého čísla pro to, aby se mohly aktivovat deaktivuje.

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

Pokud je předán metodě v tomto příkladu <xref:System.Int32.MinValue?displayProperty=fullName>, operace by podtečení. To způsobí, že nejvýznamnější bit výsledek, který má být zrušena. Následující kód ukazuje, jak k tomu dochází.

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

Výstup:

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Oprava pomocí ověření vstupu parametru

Následující příklad opravuje předchozí porušení ověřením hodnotu vstupu.

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Oprava s bloku Checked

Následující příklad opravuje předchozí porušení obalením operaci v vybraný blok. Pokud operace způsobí přetečení, <xref:System.OverflowException?displayProperty=fullName> bude vyvolána výjimka.

Checked bloků nejsou podporovány v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Zapnout Checked aritmetické přetečení a podtečení

Pokud zapnete checked aritmetické přetečení a podtečení v jazyce C#, je ekvivalentní obtékání každé operace celé číslo v vybraný blok.

Chcete-li kontrolovat aritmetické přetečení a podtečení v jazyce C#:

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a zvolte **vlastnosti**.

2.  Vyberte **sestavení** kartě a klikněte na tlačítko **Upřesnit**.

3.  Vyberte **kontrolovat aritmetické přetečení a podtečení** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

- <xref:System.OverflowException?displayProperty=fullName>
- [Operátory jazyka C#](/dotnet/csharp/language-reference/operators/index)
- [Zaškrtnuto a nezaškrtnuto](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)