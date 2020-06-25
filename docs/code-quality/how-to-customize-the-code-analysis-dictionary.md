---
title: 'Postupy: Přizpůsobení slovníku Analýzy kódu'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01c3ad83cea8dc1a28a817677be102c87ebc8f87
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371869"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Postupy: Přizpůsobení slovníku Analýzy kódu

Analýza kódu používá integrovaný slovník ke kontrole identifikátorů ve vašem kódu pro chyby v pravopisu, gramatickém případu a dalších konvencích pojmenovávání pokynů pro návrh .NET. Soubor XML vlastního slovníku můžete vytvořit tak, že přidáte, odeberete nebo upravíte výrazy, zkratky a zkratky do integrovaného slovníku.

Předpokládejme například, že váš kód obsahuje třídu s názvem **DoorKnokker**. Analýza kódu identifikuje název jako složený ze dvou slov: **dveří** a **knokker**. Vyvolalo upozornění, že **knokker** nebyl správně zadán. Chcete-li vynutit analýzu kódu pro rozpoznání pravopisu, můžete přidat pojem **knokker** do vlastního slovníku.

## <a name="to-create-a-custom-dictionary"></a>Vytvoření vlastního slovníku

Vytvořte soubor s názvem **CustomDictionary.xml**.

Pomocí následující struktury XML definujte vlastní slova:

```xml
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

## <a name="custom-dictionary-elements"></a>Vlastní prvky slovníku

Chování slovníku analýzy kódu můžete upravit přidáním podmínek jako vnitřní text následujících prvků ve vlastním slovníku:

- [Slovník/slova/rozpoznané/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Slovník/slova/Nerozpoznáno/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Slovníky/slova/zastaralé/termín [ @PreferredAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Slovníky/slova/složené/Term [ @CompoundAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Slovník/slova/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Slovníky/akronymy/CasingExceptions/akronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="dictionarywordsrecognizedword"></a><a name="BKMK_DictionaryWordsRecognizedWord"></a>Slovník/slova/rozpoznané/Word

Chcete-li zahrnout termín v seznamu podmínek, které analýza kódu identifikuje jako správně napsaný, přidejte termín jako vnitřní text slovníku/slov/rozpoznaný/wordový prvek. Výrazy ve slovníku/slovech/rozpoznaných/slovních prvcích nerozlišují velká a malá písmena.

**Příklad**

```xml
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

Podmínky v Slovníkech, slovech a rozpoznaných uzlech jsou aplikovány na následující pravidla analýzy kódu:

- [CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně](../code-quality/ca1701.md)

- [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702.md)

- [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703.md)

- [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704.md)

- [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709.md)

- [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726.md)

- [CA2204: Literály by měly být zadány správně](../code-quality/ca2204.md)

### <a name="dictionarywordsunrecognizedword"></a><a name="BKMK_DictionaryWordsUnrecognizedWord"></a>Slovník/slova/Nerozpoznáno/Word

Chcete-li vyloučit období ze seznamu podmínek, které analýza kódu identifikuje jako správně napsaný, přidejte termín, který má být vyloučen jako vnitřní text slovníku/slov/nerozpoznaný/textový prvek. Výrazy ve slovníku/slovech/nerozpoznané/wordové elementy nerozlišují velká a malá písmena.

**Příklad**

```xml
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

Termíny v poli Dictionary/Word/nerozpoznaný uzel jsou aplikovány na následující pravidla analýzy kódu:

- [CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně](../code-quality/ca1701.md)

- [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702.md)

- [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703.md)

- [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704.md)

- [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709.md)

- [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726.md)

- [CA2204: Literály by měly být zadány správně](../code-quality/ca2204.md)

### <a name="dictionarywordsdeprecatedtermpreferredalternate"></a><a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>Slovníky/slova/zastaralé/termín [ @PreferredAlternate ]

Chcete-li zahrnout výraz do seznamu podmínek, které analýza kódu identifikuje jako zastaralou, přidejte termín jako vnitřní text slovníku/slov/zastaralé nebo termín elementu. Vyřazeným termínem je slovo, které je napsané správně, ale nemělo by se používat.

Chcete-li do upozornění zahrnout navrhovaný alternativní termín, zadejte alternativu v atributu PreferredAlternate Term elementu. Hodnotu atributu můžete nechat prázdnou, pokud nechcete navrhovat alternativu.

- Nepoužívané období ve slovníku/slovech/v nepoužívaném nebo termínovém prvku nerozlišuje velká a malá písmena.

- Hodnota atributu PreferredAlternate rozlišuje velká a malá písmena. Pro složené alternativy použijte velká písmena jazyka Pascal.

**Příklad**

```xml
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

