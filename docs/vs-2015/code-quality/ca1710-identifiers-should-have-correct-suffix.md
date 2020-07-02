---
title: 'CA1710: identifikátory by měly mít správnou příponu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ee7ce7c4e9edad9d941b4a70b2a199a37130e43
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543985"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Identifikátory by měly mít správnou příponu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Identifikátor nemá správnou příponu.

## <a name="rule-description"></a>Popis pravidla
 Podle konvence mají názvy typů, které rozšíří určité základní typy nebo které implementují určitá rozhraní nebo typy odvozené z těchto typů, příponu, která je přidružena k základnímu typu nebo rozhraní.

 Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

 Následující tabulka uvádí základní typy a rozhraní, které mají přidružené přípony.

|Základní typ/rozhraní|Auditování|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Atribut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Výjimka|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Kolekce|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Slovník|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Kolekce|
|<xref:System.Collections.Queue?displayProperty=fullName>|Kolekce nebo fronta|
|<xref:System.Collections.Stack?displayProperty=fullName>|Kolekce nebo zásobník|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Kolekce|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Slovník|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Kolekce nebo DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Datový proud|
|<xref:System.Security.IPermission?displayProperty=fullName>|Oprávnění|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Podmínka|
|Delegát obslužné rutiny události.|EventHandler|

 Typy, které implementují <xref:System.Collections.ICollection> a jsou zobecněný typ datové struktury, jako je slovník, zásobník nebo fronta, jsou povoleny názvy, které poskytují smysluplnější informace o zamýšleném využití typu.

 Typy, které implementují <xref:System.Collections.ICollection> a jsou kolekce konkrétních položek, mají názvy končící slovem ' Collection '. Například kolekce <xref:System.Collections.Queue> objektů by měla mít název QueueCollection. Přípona ' Collection ' znamená, že členy kolekce lze vyčíslit pomocí `foreach` `For Each` příkazu (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

 Typy, které implementují <xref:System.Collections.IDictionary> názvy končící slovem Dictionary, i když typ také implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.ICollection> . Konvence pojmenování přípon kolekcí a slovníku umožňují uživatelům rozlišovat následující dva vzory výčtu.

 Typy s příponou Collection se řídí tímto vzorem výčtu.

```
foreach(SomeType x in SomeCollection) { }
```

 Typy s příponou Dictionary následují po tomto vzoru výčtu.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 <xref:System.Data.DataSet>Objekt se skládá z kolekce <xref:System.Data.DataTable> objektů, které se skládají z kolekcí objektů <xref:System.Data.DataColumn?displayProperty=fullName> a <xref:System.Data.DataRow?displayProperty=fullName> , mimo jiné. Tyto kolekce jsou implementovány <xref:System.Collections.ICollection> prostřednictvím základní <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> třídy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Přejmenujte typ tak, aby se najmenoval správným termínem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud je typ zobecněnou datovou strukturou, která může být rozšířená nebo která bude obsahovat libovolnou sadu různých položek, je bezpečné potlačit upozornění na použití přípony kolekce. V tomto případě je název, který poskytuje smysluplné informace o implementaci, výkonu nebo dalších vlastnostech struktury dat, smyslem (například BinaryTree). V případech, kdy typ představuje kolekci konkrétního typu (například StringCollection), potlačíte upozornění z tohoto pravidla, protože přípona označuje, že typ lze vytvořit pomocí `foreach` příkazu.

 U jiných přípon potlačíte upozornění z tohoto pravidla. Přípona umožňuje, aby bylo zamýšlené použití zřejmé z názvu typu.

## <a name="related-rules"></a>Související pravidla
 [CA1711: Identifikátory by neměly mít nesprávnou příponu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Viz také
 [Atributy](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: události a Delegáti](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
