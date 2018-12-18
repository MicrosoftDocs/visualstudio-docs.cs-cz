---
title: 'CA1063: Implementujte IDisposable správně | Dokumentace Microsoftu'
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
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 94d13514800bac80723031c6bba7920d28ac83e6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877293"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementuje správně IDisposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 `IDisposable` není správně implementovaná. Tady jsou uvedené důvody tohoto problému:

- Rozhraní IDisposable se znovu implementované ve třídě.

- Dokončení je znovu přepsána.

- Metody Dispose je přepsána.

- Dispose() není veřejný, zapečetěné, nebo s názvem metody Dispose.

- Dispose(bool) není chráněný, virtuální nebo nezapečetěné.

- V nezapečetěné typy musí volat Dispose() Dispose(true).

- Pro nezapečetěné typy nevolá Finalize implementaci Dispose(bool) jednoho nebo obou nebo finalizační metodu třídy velikosti písmen.

  Porušení některou z těchto vzorců se aktivuje toto upozornění.

  Každý nezapečetěné kořenový typ IDisposable musíte zadat své vlastní chráněné virtuální void Dispose(bool) metody. Dispose() by měly volat Dipose(true) a Finalize by měly volat Dispose(false). Při vytváření typu IDisposable nezapečetěné root, musíte definovat Dispose(bool) a jeho volání. Další informace najdete v tématu [Cleaning Up Unmanaged Resources](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) v [pokyny k návrhu architektury](http://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) část dokumentace rozhraní .NET Framework.

## <a name="rule-description"></a>Popis pravidla
 Všechny typy IDisposable by měly správně implementovat vzor Dispose.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Prozkoumat kód a určete, které z následujících řešení opraví toto porušení.

-   Odeberte IDisposable ze seznamu rozhraní, které jsou implementované pomocí {0} a místo toho přepište implementaci Dispose základní třídy.

-   Odeberte finalizační metodu z typu {0}, přepište Dispose (bool disposing) a vložte finalizační logiku do cesty kódu, kde je 'disposing ' hodnoty false.

-   Odebrat {0}, přepište Dispose (bool disposing) a vložte finalizační logiku do cesty kódu, kde je 'disposing ' hodnoty true.

-   Ujistěte se, že {0} je deklarován jako veřejná a zapečetěná.

-   Přejmenovat {0} na 'Dispose' a ujistěte se, že je deklarována jako veřejná a zapečetěná.

-   Ujistěte se, že {0} je deklarována jako chráněná, virtuální a nezapečetěné.

-   Upravit {0} tak, že volá Dispose(true), poté volá uvolňování paměti. SuppressFinalize na aktuální instanci objektu ('this' nebo 'Me' v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) a potom se vrací.

-   Upravit {0} tak, že volá Dispose(false) a potom se vrací.

-   Pokud vytváříte třídu nezapečetěné kořenové IDisposable, ujistěte se, že implementace IDisposable má následující formát, který je popsaný výše v této části.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="pseudo-code-example"></a>Příklad pseudo kódu
 Následující kód pseudo poskytuje obecné příklad, jak Dispose(bool) by měla být implementována ve třídě, která používá spravované a nativní prostředky.

```
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
    // own unmanaged resources itself, but leave the other methods
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



