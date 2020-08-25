---
title: 'Návod: Vytvoření fragmentu kódu'
ms.date: 03/31/2020
ms.topic: how-to
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 46744decddcc2d50fd05ea86cc6ebfad9d210031
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800499"
---
# <a name="walkthrough-create-a-code-snippet"></a>Návod: Vytvoření fragmentu kódu

Fragment kódu můžete vytvořit pouze s několika kroky. Vše, co potřebujete udělat, je vytvořit soubor XML, vyplnit příslušné prvky a přidat do něj svůj kód. Volitelně můžete využít náhradní parametry a odkazy na projekt. Importujte fragment kódu do instalace sady Visual Studio pomocí tlačítka **importovat** ve **Správci fragmentů kódů** (**nástroje**  >  **Správce fragmentů kódů**).

## <a name="snippet-template"></a>Šablona fragmentu

Následující kód XML je základní šablona fragmentu:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>Vytvoření fragmentu kódu

1. Vytvořte nový soubor XML v aplikaci Visual Studio a přidejte šablonu uvedenou výše.

2. Vyplňte název fragmentu v prvku **Nadpis** . Použijte název **druhé**odmocniny.

3. Vyplňte jazyk fragmentu v atributu **Language** elementu **Code** . Pro jazyk C# použijte **CSharp**, pro Visual Basic použijte **VB**a pro C++ použijte **cpp**.

   > [!TIP]
   > Chcete-li zobrazit všechny dostupné jazykové hodnoty, Projděte si [část atributy elementu kódu](code-snippets-schema-reference.md#attributes) na [referenční stránce schématu fragmenty kódu](code-snippets-schema-reference.md) .

4. Přidejte kód fragmentu do oddílu **CDATA** uvnitř elementu **kódu** .

   Pro C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Nebo pro Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > Nelze určit, jak mají být řádky kódu v oddílu **CDATA** fragment kódu odsazeny nebo formátovány. Po vložení služba jazyka automaticky zformátuje vložený kód.

5. Uložte fragment kódu jako *SquareRoot. fragment* (můžete ho uložit kdekoli).

## <a name="import-a-code-snippet"></a>Import fragmentu kódu

1. Fragment kódu můžete do instalace sady Visual Studio importovat pomocí **Správce fragmentů kódů**. Otevřete ho tak, že kliknete na **nástroje**  >  **Správce fragmentů kódů**.

2. Klikněte na tlačítko **Import** .

3. Přejděte do umístění, kam jste uložili fragment kódu v předchozím postupu, vyberte jej a klikněte na tlačítko **otevřít**.

4. Otevře se dialogové okno **importovat fragment kódu** a požádá vás, abyste zvolili, kam se má fragment přidat z voleb v pravém podokně. Jedna z možností by měla být **Moje fragmenty kódu**. Vyberte ji a klikněte na **Dokončit**a pak na **OK**.

5. Fragment kódu je zkopírován do jednoho z následujících umístění v závislosti na jazyku kódu:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017 \ Code Snippets\Visual C# \My – fragmenty kódu*  
   *%USERPROFILE%\Documents\Visual Studio 2017 \ Code Snippets\Visual Basic\My – fragmenty kódu*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019 \ Code Snippets\Visual C# \My – fragmenty kódu*  
   *%USERPROFILE%\Documents\Visual Studio 2019 \ Code Snippets\Visual Basic\My fragmenty kódu*

   ::: moniker-end

6. Otestujte fragment tak, že otevřete projekt v jazyce C# nebo Visual Basic. Se souborem kódu otevřeným v editoru zvolte **fragmenty**  >  **vložení fragmentu** z nabídky po kliknutí pravým tlačítkem myši a pak **Moje fragmenty kódu**. Měl by se zobrazit fragment nazvaný **odmocnina**. Poklikejte na ni.

   Kód fragmentu je vložen do souboru kódu.

## <a name="description-and-shortcut-fields"></a>Pole Popis a zástupce

::: moniker range="vs-2017"

1. Pole popisu poskytují více informací o fragmentu kódu při zobrazení ve Správci fragmentů kódu. Zástupce je značka, kterou mohou uživatelé zadat pro vložení fragmentu. Upravte fragment, který jste přidali, otevřením souboru *%UserProfile%\Documents\Visual Studio 2017 \ fragmenty kódu \\ [Visual C# nebo Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Pole popisu poskytují více informací o fragmentu kódu při zobrazení ve Správci fragmentů kódu. Zástupce je značka, kterou mohou uživatelé zadat pro vložení fragmentu. Upravte fragment, který jste přidali, otevřením souboru *%UserProfile%\Documents\Visual Studio 2019 \ fragmenty kódu \\ [Visual C# nebo Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Vzhledem k tomu, že upravujete soubor v adresáři, ve kterém je umístěn v aplikaci Visual Studio, nemusíte ho znovu naimportovat do sady Visual Studio.

2. Přidejte prvky **Author** a **Description** do elementu **header** a vyplňte je v.

3. Element **header** by měl vypadat přibližně takto:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Otevřete **Správce fragmentů kódu** a vyberte svůj fragment kódu. V pravém podokně si všimněte, že pole **Popis** a **Autor** jsou nyní vyplněna.

   ![Popis fragmentu kódu ve Správci fragmentů kódu](media/code-snippet-description-author.png)

5. Chcete-li přidat zástupce, přidejte prvek **zástupce** v rámci elementu **header** :

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Uložte soubor s fragmentem kódu znovu.

7. Chcete-li zástupce otestovat, otevřete projekt, který jste použili dříve, v editoru zadejte **Sqrt** a stiskněte klávesu **TAB** (jednou pro Visual Basic, dvakrát pro C#).

   Kód fragmentu je vložen.

## <a name="replacement-parameters"></a>Parametry nahrazení

Možná budete chtít, aby části fragmentu kódu byly nahrazeny uživatelem. Například může být vhodné, aby uživatel nahradil název proměnné v aktuálním projektu jako jeden. Můžete zadat dva typy nahrazení: literály a objekty. Použijte [element Literal](code-snippets-schema-reference.md#literal-element) k identifikaci náhrady pro část kódu, která je zcela obsažena v rámci fragmentu, ale bude pravděpodobně upravena poté, co je vložena do kódu (například řetězec nebo číselná hodnota). Pomocí [elementu Object](code-snippets-schema-reference.md#object-element) Identifikujte položku, která je požadována fragmentem kódu, ale je pravděpodobně definována mimo samotný fragment (například instance objektu nebo ovládací prvek).

1. Chcete-li uživateli povolit snadné nahrazení čísla pro výpočet čtvercové odmocniny, upravte prvek **fragment** souboru *SquareRoot. fragmentu* následujícím způsobem:

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Všimněte si, že nahrazení literálu je přiděleno IDENTIFIKÁTORu ( `Number` ). Na toto ID se odkazuje v rámci fragmentu kódu tím, že ho obklopují `$` znaky:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Uložte soubor fragmentu.

3. Otevřete projekt a vložte fragment kódu.

   Fragment kódu je vložen a upravitelný literál je zvýrazněn pro nahrazení. Pokud chcete zobrazit popis hodnoty, najeďte myší na náhradní parametr.

   ![Popis náhradního parametru fragmentu kódu v aplikaci Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > V případě, že fragment kódu obsahuje více než jeden parametr, můžete změnit hodnoty stisknutím klávesy **TAB** a přejít z jedné na druhou.

## <a name="import-a-namespace"></a>Import oboru názvů

Fragment kódu můžete použít k přidání `using` direktivy (C#) nebo `Imports` příkazu (Visual Basic) zahrnutím [elementu Imports](code-snippets-schema-reference.md#imports-element). Pro .NET Framework projekty lze také přidat odkaz na projekt pomocí [elementu REFERENCES](code-snippets-schema-reference.md#references-element).

Následující kód XML ukazuje fragment kódu, který používá metodu `File.Exists` v oboru názvů System.IO, a proto definuje prvek **Imports** pro import oboru názvů System.IO.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Viz také

- [Referenční informace ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)
