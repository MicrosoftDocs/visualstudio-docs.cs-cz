---
title: 'CA1704: Identifikátory by měly být zadány správně'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 710e18f4ce8199c76c34683c510d3a64160544e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916895"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Identifikátory by měly být zadány správně

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Kategorie|Microsoft.Naming|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Název identifikátoru obsahuje jeden nebo více slova, která nerozpoznal kontrola pravopisu knihovně společnosti Microsoft. Toto pravidlo není zkontrolujte konstruktory nebo s názvem zvláštní členy například get a nastavte vlastnosti přistupující objekty.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo analyzuje identifikátor do tokenů a kontroluje, zda každý token. Analýza algoritmus provádí následující transformace:

- Velká písmena spusťte nový token. Například MyNameIsJoe tokenizes "My", "Name", "Je", "Jan".

- Několik velkých písmen spustí poslední velké písmeno nový token. Například GUIEditor tokenizes k "Grafickým uživatelským rozhraním", "Editor".

- Úvodní a koncové apostrofy se odeberou. Například 'odesílatele' tokenizes "odesílateli".

- Podtržítka označují konec token a jsou odebrány. Například Hello_world tokenizes na text "Hello", "world".

- Vložené ampersandy se odeberou. Například pro & mat tokenizes k "format".

## <a name="language"></a>Jazyk

Kontrola pravopisu kontroluje aktuálně jen pro jazykovou verzi na základě angličtina slovník. Jazyková verze projektu v souboru projektu, můžete změnit tak, že přidáte **CodeAnalysisCulture** element.

Příklad:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Pokud nastavíte jazykovou verzi na jakoukoli jinou hodnotu než jazykovou verzi na základě angličtina, je tato pravidel nástroje Analýza kódu bezobslužně zakázané.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení toto pravidlo, opravte pravopis aplikace word nebo přidat slovo do slovníku.

### <a name="to-add-words-to-a-custom-dictionary"></a>Chcete-li přidat slova do slovníku

Název souboru XML vlastní slovník *CustomDictionary.xml*. Umístěte slovníku v instalačním adresáři nástroje adresáři projektu nebo v adresáři, který je přidružen nástroj v profilu uživatele (*%USERPROFILE%\Application\\...* ). Zjistěte, jak přidat vlastní slovník na projekt v sadě Visual Studio, najdete v tématu [postupy: přizpůsobení slovníku analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Přidejte slova, která by nemělo způsobit narušení ve slovníku nebo slova nebo Recognized cestě.

- Přidejte slova, která by nemělo způsobit narušení v cestě slovník nebo slova nebo Nerozpoznán.

- Přidejte slova, která by měla být označené jako zastaralé v cestě slovník nebo slova nebo zastaralé. Podívejte se na téma související pravidlo [CA1726: použijte upřednostňované výrazy](../code-quality/ca1726-use-preferred-terms.md) Další informace.

- Přidáte výjimky pravidla velká a malá písmena zkratku do slovníku nebo režim/CasingExceptions cesty.

Následuje příklad struktury vlastní slovník souboru:

```xml
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Při potlačení upozornění

Potlačíte upozornění na toto pravidlo pouze v případě, že je slovo záměrně překlepu a slovo platí pro omezenou sadu knihovny. Správně hláskovaným slova redukovat křivku vyžadovanou pro nové knihovny softwaru.

## <a name="related-rules"></a>Související pravidla

- [CA2204: Literály by měly být zadány správně](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Viz také

- [Postupy: Přizpůsobení slovníku Analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
