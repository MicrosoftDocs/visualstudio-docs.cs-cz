---
title: 'CA1704: identifikátory by měly být zadány správně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5e078fc1bb7fe247d541e7695e98c2de76c2466
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544063"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Identifikátory by měly být zadány správně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Název identifikátoru obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala. Toto pravidlo nekontroluje konstruktory nebo členy se speciálním jménem, jako jsou například GET a Set Access Property.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo analyzuje identifikátor na tokeny a kontroluje pravopis každého tokenu. Algoritmus analýzy provádí následující transformace:

- Velká písmena zahájí nový token. Například MyNameIsJoe tokenizes na "my", "Name", "is", "Jana".

- U více velkých písmen začíná poslední velké písmeno novému tokenu. Například GUIEditor tokenizes na "GUI", "Editor".

- Úvodní a koncové apostrofy jsou odebrány. Například "Sender" tokenizes na "Sender".

- Podtržítka označují konec tokenu a jsou odebrána. Například Hello_world tokenizes na "Hello", "World".

- Vložené ampersandy se odeberou. Například pro&mat tokenizes do formátu "Format".

  Ve výchozím nastavení se používá anglická (EN) verze kontroly pravopisu. Žádné jiné jazykové slovníky nejsou aktuálně k dispozici.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, opravte pravopis slova nebo přidejte slovo do vlastního slovníku s názvem CustomDictionary.xml. Umístěte slovník do instalačního adresáře nástroje, adresáře projektu nebo v adresáři, který je přidružen k nástroji v rámci profilu uživatele (%USERPROFILE%\Application data \\ ...). Informace o tom, jak přidat vlastní slovník do projektu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , naleznete v tématu [How to: Customize a Code Analysis Dictionary.](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Přidejte slova, která by neměla způsobovat porušení v rámci slovníku/slov/rozpoznané cesty.

- Přidejte slova, která by měla způsobit porušení v rámci slovníku/slov/nerozpoznaná cesta.

- Přidejte slova, která by měla být označena příznakem jako zastaralá v cestě Dictionary/Word/zastaralá cesta. Další informace najdete v tématu související pravidlo [CA1726: použijte preferované výrazy](../code-quality/ca1726-use-preferred-terms.md).

- Do slovníku/akronymy/CasingExceptions cesty přidejte výjimky do pravidel pro velká a malá písmena.

  Následuje příklad struktury souboru vlastního slovníku.

```
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

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla pouze v případě, že je slovo úmyslně špatně napsané a slovo se vztahuje na omezené sady knihovny. Správná pravopisná slova omezují výukovou křivku, která je požadována pro nové knihovny softwaru.

## <a name="related-rules"></a>Související pravidla
 [CA2204: Literály by měly být zadány správně](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Viz také
 [Postupy: Přizpůsobení slovníku Analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
