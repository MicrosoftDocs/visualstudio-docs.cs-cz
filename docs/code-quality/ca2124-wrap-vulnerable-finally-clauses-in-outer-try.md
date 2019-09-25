---
title: 'CA2124: Zabalte ohroženou klauzuli finally do vnějšího bloku try'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0008767f7d37e2c088dad58a328b025f81090ad8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232452"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Zabalte ohroženou klauzuli finally do vnějšího bloku try

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Ve verzích 1,0 a 1,1 .NET Framework metoda Public nebo Protected obsahuje `try` / `catch` / `finally` blok. Blokování se jeví jako resetování stavu zabezpečení a není uzavřeno `finally` v bloku. `finally`

## <a name="rule-description"></a>Popis pravidla
Toto pravidlo vyhledá `try` / `finally` bloky v kódu, které cílí na verze 1,0 a 1,1 .NET Framework, které mohou být ohroženy škodlivými filtry výjimek přítomnými v zásobníku volání. Pokud v bloku try dojde k citlivým operacím, jako je například zosobnění, a je vyvolána výjimka, může být filtr spuštěn `finally` před blokem. Pro příklad zosobnění to znamená, že se filtr spustí jako zosobněný uživatel. Filtry jsou aktuálně implementovány pouze v Visual Basic.

> [!NOTE]
> Ve verzích 2,0 a novějších .NET Framework modul runtime automaticky chrání `try` / `catch` /  `finally` blok před škodlivými filtry výjimek, pokud dojde k resetování přímo v rámci metody, kterou obsahuje blok výjimky.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Umístěte nezabalený `try` / `finally` do vnějšího bloku try. Podívejte se na druhý příklad, který následuje. To vynutí `finally` , aby bylo provedeno před filtrem kódu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="pseudo-code-example"></a>Příklad kódu pseudo-code

### <a name="description"></a>Popis

Následující pseudo kód ilustruje vzor zjištěný tímto pravidlem.

```csharp
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

Následující pseudo kód ukazuje vzor, který můžete použít k ochraně kódu a splnění tohoto pravidla.

```csharp
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```