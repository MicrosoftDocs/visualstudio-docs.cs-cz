---
title: 'CA1019: Definujte přístupové objekty pro argumenty atributu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ec9be9dae502ec48570a85576f483518ed0d75d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534950"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Definujte přístupové objekty pro argumenty atributů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 V konstruktoru definuje atribut argumenty, které nemají odpovídající vlastnosti.

## <a name="rule-description"></a>Popis pravidla
 Atributy mohou definovat povinné argumenty, které musí být specifikovány při použití atributu na cíl. Říká se jim také poziční argumenty, jelikož jsou konstruktorům atributů předány jako poziční parametry. Pro každý povinný argument by měl atribut navíc poskytovat odpovídající vlastnost jen pro čtení, aby mohla být hodnota argumentu během spuštění získána. Toto pravidlo kontroluje, zda pro každý parametr konstruktoru jste definovali odpovídající vlastnost.

 Atributy mohou také definovat volitelné argumenty, které jsou rovněž známy jako pojmenované argumenty. Tyto argumenty jsou podle názvu poskytovány konstruktorům atributů a měly by mít odpovídající vlastnost pro čtení i zápis.

 U povinných a volitelných argumentů by odpovídající vlastnosti a parametry konstruktoru měly používat stejný název, ale různé velikosti písmen. Vlastnosti používají velká a malá písmena Pascal a parametry používají ve stylu CamelCase velká a malá písmena.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte vlastnost jen pro čtení pro každý parametr konstruktoru, který ho nemá.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud nechcete, aby se hodnota povinného argumentu dala získat, potlačíte upozornění od tohoto pravidla.

## <a name="custom-attributes-example"></a>Příklad vlastních atributů

### <a name="description"></a>Popis
 Následující příklad ukazuje dva atributy, které definují povinný (poziční) parametr. První implementace atributu je nesprávně definovaná. Druhá implementace je správná.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Poziční a pojmenované argumenty

### <a name="description"></a>Popis
 Poziční a pojmenované argumenty umožňují jasným uživatelům vaší knihovny, které argumenty jsou povinné pro atribut a které argumenty jsou volitelné.

 Následující příklad ukazuje implementaci atributu, který má oba poziční i pojmenované argumenty.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Komentáře
 Následující příklad ukazuje, jak použít vlastní atribut na dvě vlastnosti.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1813: Vyhněte se nezapečetěným atributům](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Viz také
 [Atributy](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
