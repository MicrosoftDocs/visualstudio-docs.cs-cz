---
title: Upozornění kryptografie
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c72dd1455405ecbabb86ca10744639d402881cef
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449139"
---
# <a name="cryptography-warnings"></a>Upozornění kryptografie
Upozornění kryptografie podporují bezpečnější knihovny a aplikace přes správné použití kryptografie. Tato upozornění pomáhají zabránit chybám zabezpečení v programu. Pokud některá z těchto upozornění zakážete, měli byste v kódu jasně označit důvod a také informovat bezpečnostního úředníka vývoje projektu.

|Pravidlo|Popis|
|----------|-----------------|
|[CA5350: Nepoužívejte slabé kryptografické algoritmy](../code-quality/ca5350.md)|Slabé šifrovací algoritmy a funkce hash jsou dnes používány z mnoha důvodů, ale neměly by se používat k zajištění důvěrnosti nebo integrity dat, která chrání.        Toto pravidlo se aktivuje, když v kódu nalezne algoritmy TripleDES, SHA1 nebo RIPEMD160.|
|[CA5351: Nepoužívejte poškozené kryptografické algoritmy](../code-quality/ca5351.md)|Nefunkční kryptografické algoritmy nejsou považovány za zabezpečené a jejich použití by se mělo důrazně nedoporučuje. Toto pravidlo se aktivuje, když nalezne algoritmus hash MD5 nebo šifrovací algoritmy DES nebo RC2 v kódu.|
