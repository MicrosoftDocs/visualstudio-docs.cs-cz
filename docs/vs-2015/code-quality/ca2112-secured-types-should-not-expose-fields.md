---
title: 'CA2112: zabezpečené typy by neměly vystavovat pole | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c91a7c9833d3d9d5ae283c28ae4d437bd07734
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658751"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Zabezpečené typy by neměly vystavovat pole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ obsahuje veřejná pole a je zabezpečený [požadavky propojení](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Popis pravidla
 Pokud má kód přístup k instanci typu, která je zabezpečena pomocí požadavku na propojení, nemusí kód vyhovět požadavku na propojení pro přístup k polím tohoto typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nastavte pole NonPublic a přidejte veřejné vlastnosti nebo metody, které vrátí data pole. Kontroly zabezpečení LinkDemand u typů chrání přístup k vlastnostem a metodám typu. Zabezpečení přístupu kódu však nelze použít u polí.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pro problémy se zabezpečením a dobrým návrhem byste měli opravit porušení tím, že zveřejníte veřejná pole NonPublic. Můžete potlačit upozornění z tohoto pravidla, pokud pole neobsahuje informace, které by měly zůstat zabezpečené, a Nespoléháte se na obsah pole.

## <a name="example"></a>Příklad
 Následující příklad se skládá z typu knihovny (`SecuredTypeWithFields`) s nezabezpečenými poli, typ (`Distributor`), který může vytvořit instance typu knihovny a chybné předávání instancí typů, nemá oprávnění k jejich vytvoření a kód aplikace, který může číst pole instance, i když nemá oprávnění zabezpečující typ.

 Následující kód knihovny je v rozporu s pravidlem.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Příklad
 Aplikace nemůže vytvořit instanci z důvodu požadavku na propojení, který chrání zabezpečený typ. Následující třída umožňuje aplikaci získat instanci zabezpečeného typu.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace ukazuje, jak bez oprávnění k přístupu k metodám zabezpečeného typu, kód má přístup k jeho polím.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Vytváření instance třídy SecuredTypeWithFields.** 
**zabezpečených polí typu: 22, 33** 
**Změna pole zabezpečeného typu...** 
**pole objektů uložených v mezipaměti: 99, 33**
## <a name="related-rules"></a>Související pravidla
 [CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Viz také
 [Propojení vyžaduje](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [data a modelování](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
