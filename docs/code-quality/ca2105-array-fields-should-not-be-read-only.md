---
title: 'CA2105: Pole polí by neměly být pouze pro čtení'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a033c23a323a94dcbda0a98f9ec57de529d3c308
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883287"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Pole polí by neměly být pouze pro čtení

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Veřejné nebo chráněné pole obsahující pole je deklarován jen pro čtení.

## <a name="rule-description"></a>Popis pravidla

Pokud použijete `readonly` (`ReadOnly` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) modifikátor pro pole, které obsahuje pole, pole nelze změnit pro odkazování na jiné pole. Avšak prvky pole, které jsou uloženy v poli určeném jen pro čtení, mohou být změněny. Kód, který se rozhoduje nebo provádí operace, které jsou založeny na elementy pole jen pro čtení, který je veřejně přístupný může obsahovat chybu zneužitelné zabezpečení.

Všimněte si, že s polem veřejné také porušuje pravidla návrhu [CA1051: nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li vyřešit ohrožení zabezpečení, který je identifikován podle tohoto pravidla, nespoléhejte na obsah, který je veřejně přístupný pole jen pro čtení. Důrazně doporučujeme používat jednu z následujících postupů:

- Nahraďte pole kolekcí siného typu, který se nedá změnit. Další informace naleznete v tématu <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Nahraďte veřejné pole, která vrací klon soukromého pole. Protože váš kód nespoléhala se na klonu, nehrozí nebezpečí, pokud dojde k úpravě prvky.

Pokud jste zvolili druhého přístupu, nenahrazují pole k vlastnosti; vlastnosti, které vrací pole nepříznivě ovlivnit výkon. Další informace najdete v tématu [CA1819: vlastnosti by neměly vracet pole](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Vyloučení upozornění tohoto pravidla se důrazně nedoporučuje. Téměř žádné scénáře dojít, pokud nejsou důležité obsah pole jen pro čtení. Pokud je tomu u vašeho scénáře, odeberte `readonly` modifikátor místo vyloučení zprávy.

## <a name="example-1"></a>Příklad 1

Tento příklad ukazuje nebezpečí porušení tohoto pravidla. První část ukazuje příklad knihovny, která má typ, `MyClassWithReadOnlyArrayField`, který obsahuje dvě pole (`grades` a `privateGrades`), které nejsou zabezpečené. Pole `grades` je veřejná a proto citlivé na jakýkoli volající. Pole `privateGrades` privátní, ale je stále vztahují rizika vyplývající, protože se vrátí volajícímu podle `GetPrivateGrades` metody. `securePrivateGrades` Pole je přístupný bezpečným způsobem podle `GetSecurePrivateGrades` metody. Je deklarována jako soukromá dodržovat postupy dobrý návrh. Druhá část zobrazuje kód, který změní hodnoty uložené v `grades` a `privateGrades` členy.

Příklad knihovny tříd se zobrazí v následujícím příkladu.

[!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example-2"></a>Příklad 2

Následující kód používá příklad knihovny tříd pro ilustraci problémy se zabezpečením pole jen pro čtení.

[!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

Výstup z tohoto příkladu je:

```text
Before tampering: Grades: 90, 90, 90 Private Grades: 90, 90, 90  Secure Grades, 90, 90, 90
After tampering: Grades: 90, 555, 90 Private Grades: 90, 555, 90  Secure Grades, 90, 90, 90
```

## <a name="see-also"></a>Viz také:

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>