---
title: 'Postupy: Vytváření fragmentů XML'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b86962221dcdeff59b1152baf7b7cddcc55293e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815393"
---
# <a name="how-to-create-xml-snippets"></a>Postupy: vytváření fragmentů kódu XML

Editor XML lze použít k vytvoření nových fragmentů kódu XML. Editor obsahuje fragment kódu XML s názvem "fragment", který je často používaný fragment pro vytváření nových fragmentů kódu XML.

## <a name="to-create-a-new-xml-snippet"></a>Vytvoření nového fragmentu kódu XML

Chcete-li vytvořit nový fragment kódu XML, vytvořte nový soubor XML a použijte funkci **Vložit fragment** kódu.

1. V nabídce **soubor** klikněte na příkaz **Nový** a pak klikněte na **soubor**.

2. Klikněte na **soubor XML** a potom klikněte na **otevřít**.

3. V podokně Editoru klikněte pravým tlačítkem myši a vyberte **Vložit fragment**.

4. Vyberte ze seznamu **fragment kódu** a stiskněte klávesu **ENTER**.

5. Proveďte všechny změny v novém fragmentu kódu.

6. V nabídce **soubor** vyberte **Uložit XMLFile.xml**.

     Zobrazí se dialogové okno **Uložit soubor jako** .

7. Zadejte název nového fragmentu a vyberte **soubory fragmentů** v rozevíracím seznamu **Uložit jako typ** .

8. Pomocí rozevíracího seznamu **Uložit v** změňte umístění souboru na složku *Moje fragmenty kódu XML Documents\Visual Studio 2005 \ Code Snippets\XML\My* a pak stiskněte **Uložit**.

## <a name="snippet-description"></a>Popis fragmentu

Tato část popisuje některé klíčové prvky ve vzorci často používaného kódu. Další informace o prvcích schématu používaných fragmenty kódu XML naleznete v tématu [reference ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>Element SnippetType

Editor podporuje dva typy fragmentů:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

`Expansion`Typ určuje, zda se má fragment kódu zobrazit při vyvolání příkazu **Vložit fragment** . `SurroundsWith`Typ určuje, zda se má fragment kódu zobrazit při vyvolání příkazu **s ohraničením** .

### <a name="code-element"></a>Element kódu

`Code`Element definuje text XML, který bude vložen při vyvolání fragmentu kódu.

> [!NOTE]
> Text fragmentu XML musí být uzavřen v `<![CDATA[...]]>` oddílu.

Následuje `Code` prvek, který je vytvořen pomocí často používaného fragmentu kódu.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

`Code`Element obsahuje tři proměnné.

- $name $ je uživatelsky definovaná proměnná. Vytvoří `name` prvek, který má upravitelnou hodnotu, která má výchozí hodnotu "Name". Uživatelsky definované proměnné jsou definovány pomocí `Literal` elementu.

- $selected $ je předdefinovaná proměnná. Představuje text, který byl vybrán v editoru XML před vyvoláním fragmentu. Umístění této proměnné určuje, kde se vybraný text zobrazí ve fragmentu kódu, který tento výběr obklopuje.

- $end $ je předdefinovaná proměnná. Když uživatel stiskne klávesu **ENTER** k dokončení úprav polí fragmentu kódu, tato proměnná Určuje, kde se kurzor (^) přesune na.

  Výše uvedený `Code` element vloží následující text XML:

```xml
<test>
  <name>name</name>
</test>
```

Hodnota elementu Name je označena jako upravitelná oblast.

### <a name="literal-element"></a>Element Literal

`Literal`Prvek slouží k identifikaci nahrazujícího textu, který lze přizpůsobit poté, co je vložen do souboru. Například literálové řetězce, číselné hodnoty a některé názvy proměnných lze deklarovat jako literály. Ve fragmentu kódu XML můžete definovat libovolný počet literálů a můžete na ně odkazovat několikrát v rámci fragmentu. Následuje příklad `Literal` prvku, který definuje $Name $ Variable, jejíž výchozí hodnota je "Name".

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

Literály mohou také odkazovat na funkce. Editor XML obsahuje funkci s názvem **LookupPrefix**. Funkce **LookupPrefix** vyhledá daný identifikátor URI oboru názvů z umístění v dokumentu XML, ze kterého je tento fragment kódu vyvolán, a vrátí předponu oboru názvů, která je definována pro daný obor názvů, pokud existuje, a obsahuje dvojtečku (:) v tomto názvu. Následuje příklad `Literal` prvku, který používá funkci **LookupPrefix** .

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

Proměnnou $prefix $ lze následně použít jinde ve fragmentu kódu XML.

## <a name="see-also"></a>Viz také

- [Fragmenty kódu XML](../xml-tools/xml-snippets.md)
- [Postupy: používání fragmentů kódu XML](../xml-tools/how-to-use-xml-snippets.md)
- [Postupy: generování fragmentu XML ze schématu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
