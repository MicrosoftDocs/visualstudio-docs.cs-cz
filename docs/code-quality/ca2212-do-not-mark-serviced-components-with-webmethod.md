---
title: 'CA2212: Neoznačujte obsluhované komponenty pomocí WebMethod'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b2ace5f6e51fc7a8d29faab14cc2332fd808f93
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231657"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Neoznačujte obsluhované komponenty pomocí WebMethod

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Metoda v typu, který dědí z <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> , je označena atributem. <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>

## <a name="rule-description"></a>Popis pravidla

<xref:System.Web.Services.WebMethodAttribute>platí pro metody v rámci webové služby XML, které byly vytvořeny pomocí ASP.NET; umožňuje volat metodu ze vzdálených webových klientů. Metoda a třída musí být veřejné a musí být spouštěny ve webové aplikaci v ASP.NET. <xref:System.EnterpriseServices.ServicedComponent>typy jsou hostovány aplikacemi modelu COM+ a mohou používat služby modelu COM+. <xref:System.Web.Services.WebMethodAttribute>není aplikován na <xref:System.EnterpriseServices.ServicedComponent> typy, protože nejsou určeny pro stejné scénáře. Konkrétně přidáním atributu do <xref:System.EnterpriseServices.ServicedComponent> metody nezpůsobí, že se metoda bude volat ze vzdálených webových klientů. Vzhledem <xref:System.Web.Services.WebMethodAttribute> k tomu <xref:System.EnterpriseServices.ServicedComponent> , že metoda a má konfliktní chování a požadavky pro kontext a tok transakcí, chování metody bude v některých scénářích nesprávné.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte atribut z <xref:System.EnterpriseServices.ServicedComponent> metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Neexistují žádné scénáře, ve kterých je kombinace těchto prvků správná.

## <a name="see-also"></a>Viz také:

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>