---
title: 'CA1059: Členové by neměli zveřejňovat určité konkrétní typy'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06b7d6f9f3a04f518beeb49af1985185255f2e46
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440802"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Členové by neměli zveřejňovat určité konkrétní typy

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategorie|Microsoft. Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Externě viditelný člen je konkrétní konkrétní typ nebo zpřístupňuje určité konkrétní typy prostřednictvím jednoho z jeho parametrů nebo návratové hodnoty. V současné době toto pravidlo nahlásí následující konkrétní typy:

- Typ odvozený od <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
Konkrétní typ je typ, který je zcela implementován, a lze tudíž vytvořit jeho instanci. Chcete-li zakázat rozšířené použití člena, nahraďte konkrétní typ navrhovaným rozhraním. To umožňuje členovi přijmout jakýkoli typ, který implementuje rozhraní, nebo použít, kde je očekáván typ, který implementuje rozhraní.

V následující tabulce jsou uvedeny cílené konkrétní typy a jejich navržené náhrady.

|Konkrétní typ|Nahrazení|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Použití rozhraní odpojí člena od konkrétní implementace zdroje dat XML.|

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte konkrétní typ na navrhované rozhraní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Pokud je třeba zadat konkrétní funkce poskytnuté konkrétním typem, je bezpečné potlačit zprávu od tohoto pravidla.

## <a name="related-rules"></a>Související pravidla
[CA1011: Zvažte předání základních typů jako parametrů](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
