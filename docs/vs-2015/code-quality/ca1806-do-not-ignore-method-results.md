---
title: 'CA1806: Neignorujte výsledky metody | Dokumentace Microsoftu'
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
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9e6b7bdd99500f0be29c8101ef9993b565914300
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830584"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Neignorujte výsledky metody
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>Příklad  
 Následující příklad opravuje předchozí porušení přiřazením výsledek String.Trim zpět do proměnné, které byla volána pro.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metodu, která nepoužívá objekt, který vytvoří.  
  
> [!NOTE]
>  Toto porušení nelze reprodukovat v jazyce Visual Basic.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad opravuje předchozí porušení odebráním nepotřebných vytvoření objektu.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metodu, která metoda nativní funkce GetShortPathName vrátí kód chyby: ignoruje.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad opravuje předchozí porušení chybový kód a došlo k výjimce při volání selže.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]