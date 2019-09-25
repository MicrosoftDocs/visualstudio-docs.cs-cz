---
title: 'CA1824: Označte sestavení pomocí NeutralResourcesLanguageAttribute'
ms.date: 03/29/2018
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df5c0db4e9e141e5833893bbbb447328eab8851e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233348"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Označte sestavení pomocí NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategorie|Microsoft. Performance|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Sestavení obsahuje prostředek založený na **RESX**, ale <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> nemá k němu aplikovány.

## <a name="rule-description"></a>Popis pravidla

<xref:System.Resources.NeutralResourcesLanguageAttribute> Atribut informuje správce prostředků výchozí jazykové verze aplikace. Pokud jsou prostředky výchozí jazykové verze vloženy do hlavního sestavení aplikace a <xref:System.Resources.ResourceManager> musí načítat prostředky, které patří do stejné jazykové verze jako výchozí jazyková verze <xref:System.Resources.ResourceManager> , automaticky používá prostředky nacházející se v hlavním sestavení. místo hledání satelitního sestavení. Tím se obchází obvyklá sonda sestavení, zlepšuje se výkon vyhledávání u prvního načteného prostředku a může snížit vaši pracovní sadu.

> [!TIP]
> Viz [balení a nasazení prostředků](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) pro proces, který <xref:System.Resources.ResourceManager> nástroj používá k testování souborů prostředků.

## <a name="fix-violations"></a>Opravit porušení

Chcete-li opravit porušení tohoto pravidla, přidejte atribut do sestavení a určete jazyk prostředků neutrální jazykové verze.

### <a name="to-specify-the-neutral-language-for-resources"></a>Určení neutrálního jazyka pro prostředky

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak vyberte **vlastnosti**.

2. Vyberte kartu **aplikace** a pak vyberte **informace o sestavení**.

   > [!NOTE]
   > Pokud se jedná o projekt .NET Standard nebo .NET Core, vyberte kartu **balíček** .

3. Vyberte jazyk z rozevíracího **seznamu neutrální jazyk nebo v** **neutrálním jazyce sestavení** .

4. Vyberte **OK**.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je povoleno potlačit upozornění od tohoto pravidla. Výkon při spuštění ale může zhoršit.

## <a name="see-also"></a>Viz také:

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Prostředky v aplikacích klasické pracovní plochy (.NET)](/dotnet/framework/resources/)
- [CA1703 – řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [Složená slova CA1701-Resource by měla být správně použita.](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)