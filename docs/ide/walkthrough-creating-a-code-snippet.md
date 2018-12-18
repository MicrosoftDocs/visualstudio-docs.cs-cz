---
title: 'Návod: Vytvoření fragmentu kódu'
ms.date: 10/27/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 517eb98e7ca5b32d07a4501823ca092c366e4639
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39469149"
---
# <a name="walkthrough-create-a-code-snippet"></a>Návod: Vytvoření fragmentu kódu
Fragment kódu můžete vytvořit pouze v několika krocích. Všechno, co je třeba provést je vytvořit soubor XML, vyplnit odpovídající prvky a přidejte svůj kód do něj. Můžete také přidat odkazy a náhradní parametry do vašeho kódu. Fragment kódu pro instalaci sady Visual Studio můžete přidat pomocí **Import** tlačítko **Správce fragmentů kódů** (**nástroje**  >   **Správce fragmentů kódu**).

## <a name="snippet-template"></a>Šablona fragmentu
 Šablona základního fragmentu je následující:

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

### <a name="create-a-code-snippet"></a>Vytvoření fragmentu kódu

1.  Vytvořte nový soubor XML v sadě Visual Studio a přidejte šablonu uvedenou výše.

2.  Vyplňte název fragmentu kódu, například "Hello World VB" v **název** elementu.

3.  Vyplňte jazyk fragmentu kódu do **jazyk** atribut **kód** elementu. V tomto příkladu použijte "VB".

4.  Přidat nějaký kód ve službě **CDATA** sekci **kód** prvek, například:

    ```xml
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>
    ```

5.  Uložte výstřižek jako *VBCodeSnippet.snippet*.

### <a name="add-a-code-snippet-to-visual-studio"></a>Přidání fragmentu kódu do sady Visual Studio

1.  Můžete přidat vlastní výstřižky do instalaci sady Visual Studio pomocí Správce fragmentů kódů. Otevřít **Správce fragmentů kódu** (**nástroje** > **Správce fragmentů kódu**).

2.  Klikněte na tlačítko **Import** tlačítko.

3.  Přejděte do umístění, kam jste uložili fragmentu kódu v předchozím postupu, vyberte ho a klikněte na tlačítko **otevřít**.

4.  **Fragment kódu** otevře dialogové okno s výzvou, abyste se rozhodnete, jak přidat výstřižku z nabídky v pravém podokně. Jedna z možností by měla být **Moje fragmenty kódu**. Vyberte ho a klikněte na tlačítko **Dokončit**, pak **OK**.

5.  Fragment je zkopírován do následujícího umístění:

     *%USERPROFILE%\Documents\Visual studio 2017\Code Snippets\Visual Basic\My fragmenty kódu*

6.  Otestujte fragment otevřením projektu jazyka Visual Basic a otevřete soubor s kódem. V souboru zvolte **fragmenty** > **Vložit fragment** v místní nabídce, pak **Moje fragmenty kódu**. Měli byste vidět fragment kódu s názvem **Můj fragment kódu jazyka Visual Basic**. Poklepejte na něj.

    `Console.WriteLine("Hello, World!")` je vložen do souboru kódu.

### <a name="add-description-and-shortcut-fields"></a>Přidání polí popis a zástupce

1.  Popisná pole poskytují další informace o fragmentech kódů při zobrazení ve Správci fragmentů kódu. Zástupce je příznak, který mohou uživatelé zadat, aby vložili váš fragment. Upravte fragment kódu přidaný otevřením souboru *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet*.

2.  Přidat **Autor** a **popis** prvků, které mají **záhlaví** prvek a vyplňte je.

3.  **Záhlaví** prvek by měl vypadat přibližně takto:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>
    ```

4.  Otevřít **Správce fragmentů kódů** a vyberte váš fragment kódu. V pravém podokně byste měli vidět, který **popis** a **Autor** pole jsou nyní zaplněna.

5.  Chcete-li přidat zástupce, přidejte **místní** element společně **Autor** a **popis** element:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>
    ```

