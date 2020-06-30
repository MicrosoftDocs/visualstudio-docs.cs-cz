---
title: 'CA2117: typy APTCA by měly rozšířily pouze základní typy APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 90c1f66f36fc689ee077ec66f154487d65ee13a1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543608"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Typy APTCA by měl rozšiřovat pouze základní typy APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejný nebo chráněný typ v sestavení s <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributem dědí z typu deklarovaného v sestavení, které nemá atribut.

## <a name="rule-description"></a>Popis pravidla
 Ve výchozím nastavení jsou veřejné nebo chráněné typy v sestaveních se silnými názvy implicitně chráněny [požadavky dědičnosti](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) pro úplný vztah důvěryhodnosti. Sestavení se silným názvem označená <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributem (APTCA) nemají tuto ochranu. Atribut zakáže požadavek dědičnosti. Díky tomu jsou vystavené typy deklarované v sestavení dědičné typy, které nemají úplný vztah důvěryhodnosti.

 Pokud je atribut APTCA přítomen v plně důvěryhodném sestavení a typ v sestavení dědí z typu, který nepovoluje částečně důvěryhodné volající, je možné zajistit zneužití zabezpečení. Pokud existují dva typy `T1` a `T2` splňují následující podmínky, škodlivé volající mohou použít typ `T1` pro obejít požadavek dědičnosti implicitní plné důvěryhodnosti, který chrání `T2` :

- `T1`je veřejný typ deklarovaný v plně důvěryhodném sestavení, které má atribut APTCA.

- `T1`dědí z typu `T2` mimo jeho sestavení.

- `T2`sestavení nemá atribut APTCA a proto by nemělo být děděno typy v částečně důvěryhodných sestaveních.

  Částečně důvěryhodný typ `X` může dědit z `T1` , což dává přístup k zděděným členům deklarovaným v `T2` . Vzhledem k tomu, že nemá `T2` atribut APTCA, musí jeho bezprostřední odvozený typ ( `T1` ) splňovat požadavky dědičnosti pro úplný vztah důvěryhodnosti; `T1` má úplný vztah důvěryhodnosti, a proto splňuje tuto kontrolu. Bezpečnostní riziko je způsobeno tím, že se `X` nepodílí na splnění požadavku dědičnosti, který chrání `T2` před nedůvěryhodným podtřídou. Z tohoto důvodu typy s atributem APTCA nesmí rozkrývat typy, které nemají atribut.

  Jiné potíže se zabezpečením a možná i běžnější, je, že odvozený typ ( `T1` ) může prostřednictvím chyby programátora zveřejnit chráněné členy z typu, který vyžaduje úplný vztah důvěryhodnosti ( `T2` ). Pokud k tomu dojde, nedůvěryhodní volající získají přístup k informacím, které by měly být k dispozici pouze pro plně důvěryhodné typy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud typ hlášených porušením je v sestavení, které nevyžaduje atribut APTCA, odeberte jej.

 Pokud je požadován atribut APTCA, přidejte do typu požadavek dědičnosti pro úplný vztah důvěryhodnosti. To chrání proti dědění nedůvěryhodným typům.

 Je možné opravit porušení přidáním atributu APTCA do sestavení základních typů hlášených porušením. Neprovádějte to bez toho, aby nejprve provedla intenzivní kontrolu zabezpečení všech kódů v sestaveních a veškerý kód, který závisí na sestaveních.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Chcete-li bezpečně potlačit upozornění od tohoto pravidla, je nutné zajistit, aby chránění členové vystavené vaším typem nepřímo ani nepřímo nepovolovali nedůvěryhodným volajícím přístup k citlivým informacím, operacím nebo prostředkům, které lze použít destruktivním způsobem.

## <a name="example"></a>Příklad
 Následující příklad používá dvě sestavení a testovací aplikaci k ilustraci chyby zabezpečení zjištěné tímto pravidlem. První sestavení nemá atribut APTCA a neměl by být dědičný pomocí částečně důvěryhodných typů (reprezentovaných `T2` v předchozí diskuzi).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Příklad
 Druhé sestavení reprezentované `T1` v předchozí diskuzi je plně důvěryhodné a povoluje částečně důvěryhodné volající.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Příklad
 Typ testu reprezentovaný `X` v předchozí diskuzi je v částečně důvěryhodném sestavení.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Vyhovět na Shady glen 2/22/2003 12:00:00.** 
 **Z testu: Slunečné louky** 
 **Vyhovět na slunečné louky 2/22/2003 12:00:00.**
## <a name="related-rules"></a>Související pravidla
 [CA2116: Metody APTCA by měly volat pouze metody APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Viz také
 [Pokyny pro zabezpečené kódování](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework sestavení, která mohou být v částečně důvěryhodném kódu volat](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [pomocí knihoven z částečně důvěryhodných](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [požadavků dědičnosti](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) kódu
