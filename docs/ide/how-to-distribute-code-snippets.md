---
title: 'Postupy: distribuce fragmentů kódu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: cd6aba7c20c920c0c4351a1e9aa263fc73cd4415
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380414"
---
# <a name="how-to-distribute-code-snippets"></a>Postupy: distribuce fragmentů kódu

Můžete poskytnout fragmenty svého kódu přátelům a nainstalovat fragmenty kódu ve svých počítačích pomocí **Správce fragmentů kódů**. Pokud máte chcete distribuovat více fragmentů nebo chcete distribuovat více široce, je však zahrnout souboru fragmentu v rozšíření sady Visual Studio. Uživatelé sady Visual Studio můžete nainstalovat rozšíření.

Chcete-li vytvořit rozšíření sady Visual Studio je nutné nainstalovat sadu Visual Studio SDK. Najít verzi nástroje VSSDK, který odpovídá vaší instalaci sady Visual Studio na [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

## <a name="set-up-the-extension"></a>Nastavit rozšíření

V tomto postupu použijeme stejný Hello World fragmentu kódu, který je vytvořen v [návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md). Můžeme vám poskytnout *.snippet* text, takže není nutné vrátit zpět a si ho.

1. Vytvořte nový projekt VSIX s názvem **TestSnippet**. (**Souboru** > **nové** > **projektu** > **Visual C# (nebo Visual Basic)**  >  **Rozšiřitelnost**.)

2. V **TestSnippet** projektu, přidejte nový soubor XML a jeho volání *VBCodeSnippet.snippet*. Nahraďte obsah následujícím XML:

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

### <a name="set-up-the-directory-structure"></a>Nastavit adresářovou strukturu

1. V **Průzkumníka řešení**, vyberte uzel projektu a přidejte složku, která má název, který chcete fragment kódu na **Správce fragmentů kódů**. V takovém případě by měl být **HelloWorldVB**.

2. Přesunout *.snippet* do souboru *HelloWorldVB* složky.

3. Vyberte *.snippet* ve **Průzkumníka řešení**a **vlastnosti** Ujistěte se, že okno **akce sestavení** je nastavena na **Obsahu**, **kopírovat do výstupního adresáře** je nastavena na **vždy Kopírovat**, a **zahrnout do VSIX** je nastavena na **true**.

### <a name="add-the-pkgdef-file"></a>Přidejte soubor .pkgdef

1. Přidat textový soubor, který *HelloWorldVB* složku a pojmenujte ho *HelloWorldVB.pkgdef*. Tento soubor se používá k přidání určité klíče registru. V takovém případě přidá nový podklíč pro **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic** klíč.

2. Přidejte následující řádky do souboru.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Pokud si projdete tento klíč, najdete v článku určení různých jazycích.

3. Vyberte *.pkgdef* ve **Průzkumníka řešení**a **vlastnosti** okno Ujistěte se, že:

   - **Akce sestavení** je nastavena na **obsahu**
   - **Kopírovat do výstupního adresáře** je nastavena na **vždy kopírovat**
   - **Zahrnout do VSIX** je nastavena na **true**

4. Přidat *.pkgdef* souborů jako prostředek v manifestu VSIX. V *source.extension.vsixmanifest* souboru, přejděte **prostředky** kartě a klikněte na tlačítko **nový**.

5. V **přidat nové aktivum** dialogové okno, nastavte **typ** k **Microsoft.VisualStudio.VsPackage**, **zdroj** k **souborů v systém souborů**a **cesta** k **HelloWorldVB.pkgdef** (které by se zobrazit v rozevíracím seznamu).

### <a name="test-the-snippet"></a>Fragment kódu pro testování

1. Nyní, abyste měli jistotu, že fragment kódu funguje v experimentální instanci sady Visual Studio. Experimentální instanci je druhý kopie sady Visual Studio, která je oddělená od ten, který můžete použít k zápisu kódu. Umožňuje pracovat na rozšíření, aniž by to ovlivnilo vývojového prostředí.

2. Sestavte projekt a spusťte ladění.

   Zobrazí se druhé instanci aplikace Visual Studio.

3. V experimentální instanci aplikace, přejděte na **nástroje** > **Správce fragmentů kódů** a nastavit **jazyk** k **základní**. Měli byste vidět *HelloWorldVB* jako jeden ze složky a bude schopen rozbalte složku zobrazíte *HelloWorldVB* fragment kódu.

4. Otestujte fragment kódu. V experimentální instanci aplikace otevřete projekt jazyka Visual Basic a otevřete jeden ze souborů kódu. Umístěte ukazatel myši kamkoli v kódu, klikněte pravým tlačítkem a v místní nabídce vyberte příkaz **Vložit fragment**.

5. Měli byste vidět *HelloWorldVB* jako jedna ze složek. Poklepejte na něj. Zobrazí se automaticky otevírané okno **Vložit fragment kódu: HelloWorldVB >** , který má rozevíracího seznamu **HelloWorldVB**. Klikněte na tlačítko **HelloWorldVB** rozevíracího seznamu. Měli byste vidět následující řádek do souboru přidán:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu](../ide/code-snippets.md)