---
title: 'CA1302: nenekódujte pevně řetězců specifických pro národní prostředí | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18da0471b1ac62f0e61b303c60b46c15cdc2e428
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539006"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Nekódujte pevně řetězce závislé na národním prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Metoda používá řetězcový literál, který představuje část cesty určitých systémových složek.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>Výčet obsahuje členy, kteří odkazují na speciální systémové složky. Umístění těchto složek může mít různé hodnoty v různých operačních systémech, uživatel může změnit některá umístění a umístění jsou lokalizovaná. Příkladem speciální složky je systémová složka, která je "C:\WINDOWS\system32" na serveru, [!INCLUDE[winxp](../includes/winxp-md.md)] ale "C:\Winnt\System32" [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] . <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>Metoda vrátí umístění, která jsou přidružena k <xref:System.Environment.SpecialFolder> výčtu. Umístění, která jsou vrácena nástrojem, <xref:System.Environment.GetFolderPath%2A> jsou lokalizována a vhodná pro aktuálně běžící počítač.

 Toto pravidlo tokenizes cesty ke složkám, které jsou načteny pomocí <xref:System.Environment.GetFolderPath%2A> metody do samostatných úrovní adresáře. Každý řetězcový literál je porovnán s tokeny. Pokud je nalezena shoda, předpokládá se, že metoda sestavuje řetězec, který odkazuje na umístění systému, které je přidruženo k tokenu. Pro přenositelnost a lokalizaci použijte <xref:System.Environment.GetFolderPath%2A> metodu pro načtení umístění speciálních systémových složek namísto použití řetězcových literálů.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, načtěte umístění pomocí <xref:System.Environment.GetFolderPath%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud se řetězcový literál nepoužívá k odkazování na jeden ze systémových umístění, která jsou přidružena k výčtu, je bezpečné potlačit upozornění od tohoto pravidla <xref:System.Environment.SpecialFolder> .

## <a name="example"></a>Příklad
 Následující příklad vytvoří cestu ke složce Common data Application, která z tohoto pravidla generuje tři upozornění. Dále příklad načte cestu pomocí <xref:System.Environment.GetFolderPath%2A> metody.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1303: Nepředávejte literály jako lokalizované parametry](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
