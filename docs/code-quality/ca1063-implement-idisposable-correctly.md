---
title: 'CA1063: Implementuje správně IDisposable'
ms.date: 02/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: e202c35ee6bd8353170e758629b1cc6e739b775d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080968"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementuje správně IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina

<xref:System.IDisposable?displayProperty=nameWithType> Není správně implementovaná rozhraní. Možné příčiny tohoto stavu:

- <xref:System.IDisposable> je reimplemented ve třídě.

- Dokončení je reoverridden.

- Dispose() je přepsána.

- Metoda Dispose() není veřejný, [zapečetěné](/dotnet/csharp/language-reference/keywords/sealed), nebo s názvem **Dispose**.

- Dispose(bool) není chráněný, virtuální nebo nezapečetěné.

- V nezapečetěné typy musí volat Dispose() Dispose(true).

- Pro nezapečetěné typy nevolá Finalize implementaci Dispose(bool) jednoho nebo obou nebo finalizační metodu třídy base.

Porušení některou z těchto vzorců se aktivuje upozornění CA1063.

Každý nezapečetěný typ, který deklaruje a implementuje <xref:System.IDisposable> rozhraní musíte zadat své vlastní chráněné virtuální void Dispose(bool) metody. Dispose() by měly volat Dipose(true) a finalizační metody by měly volat Dispose(false). Pokud vytvoříte nezapečetěný typ, který deklaruje a implementuje <xref:System.IDisposable> rozhraní, je nutné definovat Dispose(bool) a jeho volání. Další informace najdete v tématu [vyčistit nespravované prostředky (Průvodce technologií .NET)](/dotnet/standard/garbage-collection/unmanaged) a [vzor Dispose](/dotnet/standard/design-guidelines/dispose-pattern).

## <a name="rule-description"></a>Popis pravidla

Všechny <xref:System.IDisposable> typy by měly implementovat [vzor Dispose](/dotnet/standard/design-guidelines/dispose-pattern) správně.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Prozkoumat kód a určit, které z následujících řešení vyřeší porušení:

- Odebrat <xref:System.IDisposable> ze seznamu rozhraní, které jsou implementovány podle typu a místo toho přepište implementaci Dispose základní třídy.

- Odeberte finalizační metodu z typu, přepište Dispose (bool disposing) a vložte finalizační logiku do cesty kódu, kde je 'disposing ' hodnoty false.

- Přepište Dispose (bool disposing) a vložte finalizační logiku do cesty kódu, kde je 'disposing ' hodnoty true.

- Ujistěte se, že je deklarována jako veřejná Dispose() a [zapečetěné](/dotnet/csharp/language-reference/keywords/sealed).

- Přejmenovat metodu dispose k **Dispose** a ujistěte se, že je deklarována jako veřejná a [zapečetěné](/dotnet/csharp/language-reference/keywords/sealed).

- Ujistěte se, že Dispose(bool) je deklarována jako chráněná, virtuální a nezapečetěná.

- Upravit Dispose() tak, že volá Dispose(true), poté volá <xref:System.GC.SuppressFinalize%2A> na aktuální instanci objektu (`this`, nebo `Me` v jazyce Visual Basic) a potom se vrací.

- Upravte vaše finalizační metodu tak, že volá Dispose(false) a potom se vrací.

- Pokud vytvoříte nezapečetěný typ, který deklaruje a implementuje <xref:System.IDisposable> rozhraní, ujistěte se, že implementace <xref:System.IDisposable> má následující formát, který je popsán výše v této části.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="pseudo-code-example"></a>Příklad pseudo kódu

Následující kód pseudo poskytuje obecné příklad, jak Dispose(bool) by měla být implementována ve třídě, která používá spravované a nativní prostředky.

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

- [(Pokyny k návrhu architektury) vzor dispose](/dotnet/standard/design-guidelines/dispose-pattern)
- [Vyčistit nespravované prostředky (Průvodce technologií .NET)](/dotnet/standard/garbage-collection/unmanaged)