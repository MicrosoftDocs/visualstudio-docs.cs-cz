---
title: 'CA1801: Přečtěte si nepoužité parametry | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f5789b514d645fc670acf9307e4714c160c3b4c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918175"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Zkontrolujte nepoužité parametry
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio naleznete v tématu [CA1801: Projděte si nepoužité parametry](/visualstudio/code-quality/ca1801-review-unused-parameters).

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategorie|Microsoft.Usage|
|Narušující změna|Bez přerušení – Pokud člen není viditelný mimo sestavení, bez ohledu na změnu, kterou provedete.<br /><br /> Bez přerušení – Pokud změníte člena tak, aby používal parametr v rámci jeho těla.<br /><br /> Přerušení – Pokud odeberete parametr a je viditelný mimo sestavení.|

## <a name="cause"></a>příčina
 Podpis metody obsahuje parametr, který není použit v těle metody. Toto pravidlo neověřuje následující metody:

- Metody, na které se odkazuje delegát.

- Metody používané jako obslužné rutiny událostí.

- Metody deklarované s modifikátorem `abstract` (`MustOverride` ve Visual Basic)

- Metody deklarované s modifikátorem `virtual` (`Overridable` ve Visual Basic)

- Metody deklarované s modifikátorem `override` (`Overrides` ve Visual Basic)

- Metody deklarované s modifikátorem `extern` (`Declare` příkaz v Visual Basic)

## <a name="rule-description"></a>Popis pravidla
 Zkontrolujte parametry v nevirtuálních metodách, které se nepoužívají v těle metody, abyste se ujistili, že při přístupu k nim neexistují žádné správné potíže. Nepoužité parametry účtují náklady na údržbu a výkon.

 V některých případech může porušení tohoto pravidla ukazovat na chybu implementace v metodě. Například parametr by měl být použit v těle metody. Potlačí upozornění tohoto pravidla, pokud parametr neexistuje kvůli zpětné kompatibilitě.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte nepoužitý parametr (nezměněná změna) nebo použijte parametr v těle metody (nepevná změna).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění pro dříve dodaný kód, pro který by došlo k zásadní změně této opravy.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dvě metody. Jedna metoda narušuje pravidlo a druhá metoda bude toto pravidlo splňovat.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1811: Vyhněte se nevolanému místnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Vyhněte se nevytvořeným instancím vnitřních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Odeberte nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md)
