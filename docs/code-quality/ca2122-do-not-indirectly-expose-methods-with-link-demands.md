---
title: 'CA2122: Nezveřejňujte nepřímo metody s požadavky propojení'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d17c2981e4dabe82817aeedcf4fcab93e970b47
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548871"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Nezveřejňujte nepřímo metody s požadavky propojení

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný člen má [požadavky propojení](/dotnet/framework/misc/link-demands) a je volán členem, který neprovádí žádné bezpečnostní kontroly.

## <a name="rule-description"></a>Popis pravidla
 Požadavek propojení kontroluje pouze oprávnění bezprostředního volajícího. Pokud člen `X` provádí žádné požadavky na zabezpečení svých volající a kód chráněn pomocí požadavku propojení, volající bez nezbytná oprávnění můžete použít volání `X` přístup chráněný člen.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Přidat bezpečnostní [Data a modelování](/dotnet/framework/data/index) nebo vyžádání propojit člen tak, aby už neposkytuje nezabezpečený přístup na vyžádání chráněné člena odkazu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete bezpečně potlačit upozornění tohoto pravidla, ujistěte se, že váš kód bez možnosti udělovat volajících přístup pro operace nebo prostředky použité destruktivním způsobem.

## <a name="example-1"></a>Příklad 1
 Následující příklady ukazují knihovnu, která porušuje pravidlo a aplikace, která ukazuje slabé stránky knihovny. Ukázky knihovny poskytuje dvě metody, které společně pravidlo porušují. `EnvironmentSetting` Metoda je zabezpečena pomocí požadavku propojení pro neomezený přístup k proměnným prostředí. `DomainInformation` Metoda provádí žádné požadavky na zabezpečení volajících před voláním `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Příklad 2
 Následující aplikace volá člen nezabezpečené knihovny.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Tento příklad vytvoří následující výstup:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](/dotnet/standard/security/secure-coding-guidelines)
- [Požadavky propojení](/dotnet/framework/misc/link-demands)
- [Data a modelování](/dotnet/framework/data/index)