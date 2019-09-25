---
title: 'CA1726: Použijte upřednostňované výrazy'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f359f7aa24ada0edf2c98a7d527ed715df85086
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233925"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Použijte upřednostňované výrazy

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Kategorie|Microsoft.Naming|
|Zásadní změna|Přerušení – při vyvolání u sestavení<br /><br /> Nerozdělitelné – při vyvolání u parametrů typu|

## <a name="cause"></a>příčina

Název externě viditelného identifikátoru zahrnuje výraz, pro který existuje alternativní upřednostňovaný výraz. Nebo název obsahuje příznak Term nebo Flags.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo analyzuje identifikátor na tokeny. Každý token a Každá souvislá kombinace dvou tokenů je porovnána s podmínkami, které jsou integrovány v pravidle a v nepoužívané části libovolného vlastního slovníku. V následující tabulce jsou uvedeny výrazy, které jsou součástí pravidla a jejich preferované alternativy.

|Zastaralý termín|Upřednostňovaný pojem|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` Nebo `Flags`|Neexistuje žádný náhradní termín. Nepoužívejte.|
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

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, nahraďte výraz upřednostňovaným alternativním termínem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačí upozornění z tohoto pravidla pouze v případě, že název identifikátoru je záměrné a vztahuje se konkrétně k původnímu termínu místo upřednostňovaného termínu.

## <a name="related-rules"></a>Související pravidla
[Upozornění na pojmenování](../code-quality/naming-warnings.md)