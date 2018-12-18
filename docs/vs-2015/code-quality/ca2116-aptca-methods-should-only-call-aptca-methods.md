---
title: 'CA2116: Metody APTCA by měly volat pouze metody APTCA | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 766de62f4781dc7ce164155a2090ffabac913a22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819547"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Metody APTCA by měly volat pouze metody APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Metodu v sestavení <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atribut volá metodu v sestavení, který nemá atribut.

## <a name="rule-description"></a>Popis pravidla
 Ve výchozím nastavení, veřejné nebo chráněné metody v podepisují sestavení silnými názvy jsou implicitně chráněné [požadavky propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) pro úplný vztah důvěryhodnosti; pouze plně důvěryhodní volající může přistupovat k sestavení se silným názvem. Sestavení se silným názvem označené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA) nemají tuto ochranu. Atribut zakáže požadavku propojení, zpřístupnění sestavení volajícím, které nemají úplný vztah důvěryhodnosti, jako je například kód provádění z intranetu nebo Internetu.

 Když je atribut APTCA uveden pro plně důvěryhodná sestavení a sestavení spustí kód v jiném sestavení, který neumožňuje volání částečně důvěryhodným volajícím, je možné zneužití zabezpečení. Pokud dvě metody `M1` a `M2` splňovat následující podmínky, škodlivý volající použít metodu `M1` obejít požadavek propojení implicitní úplný vztah důvěryhodnosti, který chrání `M2`:

- `M1` je v plně důvěryhodná sestavení, který má atribut APTCA deklarována veřejnou metodu.

- `M1` volá metodu `M2` mimo `M1`pro sestavení.

- `M2`od sestavení nemá atribut APTCA a proto by neměl být spouštěn podle nebo jejich jménem volajícím, které jsou částečně důvěryhodné.

  Částečně důvěryhodné volající `X` lze zavolat metodu `M1`, způsobující `M1` volat `M2`. Protože `M2` nemá atribut APTCA, jeho bezprostředního volajícího (`M1`) musí uspokojit požadavky propojení pro úplnou důvěryhodnost; `M1` má úplný vztah důvěryhodnosti a proto splňuje tato kontrola. Je bezpečnostní riziko, protože `X` není součástí uspokojit poptávku odkaz, který chrání `M2` z nedůvěryhodných volajících. Metody s atributem APTCA proto nesmějí volat metody, které nemají atribut.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud je vyžadován atribut APTCA, použijte k ochraně metodu, která volá do sestavení úplné důvěryhodnosti vyžádání. Vyžádání vás bude záviset na konkrétní oprávnění funkce vystavené metodu. Pokud je to možné, Chraňte metody s požadavky pro úplný vztah důvěryhodnosti k zajištění toho, že základní funkce není vystaven částečně důvěryhodné volající. Pokud to není možné, vyberte sadu oprávnění, která efektivně chrání vystavené funkce. Další informace o požadavky najdete v tématu [požadavky](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete bezpečně potlačit upozornění tohoto pravidla, ujistěte se, že funkce vystavené metodu přímo nebo nepřímo nepovoluje volající pro přístup k citlivé informace, operace nebo prostředky použité destruktivním způsobem.

## <a name="example"></a>Příklad
 Následující příklad používá dva sestavení a testovací aplikaci pro ilustraci ohrožení zabezpečení, zjistí toto pravidlo. První sestavení nemá atribut APTCA a by neměl být přístupný pro částečně důvěryhodných volajících (představované `M2` v předchozím diskusí).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Příklad
 Druhý sestavení je plně důvěryhodný a povoluje částečně důvěryhodné volající (představované `M1` v předchozím diskusí).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Příklad
 Testovací aplikace (představované `X` v předchozím diskusí) je částečně důvěryhodné.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Požadovat pro úplný vztah důvěryhodnosti: požadavek se nezdařil. ** 
 **ClassRequiringFullTrust.DoWork byla volána.**
## <a name="related-rules"></a>Související pravidla
 [CA2117: Typy APTCA by měly rozšířit pouze základní typy APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Viz také
 [Pokyny pro zabezpečené kódování](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [sestavení rozhraní .NET Framework skriptem částečně důvěryhodný kód](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [používání knihoven z částečně důvěryhodného kódu](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [požadavky](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [Požadavky na propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



