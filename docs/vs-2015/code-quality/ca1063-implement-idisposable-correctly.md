---
title: 'CA1063: Implementujte správně IDisposable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04691d2344b232906676180122ad67fff5405891
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539357"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementuje správně IDisposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 `IDisposable`není implementováno správně. Tady jsou uvedené nějaké důvody tohoto problému:

- Rozhraní IDisposable je znovu implementováno ve třídě.

- Finalizace je přepsána znovu.

- Dispose je přepsána.

- Dispose () není veřejná, zapečetěná nebo pojmenovaná Dispose.

- Dispose (bool) není chráněná, virtuální ani nezapečetěná.

- V nezapečetěných typech musí Dispose () volat Dispose (true).

- Pro nezapečetěné typy implementace Finalize nevolá buď metodu Dispose (bool), nebo finalizační metodu třídy Case.

  Toto upozornění se aktivuje při porušení některého z těchto vzorů.

  Každý nezapečetěný typ kořenového rozhraní IDisposable musí poskytovat svou vlastní chráněnou metodu virtual void Dispose (bool). Dispose () by měla volat Dispose (true) a Finalize by měla volat Dispose (false). Pokud vytváříte nezapečetěný typ IDisposable, je nutné definovat Dispose (bool) a zavolat ho. Další informace naleznete v tématu [Vymazání nespravovaných prostředků](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) v části [pokyny k návrhu rozhraní](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) v dokumentaci .NET Framework.

## <a name="rule-description"></a>Popis pravidla
 Všechny typy IDisposable by měly správně implementovat vzor Dispose.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Zkontrolujte svůj kód a určete, která z následujících řešení vyřeší toto porušení.

- Odeberte IDisposable ze seznamu rozhraní implementovaných pomocí {0} a místo toho přepište implementaci Dispose základní třídy.

- Odeberte finalizační metodu z typu {0} , přepište Dispose (bool disposing) a vložte logiku finalizace do cesty kódu, kde ' disposing ' je false.

- Odeberte {0} , přepište Dispose (bool disposing) a vložte logiku Dispose do cesty kódu, kde má vlastnost disposing hodnotu true.

- Ujistěte se, že {0} je deklarována jako veřejná a zapečetěná.

- Přejmenujte {0} na Dispose a ujistěte se, že je deklarována jako veřejná a zapečetěná.

- Ujistěte se, že {0} je deklarována jako chráněná, virtuální a nezapečetěná.

- Upravte {0} tak, že volá Dispose (true) a pak zavolá GC. SuppressFinalize na aktuální instanci objektu (' this ' nebo ' já ' v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) a pak se vrátí.

- Upravte {0} tak, že volá Dispose (false) a potom se vrátí.

- Pokud píšete nezapečetěnou kořenovou třídu IDisposable, ujistěte se, že implementace IDisposable následuje za vzorem popsaným výše v této části.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="pseudo-code-example"></a>Příklad kódu pseudo-code
 Následující pseudo kód poskytuje obecný příklad, jak Dispose (bool) by měla být implementována ve třídě, která používá spravované a nativní prostředky.

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
