---
title: 'CA2124: zabalte zranitelnosti finally ve vnějším pokusu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e191ca10456f133e1213961ca2d1ed9cb8e040b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544297"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Zabalte ohroženou klauzuli finally do vnějšího bloku try
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Ve verzích 1,0 a 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] obsahuje metoda Public nebo Protected `try` / `catch` / `finally` blok. `finally`Blokování se jeví jako resetování stavu zabezpečení a není uzavřeno v `finally` bloku.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo vyhledá `try` / `finally` bloky v kódu, které cílí na verze 1,0 a 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , které mohou být ohroženy škodlivými filtry výjimek přítomnými v zásobníku volání. Pokud v bloku try dojde k citlivým operacím, jako je například zosobnění, a je vyvolána výjimka, může být filtr spuštěn před `finally` blokem. Pro příklad zosobnění to znamená, že se filtr spustí jako zosobněný uživatel. Filtry jsou aktuálně implementovány pouze v Visual Basic.

> [!WARNING]
> Ve verzích 2,0 a novějších [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , modul runtime automaticky chrání `try` / `catch` /  `finally` blok před škodlivými filtry výjimek, pokud dojde k resetování přímo v rámci metody, která obsahuje blok výjimky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Umístěte nezabalený `try` / `finally` do vnějšího bloku try. Podívejte se na druhý příklad, který následuje. To vynutí, `finally` aby bylo provedeno před filtrem kódu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="pseudo-code-example"></a>Příklad kódu pseudo-code

### <a name="description"></a>Popis
 Následující pseudo kód ilustruje vzor zjištěný tímto pravidlem.

### <a name="code"></a>Kód

```
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

## <a name="example"></a>Příklad
 Následující pseudo kód ukazuje vzor, který můžete použít k ochraně kódu a splnění tohoto pravidla.

```
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
