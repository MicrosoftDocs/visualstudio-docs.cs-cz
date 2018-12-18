---
title: 'CA2112: Zabezpečené typy by neměly vystavovat pole'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 538c7ac89643c168086d6bdcb514d88295e482dc
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548322"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Zabezpečené typy by neměly vystavovat pole

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ obsahuje veřejná pole a je zabezpečen pomocí [požadavky propojení](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Popis pravidla
 Pokud má kód přístup k instanci typu, která je zabezpečena pomocí požadavku na propojení, nemusí kód vyhovět požadavku na propojení pro přístup k polím tohoto typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zkontrolujte neveřejné pole a přidejte veřejné vlastnosti nebo metody, které vracejí data pole. Kontroly zabezpečení LinkDemand na typech chránit přístup k vlastnostem a metodám typu. Zabezpečení přístupu kódu však nelze použít na pole.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pro problémy se zabezpečením i pro dobrý návrh by měla vyřešit porušení tím, že nonpublic veřejná pole. Upozornění tohoto pravidla můžete potlačit, pokud toto pole neobsahuje informace, které by měla zůstat zabezpečená a není závislý na obsah tohoto pole.

## <a name="example"></a>Příklad
 Následující příklad se skládá z knihovny typů (`SecuredTypeWithFields`) s nezabezpečené pole, typ (`Distributor`), který lze vytvořit instance typu knihovny a předá chybné instance na typy nemáte příslušná oprávnění k jejich vytvoření a aplikace kód, který pole instance můžete přečíst, i když nemá oprávnění, který zabezpečuje typu.

 Následující kód knihovny porušuje pravidlo.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example-1"></a>Příklad 1
 Aplikaci nelze vytvořit instanci z důvodu požadavku propojení, která chrání zabezpečeného typu. Následující třída umožňuje aplikaci získat instanci typu zabezpečené.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example-2"></a>Příklad 2
 Následující aplikace ukazuje, jak, bez oprávnění pro přístup k zabezpečené typ metody kód může přistupovat k jeho polí.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

Tento příklad vytvoří následující výstup:

```txt
Creating an instance of SecuredTypeWithFields.
Secured type fields: 22, 33
Changing secured type's field...
Cached Object fields: 99, 33
```

## <a name="related-rules"></a>Související pravidla

- [CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Viz také:

- [Požadavky propojení](/dotnet/framework/misc/link-demands)
- [Data a modelování](/dotnet/framework/data/index)