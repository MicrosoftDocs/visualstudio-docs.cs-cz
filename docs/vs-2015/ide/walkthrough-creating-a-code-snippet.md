---
title: 'Návod: Vytvoření fragmentu kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 038635db92d08837cc6519670053c9619ebe3c9b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267745"
---
# <a name="walkthrough-creating-a-code-snippet"></a>Návod: Vytvoření fragmentu kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragment kódu můžete vytvořit pouze v několika krocích. Všechno, co je třeba provést je vytvořit soubor XML, vyplnit odpovídající prvky a přidejte svůj kód do něj. Můžete také přidat odkazy a náhradní parametry do vašeho kódu. Fragment kódu můžete přidat k instalaci sady Visual Studio pomocí tlačítka importovat ve Správce fragmentů kódů (**nástroje/Správce fragmentů kódů**).  
  
> [!TIP]
>  Informace o snadnějším psaní fragmentů kódu snadněji vyhledat na webu CodePlex komunitní nástroje [Editor fragmentů](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## <a name="snippet-template"></a>Šablona fragmentu  
 Šablona základního fragmentu je následující:  
  
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
  
1.  Vytvořte nový soubor XML v sadě Visual Studio a přidejte šablonu uvedenou výše.  
  
2.  Vyplňte název fragmentu kódu, například "Hello World VB", do prvku název.  
  
3.  Vyplňte jazyk fragmentu kódu do atributu jazyky prvku kód. V tomto příkladu použijte "VB".  
  
4.  Přidáte nějaký kód do oddílu CDATA uvnitř prvku kód, například:  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  Výstřižek uložte jako VBCodeSnippet.snippet.  
  
### <a name="to-add-a-code-snippet-to-visual-studio"></a>Chcete-li přidat fragment kódu pro Visual Studio  
  
1.  Můžete přidat vlastní výstřižky do instalaci sady Visual Studio pomocí Správce fragmentů kódů. Otevřete Správce fragmentů kódů (**nástroje/Správce fragmentů kódů**).  
  
2.  Klikněte na tlačítko **Import** tlačítko.  
  
3.  Přejděte do umístění, kam jste uložili fragmentu kódu v předchozím postupu, vyberte ho a klikněte na tlačítko **otevřít**.  
  
4.  **Fragment kódu** otevře dialogové okno s výzvou, abyste se rozhodnete, jak přidat výstřižku z nabídky v pravém podokně. Jedna z možností by měla být **Moje fragmenty kódu**. Vyberte ho a klikněte na tlačítko **Dokončit**, pak **OK**.  
  
5.  Fragment je zkopírován do následujícího umístění:  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  Otestujte fragment otevřením projektu jazyka Visual Basic a otevřete soubor s kódem. V souboru klikněte na tlačítko **Vložit fragment** v místní nabídce pak **Moje fragmenty kódu**. Měli byste vidět fragment kódu s názvem **Můj fragment kódu jazyka Visual Basic**. Poklepejte na něj.  
  
7.  Měli byste vidět `Console.WriteLine("Hello, World!")` vložený v kódu.  
  
### <a name="adding-description-and-shortcut-fields"></a>Přidání polí popis a zástupce  
  
1.  Popisná pole poskytují další informace o fragmentech kódů při zobrazení ve Správci fragmentů kódu. Zástupce je příznak, který mohou uživatelé zadat, aby vložili váš fragment. Upravte fragment kódu přidaný otevřením souboru `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2.  Přidejte prvky Autor a popis do prvku záhlaví a vyplňte je.  
  
3.  Header element by měl vypadat přibližně takto:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  Otevřete Správce fragmentů kódů a vyberte váš fragment kódu. V pravém podokně byste měli vidět, že pole Popis a Autor jsou nyní zaplněna.  
  
5.  Chcete-li přidat zástupce, přidejte prvek zástupce spolu s Autor a popis – element:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  Uložte soubor výstřižku znovu.  
  
7.  Chcete-li otestovat zástupce, otevřete projekt jazyka Visual Basic a otevřete soubor kódu. Typ `hello` v souboru a stiskněte klávesu TAB. Kódu fragmentu musí být zařazen.  
  
### <a name="to-add-references-and-imports"></a>Přidání odkazů a importů  
  
1.  Fragmenty kódu jazyka Visual Basic můžete přidat odkaz na projekt pomocí elementu odkazy a přidat deklaraci na importy pomocí elementu importy. (Fragmenty kódu v jiných jazycích tuto funkci nemají.) Například, pokud změníte `Console.WriteLine` v příkladu kódu na `MessageBox.Show`, budete muset přidat do projektu sestavení System.Windows.Forms.dll.  
  
2.  Otevřete fragment.  
  
3.  Přidejte prvek odkazy pod prvek fragment:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  Přidejte prvek importy pod prvek fragment:  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  Změňte oddíl CDATA následujícím způsobem:  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  Uložte výstřižek.  
  
7.  Otevřete projekt jazyka Visual Basic a přidejte fragment kódu.  
  
8.  Zobrazí se příkaz importy v horní části souboru kódu:  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Podívejte se na vlastnosti projektu. Karta odkazy obsahuje odkaz na System.Windows.Forms.dll.  
  
### <a name="adding-replacements"></a>Přidání nahrazení  
  
1.  Můžete chtít, aby fragmenty kódu nahradil uživatel, například pokud přidáte proměnnou a má uživatel k nahrazení proměnné s jednou v aktuálním projektu. Můžete zadat dva druhy náhrad: literály a objekty. Literály jsou řetězce nějakého typu (řetězcové literály, názvy proměnných nebo řetězcové reprezentace číselných hodnot). Objekty jsou instancemi jiného typu než řetězce. V tomto postupu deklarovat náhradní literál a náhradní objekt a změníte kód, který na tyto náhrady odkazuje.  
  
2.  Otevřete fragment.  
  
3.  Tento příklad používá připojovací řetězec SQL, takže musíte změnit prvky importy a odkazy pro přidání příslušných odkazů:  
  
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
  
4.  Chcete-li deklarovat literální nahrazení pro připojovací řetězec SQL, přidejte prvek deklarace pod prvek fragment a do něj přidejte prvek literál s podprvky pro Identifikátor, popisek a výchozí hodnotu pro nahrazení:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  Chcete-li deklarovat nahrazení objektu pro připojení SQL, přidejte prvek objektu dovnitř prvku deklarace a přidejte podprvky pro Identifikátor, typ objektu, popisek a výchozí hodnota. Výsledný prvek deklarace by měla vypadat nějak takto:  
  
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
  
6.  V části kódu se odkazujete obklopením znaky $, například `$replacement$`:  
  
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
  
7.  Uložte výstřižek.  
  
8.  Otevřete projekt jazyka Visual Basic a přidejte fragment kódu.  
  
9. Kód by měl vypadat následovně, kde záměny `SQL connection string` a `dcConnection` jsou zvýrazněny světle oranžově. Stisknutím klávesy TAB přejděte od jednoho na druhý.  
  
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



