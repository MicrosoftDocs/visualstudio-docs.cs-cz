---
title: 'Postupy: distribuce fragmentů kódu | Dokumentace Microsoftu'
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
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14dea3842289b626b79d8dc7e294ba5f335d0351
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185702"
---
# <a name="how-to-distribute-code-snippets"></a>Postupy: Distribuce fragmentů kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete jednoduše poskytnout fragmenty svého kódu přátelům a nechat nainstalovat pomocí Správce fragmentů kódů ve svých počítačích. Pokud máte chcete distribuovat více fragmentů nebo chcete distribuovat více široce, je však zahrnout souboru fragmentu v rozšíření sady Visual Studio, které uživatelům aplikace Visual Studio můžete nainstalovat.  
  
 Chcete-li vytvořit rozšíření sady Visual Studio je nutné nainstalovat sadu Visual Studio SDK. Najít verzi nástroje VSSDK, který odpovídá vaší instalaci sady Visual Studio na [Visual Studio 2015 ke stažení](http://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs.aspx).  
  
## <a name="setting-up-the-extension"></a>Nastavení rozšíření  
 V tomto postupu použijeme stejný fragmentu kódu Hello World vytvořené v [návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md). Jsme dodá .snippet text, takže není nutné vrátit zpět a si ho.  
  
1.  Vytvořte nový projekt VSIX s názvem **TestSnippet**. (**Soubor / nový / Project / Visual C# (nebo Visual Basic / rozšíření**)  
  
2.  V **TestSnippet** projektu, přidejte nový soubor XML a jeho volání **VBCodeSnippet.snippet**. Nahraďte obsah následujícím kódem:  
  
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
  
#### <a name="setting-up-the-directory-structure"></a>Nastavení struktury adresáře  
  
1.  V Průzkumníku řešení vyberte uzel projektu a přidejte složku, která má název, který chcete fragment kódu na Správce fragmentů kódů. V tomto případě by měl být **HelloWorldVB**.  
  
2.  Soubor .snippet přesunout **HelloWorldVB** složky.  
  
3.  V Průzkumníku řešení a vyberte soubor .snippet **vlastnosti** Ujistěte se, že okno **akce sestavení** je nastavena na **obsahu**, **kopírovat do výstupu Adresář** je nastavena na **vždy Kopírovat**, a **zahrnout do VSIX** je nastavena na **true**.  
  
#### <a name="adding-the-pkgdef-file"></a>Přidává se soubor .pkgdef  
  
1.  Přidat textový soubor, který **HelloWorldVB** složku a pojmenujte ho **HelloWorldVB.pkgdef**. Tento soubor se používá k přidání určité klíče registru. V tomto případě přidá nový klíč  
  
     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic**.  
  
2.  Přidejte následující řádky do souboru.  
  
    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  
  
     Pokud si projdete tento klíč, najdete v článku určení různých jazycích.  
  
3.  V Průzkumníku řešení a vyberte soubor .pkgdef **vlastnosti** Ujistěte se, že okno **akce sestavení** je nastavena na **obsahu**, **kopírovat do výstupního adresáře**  je nastavena na **vždy Kopírovat**, a **zahrnout do VSIX** je nastavena na **true**.  
  
4.  Přidejte soubor .pkgdef jako prostředek v manifestu VSIX. V souboru source.extension.vsixmanifest, přejděte **prostředky** kartě a klikněte na tlačítko **nový**.  
  
5.  V **přidat nové aktivum** dialogové okno, nastavte **typ** k **Microsoft.VisualStudio.VsPackage**, **typ** k **souborů v systém souborů**a **cesta** k **HelloWorldVB.pkgdef** (které by se zobrazit v rozevíracím seznamu).  
  
### <a name="testing-the-snippet"></a>Fragment kódu pro testování  
  
1.  Nyní, abyste měli jistotu, že fragment kódu funguje v experimentální instanci sady Visual Studio. Experimentální instanci je druhý kopie sady Visual Studio, která je oddělená od ten, který můžete použít k zápisu kódu. Umožňuje pracovat na rozšíření, aniž by to ovlivnilo vývojového prostředí.  
  
2.  Sestavte projekt a spusťte ladění. Druhou instanci aplikace Visual Studio by se zobrazit.  
  
3.  V experimentální instanci aplikace, přejděte na **nástroje / kód Správce fragmentů** a nastavit **jazyk** k **základní**. HelloWorldVB by se měla zobrazit jako jedna ze složek a byste měli rozbalte složku zobrazíte HelloWorldVB fragment kódu.  
  
4.  Otestujte fragment kódu. V experimentální instanci aplikace otevřete projekt jazyka Visual Basic a otevřete jeden ze souborů kódu. Umístěte ukazatel myši kamkoli v kódu, klikněte pravým tlačítkem a v místní nabídce vyberte příkaz **Vložit fragment**.  
  
5.  Měli byste vidět HelloWorldVB jako jedna ze složek. Poklepejte na něj. Zobrazí se automaticky otevírané okno **Vložit fragment kódu: HellowWorldVB >** , který má rozevíracího seznamu **HelloWorldVB**. Klikněte na rozevírací nabídku HelloWorldVB. Měli byste vidět následující řádek do souboru přidán:  
  
    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Fragmenty kódu](../ide/code-snippets.md)



