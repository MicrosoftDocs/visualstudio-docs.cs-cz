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
ms.openlocfilehash: 2ee166f8bbc14e66968cd4f7c265331854905ac9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662948"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Neoznačujte obsluhované součásti pomocí WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategorie|Microsoft. Usage|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Metoda v typu, který dědí z <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>, je označena atributem <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Web.Services.WebMethodAttribute> platí pro metody v rámci webové služby XML, které byly vytvořeny pomocí ASP.NET; umožňuje volat metodu ze vzdálených webových klientů. Metoda a třída musí být veřejné a musí být spouštěny ve webové aplikaci v ASP.NET. typy <xref:System.EnterpriseServices.ServicedComponent> hostují aplikace modelu COM+ a můžou používat služby COM+. <xref:System.Web.Services.WebMethodAttribute> se nepoužije na typy <xref:System.EnterpriseServices.ServicedComponent>, protože nejsou určené pro stejné scénáře. Konkrétně přidáním atributu do metody <xref:System.EnterpriseServices.ServicedComponent> nezpůsobí, že se metoda bude volat ze vzdálených webových klientů. Vzhledem k tomu, že <xref:System.Web.Services.WebMethodAttribute> a metoda <xref:System.EnterpriseServices.ServicedComponent> mají konfliktní chování a požadavky pro kontext a tok transakcí, chování metody bude v některých scénářích nesprávné.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte atribut z metody <xref:System.EnterpriseServices.ServicedComponent>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Neexistují žádné scénáře, ve kterých je kombinace těchto prvků správná.

## <a name="see-also"></a>Viz také
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName><xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
