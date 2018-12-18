---
title: 'CA1710: Identifikátory by měly mít správnou příponu | Dokumentace Microsoftu'
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
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2256e3f20dfdb4ddb8efa28d7ecdd203a139bcc5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940161"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Identifikátory by měly mít správnou příponu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategorie|Microsoft.Naming|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Identifikátor nemá správnou příponu.

## <a name="rule-description"></a>Popis pravidla
 Podle úmluvy názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní, nebo typů odvozených z těchto typů máte příponu, která je přidružena k základní typ nebo rozhraní.

 Zásady vytváření názvů poskytují obecný vzhled knihovnám využívajících common language runtime. To snižuje učit se, která vyžaduje nové knihovny softwaru a zvyšuje důvěru zákazníků, že byla vyvinuta knihovny někdo, kdo má odborných znalostí v vývoj spravovaného kódu.

 V následující tabulce jsou uvedeny základní typy a rozhraní, které mají přidružené přípony.

|Základní typ nebo rozhraní|Přípona|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Atribut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Výjimka|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Kolekce|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Slovník|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Kolekce|
|<xref:System.Collections.Queue?displayProperty=fullName>|Kolekce nebo fronty|
|<xref:System.Collections.Stack?displayProperty=fullName>|Kolekce nebo zásobníku|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Kolekce|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Slovník|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Kolekci nebo tento objekt DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Stream|
|<xref:System.Security.IPermission?displayProperty=fullName>|Oprávnění|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Podmínka|
|Delegát obslužné rutiny události.|Obslužná rutina události|

 Typy, které implementují <xref:System.Collections.ICollection> a jsou zobecněného typu datové struktury, jako například slovníku, zásobníku nebo fronty, jsou povolené názvy, které poskytují smysluplné informace o zamýšlené použití typu.

 Typy, které implementují <xref:System.Collections.ICollection> a jsou kolekce konkrétní položky mají názvy, které končí slovem "Kolekce". Například kolekce <xref:System.Collections.Queue> objektů bude mít název "QueueCollection". Přípona "Kolekce" znamená, že členové kolekce jsou uvedené s použitím `foreach` (`For Each` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) příkaz.

 Typy, které implementují <xref:System.Collections.IDictionary> mít názvy, které končí slovem "Slovník" i v případě, že typ implementuje rovněž <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.ICollection>. Konvence pojmenování příponu "Kolekce" a "Slovník" umožnit uživatelům si rozlišovat mezi následujících vzorů dvě výčtu.

 Typy s příponou "Kolekce" postupovat podle tohoto vzoru výčtu.

```
foreach(SomeType x in SomeCollection) { }
```

 Typy s příponou "Slovník" postupovat podle tohoto vzoru výčtu.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 A <xref:System.Data.DataSet> objekt se skládá z kolekce <xref:System.Data.DataTable> objekty, které se skládají z kolekce <xref:System.Data.DataColumn?displayProperty=fullName> a <xref:System.Data.DataRow?displayProperty=fullName> objekty, mimo jiné. Implementace těchto kolekcí <xref:System.Collections.ICollection> prostřednictvím základní třídy <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> třídy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Přejmenujte typ tak, aby příponu správný výraz.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění použít příponu "Kolekce", pokud typ je zobecněný datová struktura, která může rozšířit nebo, který bude obsahovat libovolné sadu různých položek. Název, který poskytuje důležité informace o implementaci, výkon nebo dalších vlastností datové struktury v takovém případě může mít smysl (například BinaryTree). V případech, kde typ představuje kolekci určitého typu (například třída StringCollection), nepotlačujte upozornění tohoto pravidla vzhledem k tomu, že přípona označuje, že můžete vytvořit výčet typu pomocí `foreach` příkazu.

 Pro další přípony nepotlačujte upozornění tohoto pravidla. Přípona umožňuje zamýšlené použití bude zřejmé z názvu typu.

## <a name="related-rules"></a>Související pravidla
 [CA1711: Identifikátory by neměly mít nesprávnou příponu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Viz také
 [Atributy](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: události a delegáti](http://msdn.microsoft.com/en-us/d98fd58b-fa4f-4598-8378-addf4355a115)



