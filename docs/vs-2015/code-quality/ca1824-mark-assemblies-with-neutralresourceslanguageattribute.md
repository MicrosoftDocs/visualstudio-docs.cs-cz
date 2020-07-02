---
title: 'CA1824: Označte sestavení pomocí atribut NeutralResourcesLanguageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19077a63d5aa22bda3f968943703a82488e2745d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545285"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Označte sestavení pomocí NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Sestavení obsahuje prostředek založený na **RESX**, ale nemá <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> k němu aplikovány.

## <a name="rule-description"></a>Popis pravidla
 Atribut **NeutralResourcesLanguage** informuje **Správce prostředků** jazyka, který se použil k zobrazení prostředků neutrální jazykové verze pro sestavení. Při vyhledávání prostředků ve stejné jazykové verzi jako jazyk neutrálních prostředků použije **správce** prostředků automaticky prostředky, které jsou umístěny v hlavním sestavení. Místo toho je třeba hledat satelitní sestavení, které má aktuální jazykovou verzi uživatelského rozhraní pro aktuální vlákno. To zlepšuje výkon vyhledávání při prvním získání prostředků a může zmenšit vaši pracovní sadu.

## <a name="fixing-violations"></a>Oprava porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte atribut do sestavení a určete jazyk prostředků neutrální jazykové verze.

## <a name="specifying-the-language"></a>Určení jazyka

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Určení jazyka prostředku neutrální jazykové verze

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak klikněte na **vlastnosti**.

2. V levém navigačním panelu vyberte **aplikace**a pak klikněte na **informace o sestavení**.

3. V dialogovém okně **informace o sestavení** vyberte jazyk z rozevíracího seznamu **neutrální jazyk** .

4. Klikněte na **OK**.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je povoleno potlačit upozornění od tohoto pravidla. Výkon při spuštění se ale může snížit.
