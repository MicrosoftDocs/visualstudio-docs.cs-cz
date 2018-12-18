---
title: 'CA2112: Zabezpečené typy by neměly vystavovat pole | Dokumentace Microsoftu'
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
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a09093d05758d58828b9d7ca73223243252cb23c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871456"
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
 Veřejný nebo chráněný typ obsahuje veřejná pole a je zabezpečen pomocí [požadavky propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Popis pravidla
 Pokud má kód přístup k instanci typu, která je zabezpečena pomocí požadavku na propojení, nemusí kód vyhovět požadavku na propojení pro přístup k polím tohoto typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zkontrolujte neveřejné pole a přidejte veřejné vlastnosti nebo metody, které vracejí data pole. Kontroly zabezpečení LinkDemand na typech chránit přístup k vlastnostem a metodám typu. Zabezpečení přístupu kódu však nelze použít na pole.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pro problémy se zabezpečením i pro dobrý návrh by měla vyřešit porušení tím, že nonpublic veřejná pole. Upozornění tohoto pravidla můžete potlačit, pokud toto pole neobsahuje informace, které by měla zůstat zabezpečená a není závislý na obsah tohoto pole.

## <a name="example"></a>Příklad
 Následující příklad se skládá z knihovny typů (`SecuredTypeWithFields`) s nezabezpečené pole, typ (`Distributor`), který lze vytvořit instance typu knihovny a předá chybné instance na typy nemáte příslušná oprávnění k jejich vytvoření a aplikace kód, který pole instance můžete přečíst, i když nemá oprávnění, který zabezpečuje typu.

 Následující kód knihovny porušuje pravidlo.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Příklad
 Aplikaci nelze vytvořit instanci z důvodu požadavku propojení, která chrání zabezpečeného typu. Následující třída umožňuje aplikaci získat instanci typu zabezpečené.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace ukazuje, jak, bez oprávnění pro přístup k zabezpečené typ metody kód může přistupovat k jeho polí.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Vytvoření instance SecuredTypeWithFields. ** 
 **Zabezpečené typy polí: 22, 33**
**změna zabezpečeného typu pole... ** 
 **Pole objektů do mezipaměti: 99, 33**
## <a name="related-rules"></a>Související pravidla
 [CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Viz také
 [Požadavky na propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



