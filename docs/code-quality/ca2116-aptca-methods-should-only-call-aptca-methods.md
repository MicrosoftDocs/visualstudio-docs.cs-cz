---
title: 'CA2116: Metody APTCA by měly volat pouze metody APTCA'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7decf94644bdb055f38c267c945dc0dcc813550a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547916"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Metody APTCA by měly volat pouze metody APTCA

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Metodu v sestavení <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atribut volá metodu v sestavení, který nemá atribut.

## <a name="rule-description"></a>Popis pravidla

Ve výchozím nastavení, veřejné nebo chráněné metody v podepisují sestavení silnými názvy jsou implicitně chráněné [požadavky propojení](/dotnet/framework/misc/link-demands) pro úplný vztah důvěryhodnosti; pouze plně důvěryhodní volající může přistupovat k sestavení se silným názvem. Sestavení se silným názvem označené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA) nemají tuto ochranu. Atribut zakáže požadavku propojení, zpřístupnění sestavení volajícím, které nemají úplný vztah důvěryhodnosti, jako je například kód provádění z intranetu nebo Internetu.

Když je atribut APTCA uveden pro plně důvěryhodná sestavení a sestavení spustí kód v jiném sestavení, který neumožňuje volání částečně důvěryhodným volajícím, je možné zneužití zabezpečení. Pokud dvě metody `M1` a `M2` splňovat následující podmínky, škodlivý volající použít metodu `M1` obejít požadavek propojení implicitní úplný vztah důvěryhodnosti, který chrání `M2`:

- `M1` je v plně důvěryhodná sestavení, který má atribut APTCA deklarována veřejnou metodu.

- `M1` volá metodu `M2` mimo `M1`pro sestavení.

- `M2`od sestavení nemá atribut APTCA a proto by neměl být spouštěn podle nebo jejich jménem volajícím, které jsou částečně důvěryhodné.

Částečně důvěryhodné volající `X` lze zavolat metodu `M1`, způsobující `M1` volat `M2`. Protože `M2` nemá atribut APTCA, jeho bezprostředního volajícího (`M1`) musí uspokojit požadavky propojení pro úplnou důvěryhodnost; `M1` má úplný vztah důvěryhodnosti a proto splňuje tato kontrola. Je bezpečnostní riziko, protože `X` není součástí uspokojit poptávku odkaz, který chrání `M2` z nedůvěryhodných volajících. Metody s atributem APTCA proto nesmějí volat metody, které nemají atribut.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud je vyžadován atribut APTCA, použijte k ochraně metodu, která volá do sestavení úplné důvěryhodnosti vyžádání. Vyžádání vás bude záviset na konkrétní oprávnění funkce vystavené metodu. Pokud je to možné, Chraňte metody s požadavky pro úplný vztah důvěryhodnosti k zajištění toho, že základní funkce není vystaven částečně důvěryhodné volající. Pokud to není možné, vyberte sadu oprávnění, která efektivně chrání vystavené funkce.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete bezpečně potlačit upozornění tohoto pravidla, ujistěte se, že funkce vystavené metodu přímo nebo nepřímo nepovoluje volající pro přístup k citlivé informace, operace nebo prostředky použité destruktivním způsobem.

## <a name="example-1"></a>Příklad 1
 Následující příklad používá dva sestavení a testovací aplikaci pro ilustraci ohrožení zabezpečení, zjistí toto pravidlo. První sestavení nemá atribut APTCA a by neměl být přístupný pro částečně důvěryhodných volajících (představované `M2` v předchozím diskusí).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Příklad 2
 Druhý sestavení je plně důvěryhodný a povoluje částečně důvěryhodné volající (představované `M1` v předchozím diskusí).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Příklad 3
 Testovací aplikace (představované `X` v předchozím diskusí) je částečně důvěryhodné.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Tento příklad vytvoří následující výstup:

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Související pravidla

- [CA2117: Typy APTCA by měly rozšířit pouze základní typy APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](/dotnet/standard/security/secure-coding-guidelines)
- [Používání knihoven z částečně důvěryhodného kódu](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Požadavky propojení](/dotnet/framework/misc/link-demands)
- [Data a modelování](/dotnet/framework/data/index)