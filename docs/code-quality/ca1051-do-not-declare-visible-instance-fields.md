---
title: 'CA1051: Nedeklarujte viditelná pole instance'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 296e8cb4753d487573957de1108a8cb27778ef4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235794"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Nedeklarujte viditelná pole instance

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Typ má neprivátní pole instance.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Hlavní použití pole by mělo být jako podrobnost implementace. Pole by měla `private` být `internal` nebo a měla by být vystavena pomocí vlastností. Je snadné získat přístup k vlastnosti, protože je přístup k poli a kód v přístupových objektech vlastnosti se může změnit, protože funkce typu se rozšiřují bez úvodních změn.

Vlastnosti, které vracejí jenom hodnotu privátního nebo interního pole, jsou optimalizované tak, aby se prováděly v hodnotě s přístupem k poli. zvýšení výkonu pro použití externě viditelných polí místo vlastností je minimální. *Externě viditelné* `public`jsou úrovně dostupnosti `protected`, a `protected internal` (`Public`, `Protected` avVisualBasic).`Protected Friend`

Veřejné pole navíc nelze chránit pomocí [požadavků propojení](/dotnet/framework/misc/link-demands). Další informace najdete v tématu [CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md). (Požadavky na propojení se nevztahují na aplikace .NET Core.)

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, vytvořte pole `private` nebo `internal` ho zpřístupněte pomocí externě viditelné vlastnosti.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Toto upozornění potlačí jenom v případě, že jste si jisti, že spotřebitelé potřebují k poli přímý přístup. U většiny aplikací nevystavená pole neposkytují výhody výkonu ani udržovatelnosti prostřednictvím vlastností.

Příjemci můžou potřebovat přístup k polím v následujících situacích:

- v ovládacích prvcích obsahu webových formulářů ASP.NET
- Když cílová platforma používá `ref` pro úpravu polí, jako jsou například model-View-ViewModel (MVVM) architektury pro WPF a UWP

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje typ (`BadPublicInstanceFields`), který porušuje toto pravidlo. `GoodPublicInstanceFields`zobrazuje opravený kód.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Související pravidla

- [CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Viz také:

- [Požadavky propojení](/dotnet/framework/misc/link-demands)
