---
title: 'Návod: Vytvoření fragmentu kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3cf8d0cfd3119113247dedf7723e02fca9634a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662651"
---
# <a name="walkthrough-creating-a-code-snippet"></a>Návod: Vytvoření fragmentu kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragment kódu můžete vytvořit pouze s několika kroky. Vše, co potřebujete udělat, je vytvořit soubor XML, vyplnit příslušné prvky a přidat do něj svůj kód. Do kódu lze také přidat odkazy a náhradní parametry. Fragment kódu můžete přidat do instalace sady Visual Studio pomocí tlačítka importovat na Správce fragmentů kódů (**nástroje/Správce fragmentů kódů**).

> [!TIP]
> Informace o tom, jak snadněji psát fragmenty kódu, najdete na webu CodePlex, kde najdete nástroje komunity, jako je [Editor fragmentů](http://go.microsoft.com/fwlink/?LinkId=251033).

## <a name="snippet-template"></a>Šablona fragmentu
 Následuje základní šablona fragmentu kódu:

```
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
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

### <a name="to-create-a-code-snippet"></a>Vytvoření fragmentu kódu

1. Vytvořte nový soubor XML v aplikaci Visual Studio a přidejte šablonu uvedenou výše.

2. Do elementu title zadejte název fragmentu, například "Hello World VB".

3. Vyplňte jazyk fragmentu v atributu jazyky elementu Code. V tomto příkladu použijte "VB".

4. Přidejte nějaký kód do oddílu CDATA uvnitř elementu kódu, například:

    ```
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>

    ```

5. Uložte fragment kódu jako VBCodeSnippet. fragment.

### <a name="to-add-a-code-snippet-to-visual-studio"></a>Přidání fragmentu kódu do sady Visual Studio

1. Do instalace sady Visual Studio můžete přidat vlastní fragmenty pomocí Správce fragmentů kódů. Otevřete Správce fragmentů kódů (**nástroje/Správce fragmentů kódů**).

2. Klikněte na tlačítko **Import** .

3. Přejděte do umístění, kam jste uložili fragment kódu v předchozím postupu, vyberte jej a klikněte na tlačítko **otevřít**.

4. Otevře se dialogové okno **importovat fragment kódu** a požádá vás, abyste zvolili, kam se má fragment přidat z voleb v pravém podokně. Jedna z možností by měla být **Moje fragmenty kódu**. Vyberte ji a klikněte na **Dokončit**a pak na **OK**.

5. Fragment kódu je zkopírován do následujícího umístění:

     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`

6. Otestujte fragment tak, že otevřete projekt Visual Basic a otevřete soubor kódu. V souboru klikněte v místní nabídce na **Vložit fragment** a pak na **Moje fragmenty kódu**. Měl by se zobrazit fragment s názvem **můj Visual Basic fragment kódu**. Poklikejte na ni.

7. V kódu by se měla zobrazit `Console.WriteLine("Hello, World!")` vložená.

### <a name="adding-description-and-shortcut-fields"></a>Přidání polí popis a zástupce

1. Pole popisu poskytují více informací o fragmentu kódu při zobrazení ve Správci fragmentů kódu. Zástupce je značka, kterou mohou uživatelé zadat pro vložení fragmentu. Upravte fragment, který jste přidali, otevřením souboru `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.

2. Přidejte prvky Author a Description do elementu header a vyplňte je v.

3. Element Header by měl vypadat přibližně takto:

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>

    ```

4. Otevřete Správce fragmentů kódu a vyberte svůj fragment kódu. V pravém podokně byste měli vidět, že pole Popis a autor jsou teď naplněná.

5. Chcete-li přidat zástupce, přidejte prvek zástupce spolu s prvkem Author a Description:

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>

    ```

6. Uložte soubor s fragmentem kódu znovu.

7. Chcete-li zástupce otestovat, otevřete Visual Basic projekt a otevřete soubor kódu. Do souboru zadejte `hello` a stiskněte klávesu TAB. Kód fragmentu by měl být vložen.

### <a name="to-add-references-and-imports"></a>Přidání odkazů a importů

1. S Visual Basic fragmenty kódu můžete přidat odkaz na projekt pomocí elementu References a přidat deklaraci import pomocí elementu Imports. (Fragmenty v jiných jazycích tuto funkci nemají.) Například pokud změníte `Console.WriteLine` v příkladu kódu na `MessageBox.Show`, bude pravděpodobně nutné přidat do projektu sestavení System. Windows. Forms. dll.

2. Otevřete svůj fragment kódu.

3. Přidejte element References pod prvek fragmentu kódu:

    ```
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>

    ```

4. Přidejte element Imports pod prvek fragmentu kódu:

    ```
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>

    ```

5. Změňte oddíl CDATA na následující:

    ```
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6. Uložte fragment kódu.

7. Otevřete Visual Basic projekt a přidejte fragment kódu.

8. V horní části souboru kódu se zobrazí příkaz importy:

    ```
    Imports System.Windows.Forms

    ```

9. Podívejte se na vlastnosti projektu. Karta odkazy obsahuje odkaz na System. Windows. Forms. dll.

### <a name="adding-replacements"></a>Přidání nahrazení

1. Můžete chtít, aby části fragmentů kódu byly nahrazeny uživatelem, například pokud přidáte proměnnou a chcete, aby uživatel nahradil proměnnou pomocí jednoho v aktuálním projektu. Můžete zadat dva typy nahrazení: literály a objekty. Literály jsou řetězce určitého typu (řetězcové literály, názvy proměnných nebo řetězcové reprezentace číselných hodnot). Objekty jsou instancemi jiného typu než řetězce. V tomto postupu deklarujete náhradní literál a náhradu objektu a změníte kód tak, aby odkazoval na tato nahrazení.

2. Otevřete svůj fragment kódu.

3. V tomto příkladu se používá připojovací řetězec SQL, takže potřebujete změnit elementy import a odkazy pro přidání příslušných odkazů:

    ```
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

4. Chcete-li deklarovat nahrazení literálu pro připojovací řetězec SQL, přidejte element deklarace pod prvek fragmentu kódu a v něm přidejte element Literal s dílčími prvky pro ID, popis a výchozí hodnotu pro nahrazení:

    ```
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>

    ```

5. Chcete-li deklarovat nahrazení objektu pro připojení SQL, přidejte prvek Object do elementu Declarations a přidejte dílčí prvky pro ID, typ objektu, popis tlačítka a výchozí hodnotu. Výsledný element Declarations by měl vypadat takto:

    ```
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

6. V části Code (kód) odkazujete na náhrady s okolními znaménky $, například `$replacement$`:

    ```
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7. Uložte fragment kódu.

8. Otevřete Visual Basic projekt a přidejte fragment kódu.

9. Kód by měl vypadat jako následující, kde jsou náhrady `SQL connection string` a `dcConnection` zvýrazněny světle oranžová. Stisknutím klávesy TAB přejděte mezi sebou.

    ```
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection

    ```

## <a name="see-also"></a>Viz také
 [Fragmenty kódu – odkaz schématu](../ide/code-snippets-schema-reference.md)
