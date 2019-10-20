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
ms.openlocfilehash: 7a2a296f5dd3680209c14849b5bd863c01e6351d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660237"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Zabalte ohroženou klauzuli finally do vnějšího bloku try
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Ve verzích 1,0 a 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] obsahuje veřejná nebo chráněná metoda `try` / `catch` / `finally` bloku. Blok `finally` se jeví pro resetování stavu zabezpečení a není uzavřený v bloku `finally`.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo vyhledá `try` / `finally` bloky v kódu, které cílí na verze 1,0 a 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], které mohou být v zásobníku volání ohroženy škodlivými filtry výjimek. Pokud v bloku try dojde k citlivým operacím, jako je například zosobnění, a je vyvolána výjimka, může být filtr spuštěn před blokem `finally`. Pro příklad zosobnění to znamená, že se filtr spustí jako zosobněný uživatel. Filtry jsou aktuálně implementovány pouze v Visual Basic.

> [!WARNING]
> Ve verzích 2,0 a novějších [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modul runtime automaticky chrání `try` / `catch` /  `finally` bloku z škodlivých filtrů výjimek, pokud dojde k resetování přímo v rámci metody, která obsahuje blok výjimky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Umístit nezabalenou `try` / `finally` do vnějšího bloku try. Podívejte se na druhý příklad, který následuje. To vynutí spuštění `finally` před kódem filtru.

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
