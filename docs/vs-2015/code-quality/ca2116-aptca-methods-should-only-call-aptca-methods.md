---
title: 'CA2116: metody APTCA by měly volat pouze metody APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 115c0e733716994ba463eada938f8ff908612d0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547755"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Metody APTCA by měly volat pouze metody APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Metoda v sestavení s <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributem volá metodu v sestavení, které nemá atribut.

## <a name="rule-description"></a>Popis pravidla
 Ve výchozím nastavení jsou veřejné nebo chráněné metody v sestaveních se silnými názvy implicitně chráněny [požadavky propojení](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) pro úplný vztah důvěryhodnosti; pouze plně důvěryhodní volající mají přístup k sestavení se silným názvem. Sestavení se silným názvem označená <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributem (APTCA) nemají tuto ochranu. Atribut zakáže požadavek propojení, aby bylo sestavení přístupné volajícím, kteří nemají úplný vztah důvěryhodnosti, jako je například spouštění kódu z intranetu nebo z Internetu.

 Pokud je atribut APTCA přítomen v plně důvěryhodném sestavení a sestavení spustí kód v jiném sestavení, které nepovoluje částečně důvěryhodné volající, je možné zneužití zabezpečení. Pokud dvě metody `M1` a `M2` splňují následující podmínky, mohou škodlivé volající používat metodu `M1` pro obejít požadavky na odkaz implicitní úplný vztah důvěryhodnosti, který chrání `M2` :

- `M1` je veřejnou metodou deklarovanou v plně důvěryhodném sestavení, které má atribut APTCA.

- `M1` volá metodu `M2` mimo `M1` sestavení.

- `M2`sestavení nemá atribut APTCA a proto by neměl být spuštěn pomocí nebo jménem volajících, které jsou částečně důvěryhodné.

  Částečně důvěryhodný volající `X` může volat metodu `M1` , což je způsob `M1` volání `M2` . Vzhledem k tomu, že nemá `M2` atribut APTCA, musí jeho bezprostřední volající ( `M1` ) splňovat požadavek propojení pro úplný vztah důvěryhodnosti; `M1` má úplný vztah důvěryhodnosti, a proto splňuje tuto kontrolu. Bezpečnostní riziko je způsobeno tím, že se `X` neúčastní požadavku na propojení, který je chráněn `M2` před nedůvěryhodnými volajícími. Proto metody s atributem APTCA nesmí volat metody, které nemají atribut.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud je vyžadován atribut APCTA, použijte požadavek na ochranu metody, která volá do sestavení s úplným vztahem důvěryhodnosti. Přesná oprávnění budou záviset na funkcích, které vaše metoda zveřejňuje. Pokud je to možné, zabezpečte metodu s požadavkem na úplný vztah důvěryhodnosti, abyste zajistili, že základní funkce nebudou vystaveny částečně důvěryhodným volajícím. Pokud to není možné, vyberte sadu oprávnění, která efektivně chrání vystavené funkce. Další informace o požadavcích naleznete v tématu [Demands](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Chcete-li bezpečně potlačit upozornění z tohoto pravidla, je nutné zajistit, aby funkce vystavené vaší metodou nepřímo ani nepřímo nepovolovaly volajícím přístup k citlivým informacím, operacím nebo prostředkům, které lze použít destruktivním způsobem.

## <a name="example"></a>Příklad
 Následující příklad používá dvě sestavení a testovací aplikaci k ilustraci chyby zabezpečení zjištěné tímto pravidlem. První sestavení nemá atribut APTCA a neměl by být přístupný pro částečně důvěryhodné volající (reprezentované `M2` v předchozí diskuzi).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Příklad
 Druhé sestavení je plně důvěryhodné a umožňuje částečně důvěryhodných volajících (reprezentovaných `M1` v předchozí diskuzi).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Příklad
 Testovací aplikace (reprezentovaná `X` v předchozí diskusi) je částečně důvěryhodná.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Poptávka pro úplný vztah důvěryhodnosti: požadavek se nezdařil.** 
 **Byla volána metoda ClassRequiringFullTrust. DoWork.**
## <a name="related-rules"></a>Související pravidla
 [CA2117: Typy APTCA by měl rozšiřovat pouze základní typy APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Viz také
 [Pokyny k zabezpečenému kódování](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework sestavení, která mohou být na základě částečně důvěryhodného kódu,](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [pomocí knihoven z částečně důvěryhodného kódu](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [vyžaduje](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [propojení požadavky](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) na [data a modelování](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
