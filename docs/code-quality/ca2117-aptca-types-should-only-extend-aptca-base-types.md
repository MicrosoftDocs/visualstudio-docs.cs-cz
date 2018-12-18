---
title: 'CA2117: Typy APTCA by měl rozšířit pouze základní typy APTCA'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dac5acc0b7c7fff02862853bfd996362f80d1cc
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547497"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Typy APTCA by měl rozšířit pouze základní typy APTCA

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Veřejný nebo chráněný typ v sestavení <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atribut je odvozen z typu deklarované v sestavení, který nemá atribut.

## <a name="rule-description"></a>Popis pravidla

Ve výchozím nastavení, veřejné nebo chráněné typy v sestavení se silnými názvy jsou implicitně chráněné [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) pro úplný vztah důvěryhodnosti. Sestavení se silným názvem označené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA) nemají tuto ochranu. Atribut zakáže vyžádané dědičnosti. Odvoditelný typy, které nemají úplný vztah důvěryhodnosti jsou vystavené typy deklarované v sestavení bez vyžádané dědičnosti.

Když je atribut APTCA uveden pro plně důvěryhodná sestavení a typ v sestavení je odvozen z typu, který neumožňuje volání částečně důvěryhodným volajícím, je možné zneužití zabezpečení. Pokud dva typy `T1` a `T2` splňovat následující podmínky, škodlivý volající použít typ `T1` obejít požadavek dědičnosti implicitní úplný vztah důvěryhodnosti, který chrání `T2`:

- `T1` je veřejný typ deklarovaný v plně důvěryhodná sestavení, který má atribut APTCA.

- `T1` je odvozen z typu `T2` mimo sestavení.

- `T2`od sestavení nemá atribut APTCA a proto by neměl být odvoditelný typy v částečně důvěryhodné sestavení.

Částečně důvěryhodný typ `X` může dědit z `T1`, které jí přístup na zděděné členy deklarované v `T2`. Protože `T2` nemá atribut APTCA, její okamžitý odvozeného typu (`T1`) musí splňovat vyžádané dědičnosti pro úplný vztah důvěryhodnosti; `T1` má úplný vztah důvěryhodnosti a proto splňuje tato kontrola. Je bezpečnostní riziko, protože `X` není součástí nesplňujete vyžádané dědičnosti, který chrání `T2` z nedůvěryhodné vytváření podtříd. Z tohoto důvodu nesmí typy s atributem APTCA rozšiřují typy, které nemají atribut.

Jiné potíže se zabezpečením a možná častější ten, který je odvozený typ (`T1`) můžou prostřednictvím chyba programátora, zveřejnit chráněných členů z typu, který vyžaduje úplný vztah důvěryhodnosti (`T2`). Dojde-li se tato ohrožení, nedůvěryhodných volajících získat přístup k informacím, které by měly být k dispozici pouze pro typy plně důvěryhodné.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Pokud je typ hlášených porušení zásad v sestavení, která nevyžaduje atribut APTCA, odeberte ji.

Pokud je vyžadován atribut APTCA, přidejte na typ vyžádané dědičnosti pro úplný vztah důvěryhodnosti. Vyžádané dědičnosti chrání proti dědičnosti nedůvěryhodné typy.

Je možné opravit porušení tak, že přidáte atribut APTCA k sestavení základní typy hlášených porušení zásady. Neprovádějte tuto akci bez první provedení revize náročné na zabezpečení veškerého kódu v sestaveních a veškerý kód, který závisí na sestavení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Můžete bezpečně potlačit upozornění tohoto pravidla, ujistěte se, že chráněné členy zveřejněné podle typu přímo nebo nepřímo neumožňují nedůvěryhodných volajících pro přístup k citlivé informace, operace nebo prostředky použité destruktivním způsobem.

## <a name="example"></a>Příklad

Následující příklad používá dva sestavení a testovací aplikaci pro ilustraci ohrožení zabezpečení, zjistí toto pravidlo. První sestavení nemá atribut APTCA a neměla by být odvoditelný částečně důvěryhodné typy (představované `T2` v předchozím diskusí).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

Druhý sestavení reprezentována `T1` v předchozím diskusí je plně důvěryhodný a povoluje částečně důvěryhodné volající.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

Typ testu, reprezentovaný `X` v předchozím diskusí je v částečně důvěryhodné sestavení.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Tento příklad vytvoří následující výstup:

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>Související pravidla

[CA2116: Metody APTCA by měly volat pouze metody APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](/dotnet/standard/security/secure-coding-guidelines)
- [Používání knihoven z částečně důvěryhodného kódu](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
