---
title: 'CA1059: Členové by neměli zveřejňovat určité konkrétní typy | Dokumentace Microsoftu'
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
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 894b4c22aaab2b0cce81053e6466b791a50b089a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816882"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Členové by neměli zveřejňovat určité konkrétní typy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Externě viditelného členu je některé konkrétní typ nebo zpřístupňuje určité konkrétní typy prostřednictvím jednoho z jeho parametry nebo návratovou hodnotu. Toto pravidlo v současné době sestavy vystavení následující konkrétní typy:

-   Typ odvozený od <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Konkrétní typ je typ, který je zcela implementován, a lze tudíž vytvořit jeho instanci. Chcete-li umožnit široké využití členu, nahraďte konkrétní typ navrhovaného rozhraní. To umožňuje členu, který chcete přijmout libovolný typ, který implementuje rozhraní, nebo použít, kde se očekává typ, který implementuje rozhraní.

 Následující tabulka uvádí cílové konkrétní typy a jejich navrhované nahrazení.

|Konkrétní typ|Nahrazení|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Pomocí rozhraní odděluje obě části člena z konkrétní implementaci zdroj dat XML.|

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte konkrétní typ na navrhovaného rozhraní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné k potlačení zprávy z tohoto pravidla, pokud konkrétní funkce poskytované službou konkrétní typ je povinný.

## <a name="related-rules"></a>Související pravidla
 [CA1011: Zvažte předání základních typů jako parametrů](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)



