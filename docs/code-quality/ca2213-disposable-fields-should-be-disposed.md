---
title: 'CA2213: Uvolnitelné pole by mělo být uvolněno'
ms.date: 11/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be06c9bf38ec360cedc858d92a84b1f89c662856
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220629"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Uvolnitelné pole by mělo být uvolněno

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Typ, který implementuje <xref:System.IDisposable?displayProperty=fullName> deklaruje pole, která jsou typy, které také implementují <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Není volána metoda pole <xref:System.IDisposable.Dispose%2A> metoda deklarujícího typu.

## <a name="rule-description"></a>Popis pravidla

Typ je zodpovědná za uvolnění všech nespravovaných prostředků. Pravidlo CA2213 kontroluje, zda uvolnitelného typu (to znamená, jednu, která implementuje <xref:System.IDisposable>) `T` deklaruje pole `F` z uvolnitelného typu, který je instance `FT`. Pro každé pole `F` , které se má přiřadit místně vytvořený objekt v rámci metody nebo inicializátory nadřazeného typu `T`, pravidlo se pokusí najít volání `FT.Dispose`. Toto pravidlo vyhledá metody volané `T.Dispose` a jednu úroveň níže (to znamená, volání metody volané metody `FT.Dispose`).

> [!NOTE]
> CA2213 pravidlo je vyvoláno pouze pro pole, které jsou přiřazeny místně vytvořené uvolnitelný objekt v rámci nadřazeného typu metody a inicializátory. Pokud je objekt vytvořen nebo přiřazené mimo typ `T`, pravidlo se neaktivuje. To snižuje šumu pro případy, kdy nadřazeného typu nevlastní odpovědnost za uvolnění objektu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, zavolejte <xref:System.IDisposable.Dispose%2A> pro pole, která jsou typy, které implementují <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění tohoto pravidla, pokud ještě nejste zodpovědná pro uvolnění prostředku drží pole, nebo pokud můžete bezpečně volání <xref:System.IDisposable.Dispose%2A> dochází na hlubší úrovni volání než pravidla kontroly.

## <a name="example"></a>Příklad

Následující fragment kódu ukazuje typ `TypeA` , který implementuje <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Následující fragment kódu ukazuje typ `TypeB` , který porušuje pravidla CA2213 deklarováním pole `aFieldOfADisposableType` jako uvolnitelného typu (`TypeA`) a není volání <xref:System.IDisposable.Dispose%2A> na pole.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable?displayProperty=fullName>
- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)