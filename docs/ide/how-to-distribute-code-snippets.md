---
title: Distribuce fragmentů kódu jako rozšíření
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 23e77658b2b09f643af18a3f136f5428828cfb5c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591057"
---
# <a name="how-to-distribute-code-snippets"></a>Postup: Distribuce fragmentů kódu

Úryvky kódu můžete dát svým přátelům a nechat je nainstalovat úryvky do vlastních počítačů pomocí **Správce fragmentů kódu**. Pokud však máte několik úryvků k distribuci nebo je chcete distribuovat v širším měřítku, můžete soubory výstřižků zahrnout do rozšíření sady Visual Studio. Uživatelé sady Visual Studio pak můžete nainstalovat rozšíření získat výstřižky.

## <a name="prerequisites"></a>Požadavky

Nainstalujte **zatížení vývoje rozšíření Visual Studio,** abyste získali přístup k šablonám projektu **VSIX Project.**

![Pracovní vytížení rozšíření Visual Studio](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Nastavení rozšíření

V tomto postupu použijete stejný fragment kódu Hello World, který je vytvořen v [návodu: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md). Tento článek obsahuje úryvek XML, takže se nemusíte vracet a vytvářet úryvek.

1. Vytvořte nový projekt ze šablony **Prázdný projekt VSIX** a pojmenujte projekt **TestSnippet**.

2. V projektu **TestSnippet** přidejte nový soubor XML a nazvěte jej *VBCodeSnippet.snippet*. Nahraďte obsah následujícím xml:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeSnippets
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
      <CodeSnippet Format="1.0.0">
        <Header>
          <Title>Hello World VB</Title>
          <Shortcut>HelloWorld</Shortcut>
          <Description>Inserts code</Description>
          <Author>MSIT</Author>
          <SnippetTypes>
            <SnippetType>Expansion</SnippetType>
            <SnippetType>SurroundsWith</SnippetType>
          </SnippetTypes>
        </Header>
        <Snippet>
          <Code Language="VB">
            <![CDATA[Console.WriteLine("Hello, World!")]]>
          </Code>
        </Snippet>
      </CodeSnippet>
    </CodeSnippets>
    ```

### <a name="set-up-the-directory-structure"></a>Nastavení struktury adresáře

1. V **Průzkumníku řešení**vyberte uzel projektu a přidejte složku s názvem, který má mít výstřižek ve **Správci výstřižků kódu**. V tomto případě by měl být **HelloWorldVB**.

2. Přesuňte soubor *.snippet* do složky *HelloWorldVB.*

3. V Průzkumníku **řešení**vyberte soubor *.snippet* a v okně **Vlastnosti** **zkontrolujte,** zda je akce sestavení **nastavena**na obsah , **je možnost Kopírovat do výstupního adresáře** **nastavena**na Kopírovat vždy a **Zahrnout do pole VSIX** je nastavena na **hodnotu true**.

### <a name="add-the-pkgdef-file"></a>Přidání souboru .pkgdef

::: moniker range="vs-2017"

1. Přidejte textový soubor do složky *HelloWorldVB* a pojmenujte jej *HelloWorldVB.pkgdef*. Tento soubor se používá k přidání určitých klíčů do registru. V takovém případě přidá nový podklíč ke **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Přidejte textový soubor do složky *HelloWorldVB* a pojmenujte jej *HelloWorldVB.pkgdef*. Tento soubor se používá k přidání určitých klíčů do registru. V takovém případě přidá nový podklíč ke klíči **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic.**

::: moniker-end

2. Přidejte do souboru následující řádky.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Pokud zkontrolujete tento klíč, můžete vidět, jak zadat různé jazyky.

3. Vprůzkumníka **řešení**vyberte soubor *.pkgdef* a v okně **Vlastnosti** se ujistěte, že:

   - **Akce sestavení** je nastavena na **obsah**
   - **Kopírovat do výstupního adresáře** je nastaveno na **Kopírovat vždy**
   - **Zahrnout do VSIX** je nastavena na **hodnotu true**

4. Přidejte soubor *.pkgdef* jako datový zdroj v manifestu VSIX. V souboru *source.extension.vsixmanifest* přejděte na kartu **Datové zdroje** a klepněte na tlačítko **Nový**.

5. V dialogovém okně **Přidat nový datový zdroj** nastavte **typ** na **Microsoft.VisualStudio.VsPackage**, **zdroj** do **souboru v souborovém systému**a **cestu** k **HelloWorldVB.pkgdef** (která by se měla zobrazit v rozevíracím seznamu).

### <a name="test-the-snippet"></a>Testování úryvku

1. Nyní se můžete ujistit, že fragment kódu funguje v experimentální instanci sady Visual Studio. Experimentální instance je druhá kopie sady Visual Studio, která je oddělená od té, kterou používáte k psaní kódu. Umožňuje pracovat na rozšíření bez ovlivnění vývojového prostředí.

2. Sestavení projektu a začít ladění.

   Zobrazí se druhá instance sady Visual Studio.

3. V experimentální instanci přejděte do**Správce výstřižků kódu** **nástrojů** > a nastavte **jazyk** na **základní**. Měli byste vidět *HelloWorldVB* jako jednu ze složek a měli byste být schopni rozbalit složku, abyste viděli úryvek *HelloWorldVB.*

4. Otestujte úryvek. V experimentální instanci otevřete projekt jazyka Visual Basic a otevřete jeden ze souborů kódu. Umístěte kurzor někam do kódu, klikněte pravým tlačítkem myši a v místní nabídce vyberte **Vložit úryvek**.

5. Měli byste vidět *HelloWorldVB* jako jednu ze složek. Poklepejte na něj. Měli byste vidět pop-up **Vložit úryvek: HelloWorldVB >,** který má rozbalovací **HelloWorldVB**. Klikněte na rozbalovací seznam **HelloWorldVB.**

   Do souboru kódu je přidán následující řádek:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)
