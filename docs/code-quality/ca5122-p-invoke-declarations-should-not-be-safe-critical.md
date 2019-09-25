---
title: 'CA5122: Deklarace volání nespravovaného kódu nesmí být kritické pro zabezpečení'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7922681307b576f8da523cdd08fb808fb36b3d8c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237003"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122: Deklarace volání nespravovaného kódu nesmí být kritické pro zabezpečení

|||
|-|-|
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|
|CheckId|CA5122|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Deklarace P/Invoke byla označena jako <xref:System.Security.SecuritySafeCriticalAttribute>:

```csharp
[assembly: AllowPartiallyTrustedCallers]

// ...
public class C
{
    [SecuritySafeCritical]
    [DllImport("kernel32.dll")]
    public static extern bool Beep(int frequency, int duration); // CA5122 - safe critical p/invoke
   }
```

V tomto příkladu `C.Beep(...)` byla označena jako zabezpečená kritická metoda zabezpečení.

## <a name="rule-description"></a>Popis pravidla
Metody jsou při provádění operace citlivé na zabezpečení označeny jako SecuritySafeCritical, ale lze je také bezpečně použít transparentním kódem. Jedním ze základních pravidel modelu transparentnosti zabezpečení je, že transparentní kód nikdy nesmí přímo volat nativní kód prostřednictvím deklarace P/Invoke. Proto označení P/Invoke jako bezpečně kritické z hlediska zabezpečení neumožní transparentnímu kódu vyvolat je a je zavádějící pro analýzu zabezpečení.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Aby byla deklarace P/Invoke zpřístupněna pro transparentní kód, vystavte pro něj z hlediska zabezpečení bezpečně kritickou obalující metodu.

```csharp
[assembly: AllowPartiallyTrustedCallers

class C
{
   [SecurityCritical]
   [DllImport("kernel32.dll", EntryPoint="Beep")]
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke

   [SecuritySafeCritical]
   public static bool Beep(int frequency, int duration)
   {
      return BeepPInvoke(frequency, duration);
   }
}
```

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.