---
title: 'CA2106: zabezpečení kontrolní výrazy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eb0e097c2f13fa9d9279a5f3e9761a53cb6e4b1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547742"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Zabezpečte kontrolní příkazy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Metoda uplatňuje oprávnění a na volajícím nejsou vykonány žádné kontroly zabezpečení.

## <a name="rule-description"></a>Popis pravidla
 Uplatnění oprávnění zabezpečení bez provedení jakékoliv kontroly zabezpečení může zanechat ve vašem kódu zneužitelné slabé stránky zabezpečení. Pokud je uplatněno oprávnění zabezpečení, procházení zásobníku zabezpečení se zastaví. Pokud potvrdíte oprávnění bez provedení kontroly volajícího, volající by mohl nepřímo spustit kód pomocí vašich oprávnění. Výrazy bez kontroly zabezpečení jsou přípustné pouze v případě, že jste si jisti, že kontrolní výraz nelze použít škodlivým způsobem. Kontrolní výraz je neškodný, pokud je kód, který voláte, neškodný, nebo uživatelé nemohou předat do kódu, který zavoláte, libovolné informace.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte požadavek zabezpečení do metody nebo jejího deklarovaného typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění od tohoto pravidla až po pečlivou kontrolu zabezpečení.

## <a name="see-also"></a>Viz také
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Pokyny pro zabezpečené kódování](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
