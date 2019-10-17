---
title: 'CA1063: Implementuje správně IDisposable'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 0fd4ba8d5dd5568dc7fca50ed61739b490bdcba7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440601"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementuje správně IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategorie|Microsoft. Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Rozhraní <xref:System.IDisposable?displayProperty=nameWithType> není správně implementované. Mezi možné příčiny patří:

- <xref:System.IDisposable> se znovu implementuje ve třídě.

- `Finalize` se znovu přepíše.

- `Dispose()` je přepsáno.

- Metoda `Dispose()` není veřejná, [zapečetěná](/dotnet/csharp/language-reference/keywords/sealed)ani s názvem **Dispose**.

- @no__t – 0 není chráněná, virtuální ani nezapečetěná.

- V nezapečetěných typech musí `Dispose()` volat `Dispose(true)`.

- Pro nezapečetěné typy neimplementuje implementace `Finalize` ani jednu `Dispose(bool)` nebo finalizační metodu základní třídy.

Porušení některého z těchto vzorů vyvolá upozornění CA1063.

Každý nezapečetěný typ, který deklaruje a implementuje rozhraní <xref:System.IDisposable>, musí poskytovat svou vlastní metodu `protected virtual void Dispose(bool)`. `Dispose()` by měl volat `Dispose(true)` a finalizační metoda by měla volat `Dispose(false)`. Pokud vytvoříte nezapečetěný typ, který deklaruje a implementuje rozhraní <xref:System.IDisposable>, je nutné definovat `Dispose(bool)` a zavolat ho. Další informace najdete v tématu [Vymazání nespravovaných prostředků (Průvodce .NET)](/dotnet/standard/garbage-collection/unmanaged) a [vzor Dispose](/dotnet/standard/design-guidelines/dispose-pattern).

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Všechny typy <xref:System.IDisposable> by měly implementovat správně [vzor Dispose](/dotnet/standard/design-guidelines/dispose-pattern) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Zkontrolujte svůj kód a určete, která z následujících řešení vyřeší toto porušení:

- Odeberte <xref:System.IDisposable> ze seznamu rozhraní implementovaných vaším typem a místo toho přepište implementaci Dispose základní třídy.

- Odeberte finalizační metodu z vašeho typu, přepište Dispose (bool disposing) a vložte logiku finalizace do cesty kódu, kde ' disposing ' má hodnotu false.

- Přepište Dispose (bool disposing) a vložte logiku Dispose do cesty kódu, kde má vlastnost ' disposing ' hodnotu true.

- Ujistěte se, že metoda Dispose () je deklarována jako veřejná a [zapečetěná](/dotnet/csharp/language-reference/keywords/sealed).

- Přejmenujte metodu Dispose k **Dispose** a ujistěte se, že je deklarována jako veřejná a [zapečetěná](/dotnet/csharp/language-reference/keywords/sealed).

- Ujistěte se, že metoda Dispose (bool) je deklarována jako chráněná, virtuální a nezapečetěná.

- Upravte Dispose () tak, že volá Dispose (true), pak zavolá <xref:System.GC.SuppressFinalize%2A> na aktuální instanci objektu (`this` nebo `Me` v Visual Basic) a pak se vrátí.

- Upravte finalizační metodu tak, že volá Dispose (false) a potom se vrátí.

- Pokud vytvoříte nezapečetěný typ, který deklaruje a implementuje rozhraní <xref:System.IDisposable>, ujistěte se, že implementace <xref:System.IDisposable> následuje vzor, který je popsán výše v této části.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Příklad kódu pseudo-code

Následující pseudo kód poskytuje obecný příklad, jak Dispose (bool) by měla být implementována ve třídě, která používá spravované a nativní prostředky.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>Viz také:

- [Vzor Dispose (pokyny pro návrh rozhraní)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Vyčištění nespravovaných prostředků (Průvodce .NET)](/dotnet/standard/garbage-collection/unmanaged)
