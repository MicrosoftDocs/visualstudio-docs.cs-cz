---
title: 'CA1806: Neignorujte výsledky metody'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
dev_langs:
- CPP
- CSharp
- VB
manager: douge
ms.openlocfilehash: ebbad9eb48a448aa756f580ade794ba70eb25611
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546834"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Neignorujte výsledky metody

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Existuje několik možných důvodů pro toto upozornění:

- Nový objekt je vytvořen, ale nepoužilo.

- Volá metodu, která vytvoří a vrátí nový řetězec a nový řetězec se nikdy nepoužívá.

- COM nebo P/Invoke metoda, která vrátí HRESULT nebo kód chyby, který se nikdy nepoužívá. Popis pravidla

Vytváření zbytečné objektů a související uvolňování nepoužívané objektu dojít ke snížení výkonu.

Řetězce jsou neměnné a metod, jako je například String.ToUpper vrací novou instanci řetězce místo úpravy instanci řetězce ve volání metody.

Ignorování HRESULT nebo kód chyby může vést k neočekávanému chování chybových podmínek a ujednání nedostatku prostředků.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud metoda A vytvoří novou instanci objektu B, který se nikdy nepoužívá, předejte instanci jako argument jiné metodě, nebo přiřaďte instanci proměnné. Pokud vytvoření objektu je zbytečné, odeberte něm- nebo -

 Pokud metoda A volá metodu B, ale nepoužívá novou instanci řetězce, který vrací metoda B. Předejte instanci jako argument jiné metodě, přiřaďte instanci proměnné. Nebo odebrat volání, pokud je zbytečné.

 -nebo-

 Pokud metoda A volá metodu B, ale nepoužívá HRESULT nebo kód chyby, který metoda vrátí. Použijte výsledek v podmíněném příkazu, výsledek přiřaďte proměnné nebo předejte jako argument jiné metodě.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění tohoto pravidla, pokud při vytvoření objektu slouží některé účelu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje třídu, která se bude ignorovat, výsledek volání String.Trim.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>Příklad
 Následující příklad opravuje předchozí porušení přiřazením výsledek String.Trim zpět do proměnné, které byla volána pro.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která nepoužívá objekt, který vytvoří.

> [!NOTE]
> Toto porušení nelze reprodukovat v jazyce Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>Příklad
 Následující příklad opravuje předchozí porušení odebráním nepotřebných vytvoření objektu.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->