---
title: 'CA1806: neignorujte výsledky metody | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f68ab71d9ce4fab1b0612f15d866c58e302a317e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671498"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Neignorujte výsledky metody
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Toto upozornění může mít několik možných důvodů:

- Vytvoří se nový objekt, ale nikdy se nepoužije.

- Metoda, která vytvoří a vrátí nový řetězec, je volána a nový řetězec se nikdy nepoužije.

- Metoda COM nebo volání nespravovaného kódu, která vrací hodnotu HRESULT nebo kód chyby, který se nikdy nepoužívá. Popis pravidla

  Zbytečným vytvářením objektů a přidruženým uvolňováním paměti nevyužitého objektu, který snižuje výkon.

  Řetězce jsou neměnné a metody, jako je String. ToUpper vrací novou instanci řetězce namísto úpravy instance řetězce v volající metodě.

  Ignorování HRESULT nebo kód chyby může vést k neočekávanému chování v chybových stavech nebo v podmínkách s nízkými prostředky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud metoda A vytvoří novou instanci objektu B, který se nikdy nepoužívá, předejte instanci jako argument jiné metodě nebo přiřaďte instanci proměnné. Pokud je vytvoření objektu zbytečné, odeberte ho.-nebo-

 Pokud metoda volá metodu B, ale nepoužívá novou instanci řetězce, kterou metoda B vrátí. Předejte instanci jako argument jiné metodě, přiřaďte instanci proměnné. Nebo odeberte volání, pokud není nutné.

 -nebo-

 Pokud metoda volá metodu B, ale nepoužívá HRESULT nebo kód chyby, který metoda vrátí. Použijte výsledek v podmíněném příkazu, přiřaďte výsledek proměnné nebo ji předejte jako argument jiné metodě.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla, pokud se nejedná o vytvoření objektu, který slouží k nějakému účelu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje třídu, která ignoruje výsledek volání String. trim.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>Příklad
 Následující příklad opravuje předchozí porušení přiřazením výsledku String. střih zpět na proměnnou, na které byla volána.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která nepoužívá objekt, který je vytvořen.

> [!NOTE]
> Toto porušení nelze reprodukovat v Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>Příklad
 Následující příklad opravuje předchozí porušení odebráním zbytečného vytvoření objektu.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která ignoruje kód chyby, který vrátí nativní metoda GetShortPathName.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad opravuje předchozí porušení kontrolou kódu chyby a vyvoláním výjimky při selhání volání.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]