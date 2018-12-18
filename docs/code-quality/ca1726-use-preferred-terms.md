---
title: 'CA1726: Použijte upřednostňované výrazy'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c81bd543a6695adcea37db5ab8570ff7749c0160
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551451"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Použijte upřednostňované výrazy

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Kategorie|Microsoft.Naming|
|Narušující změna|Zásadní - při vyvolání na sestavení<br /><br /> Bez konce – při vyvolání na parametry typu|

## <a name="cause"></a>příčina

Název externě viditelného identifikátoru zahrnuje výraz, pro který existuje alternativní upřednostňovaný výraz. Nebo název obsahuje také výraz příznak nebo příznaky.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo analyzuje identifikátor do tokenů. Každý jeden token a každou souvislých kombinaci duální tokenu je ve srovnání s podmínkami, které jsou integrované do pravidla a v části zastaralé vlastní slovníky. V následující tabulce jsou uvedeny podmínky, které jsou součástí pravidla a jejich preferované alternativy.

|Zastaralé termín|Upřednostňovaný termín|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` Nebo `Flags`|Neexistuje žádné nahrazující výraz. Nepoužívejte.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte výraz s alternativní upřednostňovaný výraz.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla pouze v případě, že je název identifikátoru je úmyslné a se vztahuje konkrétně k původní termín místo Upřednostňovaný termín.

## <a name="related-rules"></a>Související pravidla
 [Upozornění na pojmenování](../code-quality/naming-warnings.md)