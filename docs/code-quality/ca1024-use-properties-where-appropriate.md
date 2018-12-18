---
title: 'CA1024: Použijte vlastnosti, kde je to vhodné'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f74c41584c8dc8960adce2bd253f7d1c38707f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823213"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Použijte vlastnosti, kde je to vhodné

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Veřejná nebo chráněná metoda má název, který začíná `Get`, nepřijímá žádné parametry a vrátí hodnotu, která není pole.

## <a name="rule-description"></a>Popis pravidla

Ve většině případů vlastnosti představují data a provedení metody akce. Vlastnosti jsou dostupné jako pole, které usnadňují jejich použití. Metoda je vhodným kandidátem pro stala vlastností, pokud se nachází jedna z těchto podmínek:

- Nepřijímá žádné argumenty a vrátí informace o stavu objektu.

- Přijímá jeden argument nastavit některá část stav objektu.

Vlastnosti by měla chovat, jako by šlo polí. Pokud nelze metodu by neměla změnit na vlastnost. Metody jsou lepší než vlastnosti v následujících situacích:

- Metoda provádí časově náročná operace. Metoda je perceivably pomalejší než čas, který je potřeba nastavit nebo získat hodnotu pole.

- Metoda provádí převod. Přístup k poli nevrací převedená verze tohoto data, která ukládá.

- Metoda Get má pozorovatelný vedlejší efekt. Načítání hodnoty pole nevytváří žádné vedlejší účinky.

- Je důležité pořadí provádění. Nastaví hodnotu pole není závislý na výskyt jiné operace.

- Volání metody dvakrát za sebou vytvoří jiné výsledky.

- Metoda je statická, ale vrátí objekt, který můžete změnit tak, volající. Načítání hodnoty pole neumožňuje volajícího, aby změna dat uložených v poli.

- Metoda vrátí pole.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, změňte metodu na vlastnost.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění tohoto pravidla, pokud metoda splňuje splnit aspoň jednu z výše uvedených kritérií.

## <a name="controlling-property-expansion-in-the-debugger"></a>Řízení vlastnosti rozšíření v ladicím programu

Jedním z důvodů, programátoři Vyhněte se použití vlastnosti je vzhledem k tomu, že nechtějí ladicí program automaticky-rozbalte ho. Například vlastnost může zahrnovat přidělování velkého objektu nebo volání P/Invoke, ale nemusí mít ve skutečnosti všechny pozorovatelný vedlejší účinky.

Ladicí program může zabránit automatické rozšiřování vlastnosti použitím <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. Následující příklad ukazuje tento atribut použity pro vlastnost instance.

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
}
```

## <a name="example"></a>Příklad

Následující příklad obsahuje několik metod, které mají být převedeny do vlastností a několik, který by nebyl, protože není chovají jako pole.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]