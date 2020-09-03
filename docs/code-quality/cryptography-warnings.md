---
title: Upozornění kryptografie
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78923dfd2873b53790421cde3fe01f024e267202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587693"
---
# <a name="cryptography-warnings"></a>Upozornění kryptografie
Upozornění kryptografie podporují bezpečnější knihovny a aplikace přes správné použití kryptografie. Tato upozornění pomáhají zabránit chybám zabezpečení v programu. Pokud některá z těchto upozornění zakážete, měli byste v kódu jasně označit důvod a také informovat bezpečnostního úředníka vývoje projektu.

|Pravidlo|Popis|
|----------|-----------------|
|[CA5350: Nepoužívejte slabé kryptografické algoritmy](../code-quality/ca5350.md)|Slabé šifrovací algoritmy a funkce hash jsou dnes používány z mnoha důvodů, ale neměly by se používat k zajištění důvěrnosti nebo integrity dat, která chrání.        Toto pravidlo se aktivuje, když v kódu nalezne algoritmy TripleDES, SHA1 nebo RIPEMD160.|
|[CA5351: Nepoužívejte poškozené kryptografické algoritmy](../code-quality/ca5351.md)|Nefunkční kryptografické algoritmy nejsou považovány za zabezpečené a jejich použití by se mělo důrazně nedoporučuje. Toto pravidlo se aktivuje, když nalezne algoritmus hash MD5 nebo šifrovací algoritmy DES nebo RC2 v kódu.|
