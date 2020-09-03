---
title: 'CA1711: identifikátory by neměly mít nesprávnou příponu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1e753083e9b4bda1e33553021ccb0027a2af2533
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544011"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Identifikátory by neměly mít nesprávnou příponu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Identifikátor nemá správnou příponu.

## <a name="rule-description"></a>Popis pravidla
 Pouze názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní, nebo typů odvozených z těchto typů by podle konvence měly končit určitými vyhrazenými příponami. Jiné názvy typů by neměly používat tyto vyhrazené přípony.

 Následující tabulka uvádí vyhrazené přípony a základní typy a rozhraní, ke kterým jsou přidruženy.

|Auditování|Základní typ/rozhraní|
|------------|--------------------------|
|Atribut|<xref:System.Attribute?displayProperty=fullName>|
|Kolekce|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Slovník|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|Delegát obslužné rutiny události|
|Výjimka|<xref:System.Exception?displayProperty=fullName>|
|Oprávnění|<xref:System.Security.IPermission?displayProperty=fullName>|
|Fronta|<xref:System.Collections.Queue?displayProperty=fullName>|
|Zásobník|<xref:System.Collections.Stack?displayProperty=fullName>|
|Datový proud|<xref:System.IO.Stream?displayProperty=fullName>|

 Kromě **toho by se neměly používat** následující přípony:

- Delegát

- Výčet

- Impl – místo toho použijte „Core“

- Ex nebo podobná přípona k odlišení starší verze stejného typu

  Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Odeberte příponu z názvu typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění tohoto pravidla, pokud přípona nemá v doméně aplikace jednoznačný význam.

## <a name="related-rules"></a>Související pravidla
 [CA1710: Identifikátory by měly mít správnou příponu](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>Viz také
 [Atributy](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: události a Delegáti](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
