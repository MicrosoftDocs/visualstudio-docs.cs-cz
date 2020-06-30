---
title: 'CA1024: použijte vlastnosti, kde je to vhodné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a240a6eea86075bbf7f721f8620b6d135d594c20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546663"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Použijte vlastnosti, kde je to vhodné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejná nebo chráněná metoda má název, který začíná `Get` , nepřebírá žádné parametry a vrací hodnotu, která není polem.

## <a name="rule-description"></a>Popis pravidla
 Ve většině případů vlastnosti reprezentují data a metody, které provádějí akce. Vlastnosti jsou dostupné jako pole, což usnadňuje jejich použití. Metoda je dobrým kandidátem, který se stane vlastností, pokud je přítomna jedna z těchto podmínek:

- Nepřijímá žádné argumenty a vrací informace o stavu objektu.

- Přijímá jeden argument pro nastavení některých částí stavu objektu.

  Vlastnosti by se měly chovat, jako by se jedná o pole. Pokud metoda nemůže, neměla by být změněna na vlastnost. Metody jsou lepší než vlastnosti v následujících situacích:

- Metoda provádí časově náročnou operaci. Metoda je vnímana pomalejší než čas, který je požadován k nastavení nebo získání hodnoty pole.

- Metoda provádí převod. Přístup k poli nevrátí převedenou verzi dat, která ukládá.

- Metoda get má pozorovatelný vedlejší efekt. Načtení hodnoty pole neprodukuje žádné vedlejší účinky.

- Pořadí spuštění je důležité. Nastavení hodnoty pole nezávisí na výskytu jiných operací.

- Volání metody dvakrát v případě úspěchu vytváří různé výsledky.

- Metoda je statická, ale vrací objekt, který může změnit volající. Načítání hodnoty pole neumožňuje volajícímu měnit data, která jsou uložena v poli.

- Metoda vrací pole.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte metodu na vlastnost.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla, pokud metoda splňuje alespoň jedno z výše uvedených kritérií.

## <a name="controlling-property-expansion-in-the-debugger"></a>Řízení rozšíření vlastností v ladicím programu
 Jedním z důvodů, proč programátoři nepoužívají vlastnost, je, že nechtějí, aby ladicí program automaticky rozbalí. Například vlastnost může zahrnovat přidělení velkého objektu nebo volání volání nespravovaného objektu, ale nemusí mít ve skutečnosti žádné pozorovatelné vedlejší účinky.

 Ladicímu programu můžete zabránit v automatickém rozbalování vlastností, a to použitím <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName> . Následující příklad ukazuje tento atribut aplikovaný na vlastnost instance.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>Příklad
 Následující příklad obsahuje několik metod, které by měly být převedeny na vlastnosti a několik, které by neměly být stejné, protože se chovají jako pole.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
