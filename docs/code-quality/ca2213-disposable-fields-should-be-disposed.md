---
title: 'CA2213: Uvolnitelná pole by měla být uvolněna'
ms.date: 05/14/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1838d7e57b841c932d95006d1ff33972dd7a1a1f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231613"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Uvolnitelná pole by měla být uvolněna

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ, který implementuje <xref:System.IDisposable?displayProperty=fullName> deklaraci polí typů, které také implementují <xref:System.IDisposable>. Metoda pole není volána <xref:System.IDisposable.Dispose%2A> metodou deklarovaného typu. <xref:System.IDisposable.Dispose%2A>

## <a name="rule-description"></a>Popis pravidla

Typ zodpovídá za likvidaci všech spravovaných prostředků. CA2213 pravidla kontroluje, zda typ na <xref:System.IDisposable>jedno, který implementuje `T` , deklaruje pole `F` , které je instancí typu `FT`na jedno použití. Pro každé pole `F` , které je přiřazeno místně vytvořený objekt v rámci metod nebo inicializátorů nadřazeného typu `T`, se pravidlo pokusí vyhledat volání `FT.Dispose`. Pravidlo vyhledá metody volané `T.Dispose` a jednu nižší úroveň (tj. metody volané metodami, které `T.Dispose`volá).

> [!NOTE]
> Kromě [zvláštních případů](#special-cases)se pravidlo CA2213 aktivuje jenom pro pole, která jsou přiřazená místně vytvořenému objektu v rámci metod a inicializátorů obsahujícího typ. Pokud je objekt vytvořen nebo přiřazen mimo typ `T`, pravidlo se neaktivuje. To snižuje šum pro případy, kdy nadřazený typ nevlastní odpovědnost za likvidaci objektu.

### <a name="special-cases"></a>Zvláštní případy

Pravidlo CA2213 může také aktivovat pole následujících typů i v případě, že objekt, který je přiřazen, není vytvořen místně:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Předání objektu jednoho z těchto typů konstruktoru a jeho přiřazení k poli indikuje *přenos vlastnictví* do nově vytvořeného typu. To znamená, že nově konstruovaný typ je nyní zodpovědný za likvidaci objektu. Pokud objekt není vyřazen, dojde k porušení CA2213.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, zavolejte <xref:System.IDisposable.Dispose%2A> na pole, která jsou typu implementující <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Upozornění z tohoto pravidla je bezpečné potlačit, pokud:

- Typ označený příznakem neodpovídá za uvolnění prostředku uloženého v poli (to znamená, že typ nemá *vlastnictví Dispose*).
- Volání, ke <xref:System.IDisposable.Dispose%2A> kterému dochází na hlubší úrovni volání než kontroly pravidel

## <a name="example"></a>Příklad

Následující fragment kódu ukazuje typ `TypeA` , který implementuje. <xref:System.IDisposable>

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Následující fragment kódu ukazuje `TypeB` typ, který porušuje pravidlo CA2213 deklarací pole `aFieldOfADisposableType` jako typ na jedno použití (`TypeA`) a nevolá <xref:System.IDisposable.Dispose%2A> ho do pole.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

Chcete-li opravit porušení, `Dispose()` zavolejte na pole na jedno použití:

```csharp
protected virtual void Dispose(bool disposing)
{
   if (!disposed)
   {
      // Dispose of resources held by this instance.
      aFieldOfADisposableType.Dispose();

      disposed = true;

      // Suppress finalization of this disposed instance.
      if (disposing)
      {
          GC.SuppressFinalize(this);
      }
   }
}
```

## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable?displayProperty=fullName>
- [Vzor Dispose](/dotnet/standard/design-guidelines/dispose-pattern)