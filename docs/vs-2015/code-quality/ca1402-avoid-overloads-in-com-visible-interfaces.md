---
title: 'CA1402: Vyhněte se přetížení ve viditelných rozhraních modelu COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 258b7ba1444cd990c3ec68ebfd5faccc945439e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661353"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Vyhněte se přetížení ve viditelných rozhraních modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Rozhraní, které je viditelné rozhraní modelu COM (Component Object Model), deklaruje přetížené metody.

## <a name="rule-description"></a>Popis pravidla
 Když jsou přetížené metody vystaveny klientům modulu COM, zachová svůj název pouze první přetížení metody. Následná přetížení jsou jednoznačně přejmenována přidáním znaku podtržítka ' _ ' a celé číslo, které odpovídá pořadí deklarace přetížení. Zvažte například následující metody.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Tyto metody jsou zveřejněny pro klienty modelu COM, jak je uvedeno níže.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Klienti modelu COM Visual Basic 6 nemohou implementovat metody rozhraní pomocí podtržítka v názvu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přejmenujte přetížené metody tak, aby názvy byly jedinečné. Alternativně můžete nastavit rozhraní jako neviditelné na modelu COM změnou přístupnosti na `internal` (`Friend` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) nebo použitím atributu <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> nastaveného na `false`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje rozhraní, které porušuje pravidlo a rozhraní, které splňuje pravidlo.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1413: Vyhněte se neveřejným polím v hodnotách viditelných modulem COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Označte sestavení pomocí atributu ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Viz také
 Spolupráce s [datovým typem Long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) [nespravovaného kódu](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
