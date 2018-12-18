---
title: 'CA1019: Definujte přístupové objekty pro argumenty atributu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2e095c862edc5d7b68e1a6c55ada90a425b7e64f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550450"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Definujte přístupové objekty pro argumenty atributu

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 V konstruktoru definuje atribut argumenty, které nemají odpovídající vlastnosti.

## <a name="rule-description"></a>Popis pravidla
 Atributy mohou definovat povinné argumenty, které musí být specifikovány při použití atributu na cíl. Říká se jim také poziční argumenty, jelikož jsou konstruktorům atributů předány jako poziční parametry. Pro každý povinný argument by měl atribut navíc poskytovat odpovídající vlastnost jen pro čtení, aby mohla být hodnota argumentu během spuštění získána. Toto pravidlo zkontroluje, pro každý parametr konstruktoru definovanou odpovídající vlastnost.

 Atributy mohou také definovat volitelné argumenty, které jsou rovněž známy jako pojmenované argumenty. Tyto argumenty jsou podle názvu poskytovány konstruktorům atributů a měly by mít odpovídající vlastnost pro čtení i zápis.

 Povinné a nepovinné argumenty, odpovídající vlastnosti a parametry konstruktoru musí použít stejný název, ale jinou velikostí písmen. Vlastnosti využívají Pascal velká a malá písmena a parametry ve formátu camelCase použití malých a velkých písmen.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte vlastnost jen pro čtení pro každý parametr konstruktoru, který nemá.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla, pokud nechcete, aby hodnota retrievable povinný argument.

## <a name="custom-attributes-example"></a>Příklad vlastní atributy

Následující příklad ukazuje dva atributy, které definují povinný parametr (poziční). První implementaci atributu je nesprávně definovaný. Druhý implementace je správná.

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>Poziční a pojmenované argumenty

Pojmenované a poziční argumenty nastavte ji vymazat spotřebitelé knihovny které argumenty jsou povinné pro atribut a které argumenty jsou volitelné.

Následující příklad ukazuje implementaci atributu, který má pojmenované i poziční argumenty:

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

Následující příklad ukazuje, jak použít vlastní atribut na dvě vlastnosti:

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>Související pravidla
 [CA1813: Vyhněte se nezapečetěným atributům](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Viz také:
 [Atributy](/dotnet/standard/design-guidelines/attributes)