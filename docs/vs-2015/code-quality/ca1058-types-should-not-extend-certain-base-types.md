---
title: 'CA1058: typy by neměly rozkrývat určité základní typy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d8e267b1e6203759efc91936a3b13059368a3862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545389"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy by neměly rozšiřovat určité základní typy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Externě viditelný typ rozšiřuje určité základní typy. V současné době toto pravidlo sestaví typy, které jsou odvozeny z následujících typů:

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Popis pravidla
 Pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi 1 se doporučuje odvodit nové výjimky z <xref:System.ApplicationException> . Doporučení se změnilo a nové výjimky by měly být odvozeny z <xref:System.Exception?displayProperty=fullName> nebo jedné z jejích podtříd v <xref:System> oboru názvů.

 Nevytvářejte podtřídu, <xref:System.Xml.XmlDocument> Pokud chcete vytvořit zobrazení XML základního objektového modelu nebo zdroje dat.

### <a name="non-generic-collections"></a>Neobecné kolekce
 Pokud je to možné, používejte a rozšíříte obecné kolekce. Nezvětšujte neobecné kolekce v kódu, pokud jste ho předtím dodali.

 **Příklady nesprávného použití**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Příklady správného použití**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odvodit typ z jiného základního typu nebo z obecné kolekce.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla pro porušení <xref:System.ApplicationException> . Z tohoto pravidla je bezpečné potlačit upozornění, které se týká porušení <xref:System.Xml.XmlDocument> . Je bezpečné potlačit upozornění na neobecnou kolekci, pokud byl kód vydaný dříve.
