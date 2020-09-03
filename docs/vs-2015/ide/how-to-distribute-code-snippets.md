---
title: 'Postupy: distribuce fragmentů kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1a692ee29ea9d43e1a0a4fbed5c52934d69256d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476984"
---
# <a name="how-to-distribute-code-snippets"></a>Postupy: Distribuce fragmentů kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete jednoduše poskytnout vašim přátelům fragmenty kódu a nechat je nainstalovat do svých vlastních počítačů pomocí Správce fragmentů kódů. Nicméně pokud máte několik fragmentů kódu k distribuci nebo chcete více rozšířit, zahrnete soubor s fragmenty do rozšíření sady Visual Studio, které mohou instalovat uživatelé sady Visual Studio.

 Aby bylo možné vytvořit rozšíření sady Visual Studio, je nutné nainstalovat sadu Visual Studio SDK. Vyhledejte verzi VSSDK, která odpovídá vaší instalaci sady Visual Studio, na webu [Visual studio 2015 ke stažení](https://visualstudio.microsoft.com/vs/older-downloads/).

## <a name="setting-up-the-extension"></a>Nastavení rozšíření
 V tomto postupu použijeme stejný fragment kódu Hello World vytvořený v [návodu: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md). Budeme poskytovat text. fragment, takže nemusíte se vracet a vytvořit ho.

1. Vytvořte nový projekt VSIX s názvem **TestSnippet**. (**Soubor/nový/projekt/Visual C# (nebo Visual Basic/rozšiřitelnost**)

2. V projektu **TestSnippet** přidejte nový soubor XML a zavolejte ho **VBCodeSnippet. fragment**. Nahraďte obsah následujícím:

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

#### <a name="setting-up-the-directory-structure"></a>Nastavení adresářové struktury

1. V Průzkumník řešení vyberte uzel projektu a přidejte složku, která má název, který má fragment obsahovat ve Správci fragmentů kódu. V takovém případě by měl být **HelloWorldVB**.

2. Přesuňte soubor. fragmentů do složky **HelloWorldVB** .

3. Vyberte soubor. fragmentů v Průzkumník řešení a v okně **vlastnosti** se ujistěte, že je **Akce sestavení** nastavena na **obsah**, možnost **Kopírovat do výstupního adresáře** je nastavena na hodnotu **vždy kopírovat**a možnost **zahrnout do souboru VSIX** je nastavena na **hodnotu true**.

#### <a name="adding-the-pkgdef-file"></a>Přidání souboru. pkgdef

1. Do složky **HelloWorldVB** přidejte textový soubor a pojmenujte ho **HelloWorldVB. pkgdef**. Tento soubor se používá k přidání určitých klíčů do registru. V takovém případě přidá nový klíč do

     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic**.

2. Do souboru přidejte následující řádky.

    ```
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

     Pokud prohlížíte tento klíč, můžete se podívat, jak zadat různé jazyky.

3. V Průzkumník řešení vyberte soubor. pkgdef a v okně **vlastnosti** se ujistěte, že je **Akce sestavení** nastavena na **obsah**, možnost **Kopírovat do výstupního adresáře** je nastavena na hodnotu **vždy kopírovat**a **v souboru VSIX** je nastavena **hodnota true**.

4. Přidejte soubor. pkgdef jako prostředek do manifestu VSIX. V souboru source. extension. vsixmanifest přejděte na kartu **assets (prostředky** ) a klikněte na **Nový**.

5. V dialogovém okně **Přidat nový prostředek** nastavte **typ** na **Microsoft. VisualStudio. VSPackage**, **Zadejte** **soubor v systému souborů**a **cestu** k **HelloWorldVB. pkgdef** (která by se měla objevit v rozevíracím seznamu).

### <a name="testing-the-snippet"></a>Testování fragmentu

1. Nyní se můžete ujistit, že fragment kódu funguje v experimentální instanci aplikace Visual Studio. Experimentální instance je druhá kopie sady Visual Studio, která je oddělená od ta, kterou používáte k psaní kódu. Umožňuje pracovat s rozšířením, aniž by to mělo vliv na vývojové prostředí.

2. Sestavte projekt a spusťte ladění. Měla by se zobrazit druhá instance aplikace Visual Studio.

3. V experimentální instanci otevřete **Správce fragmentů kódu** a nastavte **jazyk** na **Basic**. Měli byste vidět HelloWorldVB jako jednu ze složek a měli byste být schopni rozbalit složku pro zobrazení fragmentu HelloWorldVB.

4. Otestujte fragment. V experimentální instanci otevřete Visual Basic projekt a otevřete jeden ze souborů kódu. Umístěte kurzor někam do kódu, klikněte pravým tlačítkem myši a v místní nabídce vyberte **Vložit fragment**.

5. Měli byste vidět HelloWorldVB jako jednu ze složek. Poklikejte na ni. Měl by se zobrazit překryvný **fragment vložení: HellowWorldVB >** , který má rozevírací seznam **HelloWorldVB**. Klikněte na rozevírací seznam HelloWorldVB. Měl by se zobrazit následující řádek přidaný do souboru:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Viz také
 [Fragmenty kódu](../ide/code-snippets.md)
