---
title: 'Postupy: Přizpůsobení slovníku Analýzy kódu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 190c94d70b87306ce119a2f37cf10b0f034fede9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869285"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Postupy: Přizpůsobení slovníku Analýzy kódu
Analýza kódu používá integrované slovník ke kontrole identifikátory v kódu chyby pravopisu, gramatické případ a jiné konvence pojmenování z pokynů pro rozhraní .NET Framework. Můžete vytvořit soubor Xml s vlastního slovníku na Přidat, odebrat nebo změnit podmínky, zkratky a zkratky integrované slovníku.

 Předpokládejme například, že váš kód obsažen třídu s názvem **DoorKnokker**. Analýza kódu určí název jako složený ze dvou slov: **dveře** a **knokker**. Ho pak může vygenerovat upozornění, která **knokker** nebyl zadán správně. Vynutit analýzu kódu pro rozpoznávání pravopisu, můžete přidat výraz **knokker** do vlastního slovníku.

## <a name="to-create-a-custom-dictionary"></a>Chcete-li vytvořit vlastní slovník
 Vytvořte soubor s názvem **CustomDictionary.xml**.

 Definujte vlastní slov pomocí následující struktury XML:

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Vlastní slovník elementů
 Můžete změnit chování slovníku analýzy kódu tak, že přidáte podmínky jako vnitřní text z následujících elementů ve slovníku:

- [Slovník/slova/rozpoznán nebo Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Slovník/slova/nebyl rozpoznán nebo Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Slovník/slova nebo zastaralé/termín [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Slovník/slova/složeného/termín [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Slovník/slova/DiscreteExceptions/termín](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Slovník/zkratky/CasingExceptions/zkratka](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Slovník/slova/rozpoznán nebo Word
 Aby byly termín, který v seznamu podmínek, které identifikuje analýzy kódu jako správně zadány, přidejte výraz jako vnitřní text prvku/slova/Recognized/slovo. Podmínky v elementech/slova/Recognized/slovo nerozlišují malá a velká písmena.

 **Příklad**

```
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>
```

 Podmínky v uzlech slovníku/slova/Recognized se použijí následující pravidla analýzy kódu:

-   [CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: Literály by měly být zadány správně](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Slovník/slova/nebyl rozpoznán nebo Word
 Pokud chcete vyloučit z seznam termínů, které identifikuje analýzy kódu jako správně zadány termín, přidejte výraz k vyloučení jako vnitřní text prvku/slova/Nerozpoznán/slovo. Podmínky v elementech/slova/Nerozpoznán/slovo nerozlišují malá a velká písmena.

 **Příklad**

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>
```

 Podmínky v uzlu slovníku/slova/Nerozpoznán se použijí následující pravidla analýzy kódu:

-   [CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: Literály by měly být zadány správně](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Slovník/slova nebo zastaralé/termín [@PreferredAlternate]
 Aby byly termín, který v seznamu podmínek, které identifikuje analýzy kódu jako zastaralé, přidejte výraz jako vnitřní text prvku slovníku/slova nebo zastaralé funkce nebo termín. Nepoužívané termín je slovo, které je napsaný správně, ale neměl by se používat.

 Zahrnout navrhovaný termín alternativní upozornění, zadejte alternativní v atributu PreferredAlternate prvku termín. Hodnota atributu může být prázdný, pokud nechcete navrhnout alternativu.

- Nepoužívané termín ve slovníku/slova nebo zastaralé funkce nebo termín element není malá a velká písmena.

- Hodnota atributu PreferredAlternate je velká a malá písmena. Pomocí pascalcase pro složené alternativ.

  **Příklad**

```
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>
```

 Podmínky v uzlu slovníku/slova nebo zastaralé funkce se použijí následující pravidla analýzy kódu:

-   [CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726-use-preferred-terms.md)

###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Slovník/slova/složeného/termín [@CompoundAlternate]
 Integrované slovník identifikuje termíny, které se jako jeden, diskrétní podmínky spíše než složené termín. Zahrnout termín, který seznam termínů, které identifikuje analýzy kódu jako složené slovo a zadejte správné použití malých a velkých termín, přidejte výraz jako vnitřní text prvku slovníku/slova/složeného/termín. V atributu CompoundAlternate prvku termín zadejte jednotlivá slova, které tvoří složené termín podle prvního písmena jednotlivých slov (pascalcase). Všimněte si, že výraz zadaný ve vnitřním textu je automaticky přidán do seznamu slovníku/slova/DiscreteExceptions.

- Nepoužívané termín ve slovníku/slova nebo zastaralé funkce nebo termín element není malá a velká písmena.

- Hodnota atributu PreferredAlternate je velká a malá písmena. Pomocí pascalcase pro složené alternativ.

  **Příklad**

```
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>
```

 Podmínky v uzlu slovníku/slova/složeného se použijí následující pravidla analýzy kódu:

-   [CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Slovník/slova/DiscreteExceptions/termín
 Vyloučit výraz v seznamu podmínek, které identifikuje analýzy kódu jako jedna, diskrétní slovo zaškrtnuta možnost termín je pravidly malá a velká písmena složených slov, přidejte termín jako vnitřní text prvku slovníku/slova/DiscreteExceptions/termín. Termín v elementu slovníku/slova/DiscreteExceptions/termín není malá a velká písmena.

 **Příklad**

```
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>
```

 Podmínky v uzlu slovníku/slova/DiscreteExceptions se použijí následující pravidla analýzy kódu:

-   [CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Slovník/zkratky/CasingExceptions/zkratka
 Zahrnout zkratka seznam termínů, které identifikuje analýzy kódu jako správně zadané a určit, jak se používá zkratka při termín je použití malých a pravidel pro složených slov, přidejte výraz jako vnitřní text slovníku nebo zkratky/CasingExceptions / Zkratka elementu. Zkratka v elementu slovníku nebo zkratky/CasingExceptions/zkratka rozlišuje velká a malá písmena.

 **Příklad**

```
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>
```

 Podmínky v uzlu slovníku nebo zkratky/CasingExceptions se použijí následující pravidla analýzy kódu:

-   [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Chcete-li použít vlastní slovník do projektu

1.  V **Průzkumníka řešení**, použijte jednu z následujících postupů:

2.  Přidat slovník do jednoho projektu, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **přidat existující položku**. Zadejte soubor, který v **přidat existující položku** dialogové okno.

3.  Přidat slovník, který je sdílen mezi dva nebo více projektů, vyhledejte soubor pro sdílení v **přidat existující položku** dialogového okna klikněte na šipku dolů **přidat** tlačítko a pak klikněte na **přidat jako odkaz** .

4.  V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **CustomDictionary.xml** název souboru a klikněte na tlačítko **vlastnosti**.

5.  Z **akce sestavení** seznamu vyberte **CodeAnalysisDictionary**.

6.  Z **kopírovat do výstupního adresáře** seznamu vyberte **nekopírovat**.