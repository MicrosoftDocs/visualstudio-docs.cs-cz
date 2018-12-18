---
title: 'CA2114: Zabezpečení metody by mělo být nadmnožinou typu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66fe0031380139c55942a1a47f71066a327d5e24
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551424"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Zabezpečení metody by mělo být nadmnožinou typu

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Typ má deklarativní zabezpečení a jeden z jeho metod má deklarativní zabezpečení pro stejnou akci zabezpečení a akce zabezpečení není [požadavky propojení](/dotnet/framework/misc/link-demands), a oprávnění ověřena pomocí typu nejsou podmnožinu oprávnění ověří pomocí metody.

## <a name="rule-description"></a>Popis pravidla
 Metoda by neměla mít v obou úrovni metody nebo typ deklarativní zabezpečení pro stejnou akci. Dva kontroly nejsou sloučeny; je použita pouze vyžádání úrovni metod. Například, pokud typ požaduje oprávnění `X`, a jeden z jeho metod požaduje oprávnění `Y`, kód nemá oprávnění k `X` spustí metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Zrevidujete váš kód, abyste měli jistotu, že obě akce se vyžadují. Pokud obě akce, ujistěte se, že úroveň metody akce obsahuje zabezpečení na úrovni typu. Například, pokud váš typ požaduje oprávnění `X`, a její metoda musí také vyžadují oprávnění `Y`, metoda by měla explicitně vyžadují `X` a `Y`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud metoda nevyžaduje zabezpečení podle typu. To však není běžné scénáře a může znamenat potřebu přezkoumání Pečlivý návrh.

## <a name="example-1"></a>Příklad 1

Následující příklad používá oprávnění prostředí k předvedení nebezpečí porušení tohoto pravidla. V tomto příkladu kódu aplikace vytvoří instanci typu zabezpečené před odepřením oprávnění vyžadovaný typem. Ve scénáři hrozbami reálného světa bude aplikace vyžadovat, aby jiný způsob, jak získat instanci objektu.

V následujícím příkladu knihovna požadavků pro typ oprávnění k zápisu a oprávnění ke čtení pro metodu.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Příklad 2

Následující kód aplikace ukazuje ohrožení zabezpečení knihovny voláním metody i v případě, že nesplňuje požadavek na zabezpečení na úrovni typu.

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

Tento příklad vytvoří následující výstup:

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](/dotnet/standard/security/secure-coding-guidelines)
- [Požadavky propojení](/dotnet/framework/misc/link-demands)
- [Data a modelování](/dotnet/framework/data/index)