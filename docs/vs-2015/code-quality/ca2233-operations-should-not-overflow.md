---
title: 'CA2233: Operace by neměly přetéct. | Dokumentace Microsoftu'
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
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5f6690f6577d936757ae3bbe8b725b4434b6bee1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836655"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Operace by neměly přetéct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Metoda provádí aritmetické operace a neověřuje operandy předem, aby zabránil přetečení.

## <a name="rule-description"></a>Popis pravidla
 Aritmetické operace by neměly provést bez prvního ověřování operandů, abyste měli jistotu, že výsledek operace není mimo rozsah možných hodnot pro typy dat zapojených. V závislosti na kontextu spuštění a souvisejících datových typech, může způsobit přetečení aritmetické operace v jednom <xref:System.OverflowException?displayProperty=fullName> nebo zahozeny nejvýznamnější části výsledku.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, ověření operandů před provedením operace.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, je-li možné hodnoty z operandů nikdy nezpůsobí Přetečení aritmetické operace.

## <a name="example-of-a-violation"></a>Příkladem porušení

### <a name="description"></a>Popis
 Metoda v následujícím příkladu manipuluje s celým číslem, který porušuje tato pravidla. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] vyžaduje **odebrat** možnost přetečení celého čísla pro to, aby se mohly aktivovat deaktivuje.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Komentáře
 Pokud je předán metodě v tomto příkladu <xref:System.Int32.MinValue?displayProperty=fullName>, operace by podtečení. To způsobí, že nejvýznamnější bit výsledek, který má být zrušena. Následující kód ukazuje, jak k tomu dochází.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

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

## <a name="fix-with-input-parameter-validation"></a>Oprava pomocí ověření vstupu parametru

### <a name="description"></a>Popis
 Následující příklad opravuje předchozí porušení ověřením hodnotu vstupu.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Oprava s bloku Checked

### <a name="description"></a>Popis
 Následující příklad opravuje předchozí porušení obalením operaci v vybraný blok. Pokud operace způsobí přetečení, <xref:System.OverflowException?displayProperty=fullName> bude vyvolána výjimka.

 Všimněte si, že kontrolovaný bloky se nepodporují v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Zapnout Checked aritmetické přetečení a podtečení
 Pokud zapnete checked aritmetické přetečení a podtečení v jazyce C#, je ekvivalentní obtékání každé operace celé číslo v vybraný blok.

 **Chcete-li zaškrtnutí aritmetické přetečení a podtečení v jazyce C#**

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a zvolte **vlastnosti**.

2.  Vyberte **sestavení** kartě a klikněte na tlačítko **Upřesnit**.

3.  Vyberte **kontrolovat aritmetické přetečení a podtečení** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také
 <xref:System.OverflowException?displayProperty=fullName> [Operátory jazyka C#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [zaškrtnuto a nezaškrtnuto](http://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)



