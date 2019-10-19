---
title: 'CA2147: transparentní metody nemůžou používat kontrolní výrazy zabezpečení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f2bd0042b6f9a8e46939ab34c86294218fb79f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610161"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Transparentní metody nemusejí podporovat použití nepodmíněných výrazů zabezpečení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Kód, který je označen jako <xref:System.Security.SecurityTransparentAttribute>, nemá udělena dostatečná oprávnění k vyhodnocení.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo analyzuje všechny metody a typy v sestavení, které je buď 100% transparentní, nebo smíšené transparentní/kritické, a označí jakékoli deklarativní nebo imperativní použití <xref:System.Security.CodeAccessPermission.Assert%2A>.

 V době spuštění jakákoli volání <xref:System.Security.CodeAccessPermission.Assert%2A> z transparentního kódu způsobí vyvolání <xref:System.InvalidOperationException>. K této chybě může dojít v transparentním sestavení 100% a také ve smíšených transparentních/kritických sestaveních, kde je metoda nebo typ deklarována jako průhledná, ale obsahuje deklarativní nebo imperativní vyhodnocení.

 @No__t_0 2,0 zavedl funkci s názvem *transparentnost*. Jednotlivé metody, pole, rozhraní, třídy a typy mohou být buď transparentní, nebo kritické.

 Transparentní kód nemá povoleno zvyšovat oprávnění zabezpečení. Proto všechna oprávnění, která jsou udělena nebo vyřízená, jsou automaticky předána prostřednictvím kódu volající nebo hostitelské doméně aplikace. Příklady zvýšení oprávnění zahrnují kontrolní výrazy, LinkDemand, SuppressUnmanagedCode a kód `unsafe`.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li tento problém vyřešit, buď označte kód, který volá kontrolní výraz s <xref:System.Security.SecurityCriticalAttribute>, nebo odeberte Assert.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit zprávu od tohoto pravidla.

## <a name="example"></a>Příklad
 Tento kód selže, pokud je `SecurityTestClass` transparentní, pokud metoda `Assert` vyvolá <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Příklad
 Jednou z možností je přečíst si metodu SecurityTransparentMethod v níže uvedeném příkladu, a pokud je metoda považována za bezpečnou ke zvýšení oprávnění, označit SecurityTransparentMethod s bezpečným zabezpečením vyžaduje, aby bylo podrobné, úplné a bezplatné zabezpečení. audit musí být proveden u metody společně s jakýmkoli voláním, ke kterým dojde v rámci metody v rámci kontrolního výrazu:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Další možností je odebrat z kódu kontrolní výraz a nechat libovolné následné oprávnění v/v souboru, které vyžaduje tok nad rámec SecurityTransparentMethod k volajícímu. To umožňuje kontroly zabezpečení. V takovém případě není nutné provádět audit zabezpečení, protože požadavky na oprávnění budou předávány volajícímu nebo doméně aplikace. Požadavky na oprávnění jsou úzce řízeny prostřednictvím zásad zabezpečení, hostitelského prostředí a udělení oprávnění ke zdroji kódu.

## <a name="see-also"></a>Viz také
 [Upozornění zabezpečení](../code-quality/security-warnings.md)