Podmínky v rámci slovníku/slov/zastaralých uzlů jsou aplikovány na následující pravidla analýzy kódu:

- [CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně](../code-quality/ca1701.md)

- [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702.md)

- [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703.md)

- [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704.md)

- [CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726.md)

### <a name="dictionarywordscompoundtermcompoundalternate"></a><a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>Slovníky/slova/složené/Term [ @CompoundAlternate ]

Vestavěný slovník identifikuje některé podmínky jako jednoduché, diskrétní podmínky a nikoli složený výraz. Chcete-li zahrnout výraz do seznamu podmínek, které analýza kódu identifikuje jako složené slovo, a určit správná velká a malá písmena, přidejte termín jako vnitřní text slovníku/slov/složeného/Term elementu. V atributu CompoundAlternate elementu Term určete jednotlivá slova, která tvoří složený výraz, a to tak, že se první písmeno jednotlivých slov (malý případ) odvede na velká písmena. Všimněte si, že termín zadaný ve vnitřním textu je automaticky přidán do seznamu slovníky/slova/DiscreteExceptions.

- Složený výraz v rámci slovníku/slov/složené/Term elementu nerozlišuje velká a malá písmena.

- Hodnota atributu CompoundAlternate rozlišuje velká a malá písmena. Pro složené alternativy použijte velká písmena jazyka Pascal.

**Příklad**

```xml
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

Termíny v poli Dictionary/Word/složený uzel jsou aplikovány na následující pravidla analýzy kódu:

- [CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně](../code-quality/ca1701.md)

- [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702.md)

- [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703.md)

- [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704.md)

### <a name="dictionarywordsdiscreteexceptionsterm"></a><a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>Slovník/slova/DiscreteExceptions/Term

Chcete-li vyloučit termín v seznamu podmínek, které analýza kódu identifikuje jako samostatné slovo, když je výraz kontrolován pravidly pro všechna velká písmena pro složená slova, přidejte termín jako vnitřní text slovníku/slov/DiscreteExceptions/Term elementu. Termín v prvku Dictionary/Word/DiscreteExceptions/Term nerozlišuje velká a malá písmena.

**Příklad**

```xml
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

Podmínky v uzlu Dictionary/Word/DiscreteExceptions jsou aplikovány na následující pravidla analýzy kódu:

- [CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně](../code-quality/ca1701.md)

- [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702.md)

### <a name="dictionaryacronymscasingexceptionsacronym"></a><a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>Slovníky/akronymy/CasingExceptions/akronym

Chcete-li zahrnout akronym do seznamu podmínek, které analýza kódu identifikuje jako správně napsaný a který označuje, jak akronym, pokud je výraz kontrolován pravidly pro všechna velká písmena pro složená slova, přidejte termín jako vnitřní text prvku Dictionary/Akronyms/CasingExceptions/akronym. Akronym v prvku Dictionary/Akronyms/CasingExceptions/akronym rozlišuje velká a malá písmena.

**Příklad**

```xml
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

Podmínky v uzlu Dictionary/Akronyms/CasingExceptions jsou aplikovány na následující pravidla analýzy kódu:

- [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709.md)

## <a name="to-apply-a-custom-dictionary-to-a-project"></a><a name="BKMK_ToApplyACustomDictionaryToAProject"></a>Použití vlastního slovníku na projekt

1. V **Průzkumník řešení**použijte jeden z následujících postupů:

2. Chcete-li přidat slovník do jednoho projektu, klikněte pravým tlačítkem myši na název projektu a pak klikněte na položku **Přidat existující položku**. Zadejte soubor v dialogovém okně **Přidat existující položku** .

3. Chcete-li přidat slovník, který je sdílen mezi dvěma nebo více projekty, vyhledejte soubor pro sdílení v dialogovém okně **Přidat existující položku** , klikněte na šipku dolů na tlačítku **Přidat** a potom klikněte na tlačítko **Přidat jako odkaz**.

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název souboru **CustomDictionary.xml** a klikněte na **vlastnosti**.

5. V seznamu **Akce sestavení** vyberte možnost **CodeAnalysisDictionary**.

6. V seznamu **Kopírovat do výstupního adresáře** vyberte **Nekopírovat**.
