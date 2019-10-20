---
title: Upozornění kryptografie | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d9f5694ccf48615ebdf7157adc80543b0fbb71eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667675"
---
# <a name="cryptography-warnings"></a>Upozornění kryptografie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upozornění kryptografie podporují bezpečnější knihovny a aplikace přes správné použití kryptografie. Tato upozornění pomáhají zabránit chybám zabezpečení v programu. Pokud některá z těchto upozornění zakážete, měli byste v kódu jasně označit důvod a také informovat bezpečnostního úředníka vývoje projektu.

|Pravidlo|Popis|
|----------|-----------------|
|[CA5350: Nepoužívejte slabé kryptografické algoritmy](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Slabé šifrovací algoritmy a funkce hash jsou dnes používány z mnoha důvodů, ale neměly by se používat k zajištění důvěrnosti nebo integrity dat, která chrání.        Toto pravidlo se aktivuje, když v kódu nalezne algoritmy TripleDES, SHA1 nebo RIPEMD160.|
|[CA5351: Nepoužívejte poškozené kryptografické algoritmy](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Nefunkční kryptografické algoritmy nejsou považovány za zabezpečené a jejich použití by se mělo důrazně nedoporučuje. Toto pravidlo se aktivuje, když nalezne algoritmus hash MD5 nebo šifrovací algoritmy DES nebo RC2 v kódu.|
