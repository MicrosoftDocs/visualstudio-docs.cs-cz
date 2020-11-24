---
title: Distribuce fragmentů kódu jako rozšíření
description: Naučte se používat Správce fragmentů kódu k distribuci fragmentů kódu jiným vývojářům.
ms.custom: SEO-VS-2020
ms.date: 03/21/2019
ms.topic: how-to
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
ms.openlocfilehash: 17f477fe2d02a43cef77358e862cfdf80a079ba5
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597168"
---
# <a name="how-to-distribute-code-snippets"></a>Postupy: distribuce fragmentů kódu

Vašim přátelům můžete dát fragmenty kódu a nechat je instalovat na svých vlastních počítačích pomocí **Správce fragmentů kódů**. Nicméně pokud máte několik fragmentů kódu k distribuci nebo chcete více rozšířit, můžete zahrnout soubory fragmentů do rozšíření aplikace Visual Studio. Uživatelé sady Visual Studio si pak můžou nainstalovat rozšíření a získat fragmenty.

## <a name="prerequisites"></a>Předpoklady

Nainstalujte úlohu **vývoj rozšíření sady Visual Studio** , abyste získali přístup k šablonám projektu **VSIX** .

![Úlohy vývoje rozšíření sady Visual Studio](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Nastavení rozšíření

V tomto postupu použijete stejný Hello World fragment kódu, který je vytvořen v [návodu: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md). Tento článek obsahuje kód XML fragmentu, takže se nemusíte vracet a vytvářet fragment.

1. Vytvořte nový projekt z prázdné šablony **projektu VSIX** a pojmenujte projekt **TestSnippet**.

2. V projektu **TestSnippet** přidejte nový soubor XML a zavolejte ho *VBCodeSnippet. fragment*. Nahraďte obsah následujícím kódem XML:

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

### <a name="set-up-the-directory-structure"></a>Nastavení adresářové struktury

1. V **Průzkumník řešení** vyberte uzel projektu a přidejte složku, která má název, který má fragment obsahovat ve **Správci fragmentů kódu**. V takovém případě by měl být **HelloWorldVB**.

2. Přesuňte soubor *. fragmentů* do složky *HelloWorldVB* .

3. Vyberte soubor *. fragment* v **Průzkumník řešení** a v okně **vlastnosti** se ujistěte, že je **Akce sestavení** nastavena na **obsah**, možnost **Kopírovat do výstupního adresáře** je nastavena na hodnotu **vždy kopírovat** a možnost **zahrnout do souboru VSIX** je nastavena na **hodnotu true**.

### <a name="add-the-pkgdef-file"></a>Přidat soubor. pkgdef

::: moniker range="vs-2017"

1. Do složky *HelloWorldVB* přidejte textový soubor a pojmenujte ho *HelloWorldVB. pkgdef*. Tento soubor se používá k přidání určitých klíčů do registru. V tomto případě přidá nový podklíč do klíče **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic** .

::: moniker-end

::: moniker range=">=vs-2019"

1. Do složky *HelloWorldVB* přidejte textový soubor a pojmenujte ho *HelloWorldVB. pkgdef*. Tento soubor se používá k přidání určitých klíčů do registru. V tomto případě přidá nový podklíč do klíče **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic** .

::: moniker-end

2. Do souboru přidejte následující řádky.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Pokud prohlížíte tento klíč, můžete se podívat, jak zadat různé jazyky.

3. V **Průzkumník řešení** vyberte soubor *. pkgdef* a v okně **vlastnosti** se ujistěte, že:

   - **Akce sestavení** je nastavena na **obsah**
   - **Kopírovat do výstupního adresáře** je nastaveno na **Kopírovat vždycky**
   - **Zahrnutí do VSIX** je nastavené na **hodnotu true** .

4. Přidejte soubor *. pkgdef* jako prostředek do manifestu VSIX. V souboru *source. extension. vsixmanifest* přejděte na kartu **assets (prostředky** ) a klikněte na **Nový**.

5. V dialogovém okně **Přidat nový prostředek** nastavte **typ** na **Microsoft. VisualStudio. VSPackage**, **zdroj** na **soubor v systému souborů** a **cestu** k **HelloWorldVB. pkgdef** (která by se měla objevit v rozevíracím seznamu).

### <a name="test-the-snippet"></a>Test fragmentu

1. Nyní se můžete ujistit, že fragment kódu funguje v experimentální instanci aplikace Visual Studio. Experimentální instance je druhá kopie sady Visual Studio, která je oddělená od ta, kterou používáte k psaní kódu. Umožňuje pracovat s rozšířením, aniž by to mělo vliv na vývojové prostředí.

2. Sestavte projekt a spusťte ladění.

   Zobrazí se druhá instance aplikace Visual Studio.

3. V experimentální instanci přejdete na **nástroje**  >  **Správce fragmentů kódu** a nastavte **jazyk** na **Basic**. Měli byste vidět *HelloWorldVB* jako jednu ze složek a měli byste být schopni rozbalit složku pro zobrazení fragmentu *HelloWorldVB* .

4. Otestujte fragment. V experimentální instanci otevřete Visual Basic projekt a otevřete jeden ze souborů kódu. Umístěte kurzor někam do kódu, klikněte pravým tlačítkem myši a v místní nabídce vyberte **Vložit fragment**.

5. Měli byste vidět *HelloWorldVB* jako jednu ze složek. Poklikejte na ni. Měl by se zobrazit překryvný **fragment vložení: HelloWorldVB >** , který má rozevírací seznam **HelloWorldVB**. Klikněte na rozevírací seznam **HelloWorldVB** .

   Do souboru kódu se přidá následující řádek:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)
