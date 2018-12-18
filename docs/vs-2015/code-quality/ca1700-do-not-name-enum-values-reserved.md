---
title: 'CA1700: Nepojmenovávejte hodnoty výčtu &#39;vyhrazeno&#39; | Dokumentace Microsoftu'
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
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3229b8432af89857d1aadd8bf1531c8b11a29ed7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897989"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Nepojmenovávejte hodnoty výčtu &#39;Reserved&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategorie|Microsoft.Naming|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Název na člena výčtu obsahuje slovo "vyhrazených".

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna. Uživatelům ignorovat člen to, že název obsahuje "vyhrazených" ani můžete spolehnout na uživatelům číst a dodržováním dokumentaci, by neměli očekávat. Navíc protože vyhrazené členy se zobrazí v prohlížeči objektů a inteligentní Integrovaná vývojová prostředí, mohou způsobit zmatení, o tom, které jsou členy ve skutečnosti používá.

 Namísto použití vyhrazeným členem, přidání nového člena výčtu v budoucí verzi. Ve většině případů není přidání nového člena k zásadní změně, za předpokladu, přidání nezpůsobí hodnoty původní členů, chcete-li změnit.

 Pro omezený počet případů, je přidání člena k zásadní změně i v případě, že původní členy zachovat původní hodnoty. Především, nejde vrátit nového člena z existující cesty kódu bez narušení volajícím, které používají `switch` (`Select` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) příkaz na návratovou hodnotu, která zahrnuje celou člena seznamu a, která vyvolají výjimku výchozí případ. Sekundární problém je, že kód klienta, jako nemusí zpracovávat změny v chování z metody reflexe <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. Podle toho, pokud má nový člen má být vrácena z existující metody nebo nekompatibilita známé aplikace nastává z důvodu špatného reflexe využití, pouze pevná řešení, je:

1. Přidáte nový výčet, který obsahuje původní a nové členy.

2. Označte výčet pomocí původní <xref:System.ObsoleteAttribute?displayProperty=fullName> atribut.

   Postupujte stejným způsobem pro žádné externě viditelné typy nebo členy, které zveřejňují původní výčtu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte nebo změňte jeho název.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla pro člena, který je aktuálně používán nebo pro knihovny, které byly dříve součástí.

## <a name="related-rules"></a>Související pravidla
 [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: Nezačínejte hodnoty výčtu s názvem typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Úložiště výčtu by měl být Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: Výčty by měly mít nulovou hodnotu](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)