6.  Uložte soubor výstřižku znovu.

7.  Chcete-li otestovat zástupce, otevřete projekt jazyka Visual Basic a otevřete soubor kódu. Typ `hello` v souboru a stiskněte klávesu **kartu** dvakrát.

    Fragment kódu vložen.

### <a name="add-references-and-imports"></a>Přidání odkazů a importů

1.  Můžete přidat odkaz na projekt pomocí **odkazy** prvek a přidat deklaraci na importy pomocí **importy** elementu. (Tento postup funguje pro jazyk C# také.) Například, pokud změníte `Console.WriteLine` v příkladu kódu na `MessageBox.Show`, budete muset přidat *System.Windows.Forms.dll* sestavení do projektu.

2.  Otevřete fragment.

3.  Přidat **odkazy** element v rámci **fragment** element:

    ```xml
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>
    ```

4.  Přidat **importy** element v rámci **fragment** element:

    ```xml
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>
    ```

5.  Změnit **CDATA** části takto:

    ```xml
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6.  Uložte výstřižek.

7.  Otevřete projekt jazyka Visual Basic a přidejte fragment kódu.

8.  Zobrazí se `Imports` příkazu v horní části souboru kódu:

    ```vb
    Imports System.Windows.Forms
    ```

9. Podívejte se na vlastnosti projektu. **Odkazy** karta obsahuje odkaz na *System.Windows.Forms.dll*.

### <a name="add-replacements"></a>Přidání nahrazení

1.  Můžete chtít, aby fragmenty kódu nahradil uživatel, například pokud přidáte proměnnou a má uživatel k nahrazení proměnné s jednou v aktuálním projektu. Můžete zadat dva druhy náhrad: literály a objekty. Literály jsou řetězce nějakého typu (řetězcové literály, názvy proměnných nebo řetězcové reprezentace číselných hodnot). Objekty jsou instancemi jiného typu než řetězce. V tomto postupu deklarovat náhradní literál a náhradní objekt a změníte kód, který na tyto náhrady odkazuje.

2.  Otevřete fragment.

3.  Tento příklad používá připojovací řetězec SQL, takže budete muset změnit **importy** a **odkazy** prvky pro přidání příslušných odkazů:

    ```xml
    <References>
        <Reference>
            <Assembly>System.Data.dll</Assembly>
        </Reference>
        <Reference>
            <Assembly>System.Xml.dll</Assembly>
        </Reference>
    </References>
    <Imports>
        <Import>
            <Namespace>System.Data</Namespace>
        </Import>
        <Import>
            <Namespace>System.Data.SqlClient</Namespace>
        </Import>
    </Imports>
    ```

4.  Chcete-li deklarovat literální nahrazení pro připojovací řetězec SQL, přidejte **deklarace** element v rámci **fragment** elementu a do něj přidejte **literálu** element s podprvky pro Identifikátor, popisek a výchozí hodnotu pro nahrazení:

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>
    ```

5.  Chcete-li deklarovat nahrazení objektu pro připojení SQL, přidejte **objekt** element v rámci **deklarace** prvek a přidejte podprvky pro Identifikátor, typ objektu, popisek a výchozí hodnota hodnota. Výsledná **deklarace** prvek by měl vypadat takto:

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
        <Object>
            <ID>SqlConnection</ID>
            <Type>System.Data.SqlClient.SqlConnection</Type>
            <ToolTip>Replace with a connection object in your application.</ToolTip>
            <Default>dcConnection</Default>
        </Object>
    </Declarations>
    ```

6.  V části kódu se odkazujete obklopením znaky $, například `$replacement$`:

    ```xml
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7.  Uložte výstřižek.

8.  Otevřete projekt jazyka Visual Basic a přidejte fragment kódu.

9. Kód by měl vypadat následovně, kde záměny `SQL connection string` a `dcConnection` jsou zvýrazněny světle oranžově. Zvolte **kartu** přejděte od jednoho na druhý.

    ```vb
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection
    ```

## <a name="see-also"></a>Viz také:

- [Referenční informace ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)