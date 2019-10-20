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
ms.openlocfilehash: 9a4663fe3bc09b27bad9eeec05e325f07a3de6f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603056"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy by neměly rozšířit určité základní typy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
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
 Pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verze 1 se doporučuje odvodit nové výjimky z <xref:System.ApplicationException>. Doporučení se změnilo a nové výjimky by měly odvozovat z <xref:System.Exception?displayProperty=fullName> nebo jedné z jejích podtříd v oboru názvů <xref:System>.

 Nevytvářejte podtřídu <xref:System.Xml.XmlDocument>, pokud chcete vytvořit zobrazení XML základního objektového modelu nebo zdroje dat.

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
 Potlačit upozornění z tohoto pravidla na porušení <xref:System.ApplicationException>. Z tohoto pravidla je bezpečné potlačit upozornění na porušení <xref:System.Xml.XmlDocument>. Je bezpečné potlačit upozornění na neobecnou kolekci, pokud byl kód vydaný dříve.
