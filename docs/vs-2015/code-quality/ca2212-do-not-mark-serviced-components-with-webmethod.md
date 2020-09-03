---
title: 'CA2212: neoznačujte obsluhované součásti pomocí WebMethod | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c707fef5562b932b6232300131f6e6e6efef6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534560"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Neoznačujte obsluhované komponenty pomocí WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategorie|Microsoft. Usage|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Metoda v typu, který dědí z, <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> je označena atributem <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> .

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Web.Services.WebMethodAttribute> platí pro metody v rámci webové služby XML, které byly vytvořeny pomocí ASP.NET; umožňuje volat metodu ze vzdálených webových klientů. Metoda a třída musí být veřejné a musí být spouštěny ve webové aplikaci v ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> typy jsou hostovány aplikacemi modelu COM+ a mohou používat služby modelu COM+. <xref:System.Web.Services.WebMethodAttribute> není aplikován na <xref:System.EnterpriseServices.ServicedComponent> typy, protože nejsou určeny pro stejné scénáře. Konkrétně přidáním atributu do metody nezpůsobí, <xref:System.EnterpriseServices.ServicedComponent> že se metoda bude volat ze vzdálených webových klientů. Vzhledem k tomu <xref:System.Web.Services.WebMethodAttribute> <xref:System.EnterpriseServices.ServicedComponent> , že metoda a má konfliktní chování a požadavky pro kontext a tok transakcí, chování metody bude v některých scénářích nesprávné.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte atribut z <xref:System.EnterpriseServices.ServicedComponent> metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Neexistují žádné scénáře, ve kterých je kombinace těchto prvků správná.

## <a name="see-also"></a>Viz také
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
