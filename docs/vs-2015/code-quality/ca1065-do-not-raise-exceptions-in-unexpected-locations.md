---
title: 'CA1065: nevyvolává výjimky v neočekávaných umístěních | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 439c6b5fc30be2e76eb6c0b6a44b1ec5226633b1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295943"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Nevyvolávejte výjimky v neočekávaných umístěních
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Kategorie|Microsoft.Design|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Metoda, u které není předpokládáno vyvolání výjimky, vyvolá výjimku.

## <a name="rule-description"></a>Popis pravidla
 Metody, které nejsou očekávány k vyvolání výjimek, mohou být zařazeny následujícím způsobem:

- Metody Get vlastnosti

- Metody přístupového objektu události

- Equals – metody

- Metody GetHashCode

- Metody ToString

- Statické konstruktory

- Finalizační metody

- Metody Dispose

- Operátory rovnosti

- Operátory implicitního přetypování

  Následující části popisují tyto typy metod.

### <a name="property-get-methods"></a>Metody Get vlastnosti
 Vlastnosti jsou v podstatě inteligentní pole. Proto by se měly chovat jako pole co nejvíce. Pole nevyvolají výjimky a ani žádné vlastnosti. Pokud máte vlastnost, která vyvolá výjimku, zvažte její vytvoření metodou.

 Následující výjimky mohou být vyvolány z metody Get vlastnosti:

- <xref:System.InvalidOperationException?displayProperty=fullName> a všechny deriváty (včetně <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> a všechny deriváty

- <xref:System.ArgumentException?displayProperty=fullName> (jenom z indexovaného Get)

- <xref:System.Collections.Generic.KeyNotFoundException> (jenom z indexovaného Get)

### <a name="event-accessor-methods"></a>Metody přístupového objektu události
 Přístupové objekty událostí by měly být jednoduché operace, které nevyvolají výjimky. Událost by neměla vyvolat výjimku při pokusu o přidání nebo odebrání obslužné rutiny události.

 Následující výjimky mohou být vyvolány z objektu k vyvolání události:

- <xref:System.InvalidOperationException?displayProperty=fullName> a všechny deriváty (včetně <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> a všechny deriváty

- <xref:System.ArgumentException> a deriváty

### <a name="equals-methods"></a>Equals – metody
 Následující metody **Equals** by neměly vyvolat výjimky:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](https://go.microsoft.com/fwlink/?LinkId=113472)

  Metoda **EQUAL** by měla vracet `true` nebo `false` namísto vyvolání výjimky. Například pokud se rovná se předává dvěma neodpovídajícím typům, měl by vracet pouze `false` namísto vyvolání <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Metody GetHashCode
 Následující metody **GetHashCode** by obvykle neměly vyvolat výjimky:

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode (T)](https://go.microsoft.com/fwlink/?LinkId=113477)

  **GetHashCode** by měla vždycky vracet hodnotu. V opačném případě můžete ztratit položky v zatřiďovací tabulce.

  Verze **GetHashCode** , které přebírají argument, mohou vyvolat <xref:System.ArgumentException>. **Objekt. GetHashCode** by však nikdy neměl vyvolat výjimku.

### <a name="tostring-methods"></a>Metody ToString
 Ladicí program používá <xref:System.Object.ToString%2A?displayProperty=fullName> k zobrazení informací o objektech ve formátu řetězce. Proto by **ToString** neměl měnit stav objektu a neměl by vyvolávat výjimky.

### <a name="static-constructors"></a>Statické konstruktory
 Vyvolávání výjimek ze statického konstruktoru způsobí, že typ bude v aktuální doméně aplikace nepoužitelný. K vyvolání výjimky ze statického konstruktoru byste měli mít velmi dobrý důvod (například potíže se zabezpečením).

### <a name="finalizers"></a>Finalizační metody
 Vyvolání výjimky z finalizační metody způsobí, že modul CLR nebude úspěšný, což rozvine proces. Proto by se měly vyvarovat výjimky v finalizační metodě vždy.

### <a name="dispose-methods"></a>Metody Dispose
 Metoda <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> by neměla vyvolat výjimku. Dispose se často volá jako součást logiky vyčištění v klauzuli `finally`. Proto explicitní vyvolání výjimky z Dispose vynutí uživatele přidat zpracování výjimek v rámci klauzule `finally`.

 Cesta k **Dispose (false)** kódu by nikdy neměla vyvolat výjimky, protože to je téměř vždy voláno od finalizační metody.

### <a name="equality-operators--"></a>Operátory rovnosti (= =,! =)
 Podobně jako metody Equals by operátory rovnosti měly vracet buď `true`, nebo `false` a neměly by vyvolávat výjimky.

### <a name="implicit-cast-operators"></a>Operátory implicitního přetypování
 Vzhledem k tomu, že uživatel často neví, že byl volán Operátor implicitního přetypování, výjimka vyvolaná implicitním operátorem přetypování je zcela neočekávaná. Proto by neměly být vyvolány žádné výjimky z implicitních operátorů přetypování.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pro metodu getter vlastnosti buď změňte logiku tak, že již není nutné vyvolat výjimku, nebo změňte vlastnost na metodu.

 U všech ostatních typů metod, které jsou uvedeny dříve, změňte logiku tak, aby již nemusela vyvolat výjimku.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění, pokud bylo porušení způsobeno deklarací výjimky, nikoli vyvolanou výjimkou.

## <a name="related-rules"></a>Související pravidla
 [CA2219: Nevyvolávejte výjimky v klauzulích výjimky](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Viz také
 [Upozornění ohledně návrhu](../code-quality/design-warnings.md)
