---
title: 'CA1801: Revize nepoužitých parametrů | Dokumentace Microsoftu'
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
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b0946e315aef0c333207d49eb14820d287a9b361
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269682"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Revize nepoužitých parametrů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio 2017, najdete v části [CA1801: revize nepoužitých parametrů](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters) na webu docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Kategorie|Microsoft.Usage|  
|Narušující změna|Pevné – Pokud člen není viditelný mimo sestavení, bez ohledu na to, které provedete změnu.<br /><br /> Pevné – Pokud změníte členu, který chcete použít parametr v rámci svého těla.<br /><br /> Rozdělení – odeberte parametr a je viditelný mimo sestavení.|  
  
## <a name="cause"></a>příčina  
 Podpis metody obsahuje parametr, který není použit v těle metody. Toto pravidlo nezkoumá následujících metod:  
  
-   Metody odkazuje delegáta.  
  
-   Metody používané jako obslužné rutiny událostí.  
  
-   Metody deklarované s `abstract` (`MustOverride` v jazyce Visual Basic) modifikátor.  
  
-   Metody deklarované s `virtual` (`Overridable` v jazyce Visual Basic) modifikátor.  
  
-   Metody deklarované s `override` (`Overrides` v jazyce Visual Basic) modifikátor.  
  
-   Metody deklarované s `extern` (`Declare` v sadě Visual Studio) modifikátor.  
  
## <a name="rule-description"></a>Popis pravidla  
 Zkontrolujte parametry v nevirtuálních metodách, které nejsou používány v těle metody, abyste měli jistotu, že nesprávnosti kolem selhání k nim přístup. Nevyužité parametry zvyšují náklady na náklady na údržbu a výkonu.  
  
 Porušení tohoto pravidla může někdy odkazovat na implementační chybě v metodě. Například parametr by měl byly použity v těle metody. Potlačení upozornění tohoto pravidla, pokud parametr existuje z důvodu zpětné kompatibility.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Chcete-li opravit porušení tohoto pravidla, odebrat Nepoužitý parametr (k zásadní změně) nebo pomocí parametru v těle metody (nevýznamných změn).  
  
## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění  
 Je bezpečné potlačit upozornění tohoto pravidla pro dříve dodané kód, pro kterou bude oprava rozbíjející změny.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva způsoby. Jedna metoda porušuje pravidlo a jiná metoda splňuje pravidlo.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]  
  
## <a name="related-rules"></a>Související pravidla  
 [CA1811: Vyhněte se nevolanému místnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Vyhněte se nevytvořeným instancím vnitřních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Odeberte nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md)

