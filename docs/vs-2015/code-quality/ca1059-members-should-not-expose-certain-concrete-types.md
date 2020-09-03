---
title: 'CA1059: členové by neměli zveřejňovat určité konkrétní typy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792426615dd78241ade1d38a24ec1f4d5702cede
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545376"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Členy by neměly zveřejňovat určité konkrétní typy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Externě viditelný člen je konkrétní konkrétní typ nebo zpřístupňuje určité konkrétní typy prostřednictvím jednoho z jeho parametrů nebo návratové hodnoty. V současné době toto pravidlo nahlásí následující konkrétní typy:

- Typ odvozený z <xref:System.Xml.XmlNode?displayProperty=fullName> .

## <a name="rule-description"></a>Popis pravidla
 Konkrétní typ je typ, který je zcela implementován, a lze tudíž vytvořit jeho instanci. Chcete-li zakázat rozšířené použití člena, nahraďte konkrétní typ navrhovaným rozhraním. To umožňuje členovi přijmout jakýkoli typ, který implementuje rozhraní, nebo použít, kde je očekáván typ, který implementuje rozhraní.

 V následující tabulce jsou uvedeny cílené konkrétní typy a jejich navržené náhrady.

|Konkrétní typ|Náhrada|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Použití rozhraní odpojí člena od konkrétní implementace zdroje dat XML.|

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte konkrétní typ na navrhované rozhraní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud je třeba zadat konkrétní funkce poskytnuté konkrétním typem, je bezpečné potlačit zprávu od tohoto pravidla.

## <a name="related-rules"></a>Související pravidla
 [CA1011: Zvažte předání základních typů jako parametrů](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
