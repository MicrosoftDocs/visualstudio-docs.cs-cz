---
title: 'CA1302: Nekódujte pevně řetězce závislé na národním prostředí'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 727acfa5497f2d7f0d09349ff2f5f6648c9d1ca6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444413"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Nekódujte pevně řetězce závislé na národním prostředí

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategorie|Microsoft. Globalization|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Metoda používá řetězcový literál, který představuje část cesty určitých systémových složek.

## <a name="rule-description"></a>Popis pravidla
Výčet <xref:System.Environment.SpecialFolder?displayProperty=fullName> obsahuje členy, kteří odkazují na speciální systémové složky. Umístění těchto složek může mít různé hodnoty v různých operačních systémech, uživatel může změnit některá umístění a umístění jsou lokalizovaná. Příkladem speciální složky je systémová složka, která je "C:\WINDOWS\system32" na [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], ale "C:\WINNT\system32" v [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. Metoda <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> vrací umístění, která jsou asociována s výčtem <xref:System.Environment.SpecialFolder>. Umístění, která jsou vrácena <xref:System.Environment.GetFolderPath%2A>, jsou lokalizována a vhodná pro aktuálně běžící počítač.

Toto pravidlo tokenizes cesty ke složkám, které jsou načteny pomocí metody <xref:System.Environment.GetFolderPath%2A> do samostatných úrovní adresáře. Každý řetězcový literál je porovnán s tokeny. Pokud je nalezena shoda, předpokládá se, že metoda sestavuje řetězec, který odkazuje na umístění systému, které je přidruženo k tokenu. Pro přenositelnost a lokalizovatelnosti použijte metodu <xref:System.Environment.GetFolderPath%2A> pro načtení umístění speciálních systémových složek namísto použití řetězcových literálů.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, načtěte umístění pomocí metody <xref:System.Environment.GetFolderPath%2A>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Pokud se řetězcový literál nepoužívá k odkazování na jedno ze systémových umístění, které je spojeno s výčtem <xref:System.Environment.SpecialFolder>, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
Následující příklad vytvoří cestu ke složce Common data Application, která z tohoto pravidla generuje tři upozornění. Dále příklad načte cestu pomocí metody <xref:System.Environment.GetFolderPath%2A>.

[!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
[!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA1303: Nepředávejte literály jako lokalizované parametry](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
