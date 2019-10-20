---
title: 'Návod: ladění textové šablony přistupující k modelu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7dc591451b314d5ebac10d30cc89d9498d70f96b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659271"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Návod: Ladění textové šablony přistupující k modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když upravujete nebo přidáváte textové šablony v řešení jazyka specifického pro doménu, může dojít k chybám, když modul transformuje šablonu na zdrojový kód nebo když zkompiluje generovaný kód. Následující návod ukazuje některé z akcí, které můžete provést při ladění textové šablony.

> [!NOTE]
> Další informace o šablonách textu obecně naleznete v tématu [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md). Další informace o ladění textových šablon naleznete v tématu [Návod: ladění textové šablony](https://msdn.microsoft.com/library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).

## <a name="creating-a-domain-specific-language-solution"></a>Vytváření řešení jazyka specifického pro doménu
 V tomto postupu vytvoříte řešení jazyka specifického pro doménu, které má následující vlastnosti:

- Název: DebuggingTestLanguage

- Šablona řešení: minimální jazyk

- Přípona souboru:. ddd

- Název společnosti: Fabrikam

  Další informace o vytváření řešení jazyka specifického pro doménu najdete v tématu [Postupy: vytvoření řešení jazyka specifického pro doménu](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Vytvoření textové šablony
 Přidejte do svého řešení textovou šablonu.

#### <a name="to-create-a-text-template"></a>Vytvoření textové šablony

1. Sestavte řešení a začněte ho spouštět v ladicím programu. (V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**a potom v nabídce **ladění** klikněte na příkaz **Spustit ladění**.) Nová instance aplikace Visual Studio otevře ladění projektu.

2. Přidejte textový soubor s názvem `DebugTest.tt` do ladicího projektu.

3. Ujistěte se, že vlastnost **Custom Tool** třídy DebugTest.TT je nastavená na `TextTemplatingFileGenerator`.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Direktivy ladění, které přistupují k modelu z textové šablony
 Předtím, než budete moci získat přístup k modelu z příkazů a výrazů v textové šabloně, je nutné nejprve volat generovaný procesor direktiv. Volání vygenerovaného procesoru direktiv zpřístupňuje třídy v modelu pro kód textové šablony jako vlastnosti. Další informace naleznete v tématu [přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md).

 V následujících postupech budete ladit nesprávný název direktivy a název nesprávného názvu vlastnosti.

#### <a name="to-debug-an-incorrect-directive-name"></a>Ladění nesprávného názvu direktivy

1. Nahraďte kód v DebugTest.tt následujícím kódem:

    > [!NOTE]
    > Kód obsahuje chybu. Představujeme chybu, abyste ji mohli ladit.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. V **Průzkumník řešení**klikněte pravým tlačítkem na DebugTest.TT a pak klikněte na **Spustit vlastní nástroj**.

     Tato chyba se zobrazí v okně **Seznam chyb** :

     **Procesor nazvaný ' DebuggingTestLanguageDirectiveProcessor ' nepodporuje direktivu nazvanou ' modelRoot '. Transformace se nespustí.**

     V tomto případě volání direktivy obsahuje nesprávný název direktivy. Zadali jste `modelRoot` jako název direktivy, ale správný název direktivy je `DebuggingTestLanguage`.

3. Dvojitým kliknutím na chybu v okně **Seznam chyb** přejdete do kódu.

4. Chcete-li tento kód opravit, změňte název direktivy na `DebuggingTestLanguage`.

     Změna je zvýrazněna.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. V **Průzkumník řešení**klikněte pravým tlačítkem na DebugTest.TT a pak klikněte na **Spustit vlastní nástroj**.

     Nyní systém transformuje textovou šablonu a generuje odpovídající výstupní soubor. V okně **Seznam chyb** se nezobrazí žádné chyby.

#### <a name="to-debug-an-incorrect-property-name"></a>Ladění nesprávného názvu vlastnosti

1. Nahraďte kód v DebugTest.tt následujícím kódem:

    > [!NOTE]
    > Kód obsahuje chybu. Představujeme chybu, abyste ji mohli ladit.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. V **Průzkumník řešení**klikněte pravým tlačítkem na DebugTest.TT a pak klikněte na **Spustit vlastní nástroj**.

     Zobrazí se okno **Seznam chyb** a zobrazí se jedna z následujících chyb:

     (C#)

     **Kompilování transformace: Microsoft. VisualStudio. TextTemplating \<GUID >. GeneratedTextTransformation neobsahuje definici pro ' ExampleModel '.**

     (Visual Basic)

     **Kompilace transformace: ' ExampleModel ' není členem ' Microsoft. VisualStudio. TextTemplating \<GUID >. GeneratedTextTransformation'.**

     V tomto případě kód textové šablony obsahuje nesprávný název vlastnosti. Zadali jste `ExampleModel` jako název vlastnosti, ale správný název vlastnosti je `LibraryModel`. Správný název vlastnosti můžete najít v parametru poskytuje, jak je znázorněno v následujícím kódu:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Dvojitým kliknutím na chybu v okně Seznam chyb přejdete do kódu.

4. Chcete-li tento kód opravit, změňte název vlastnosti na `LibraryModel` v kódu textové šablony.

     Změny jsou zvýrazněny.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5. V **Průzkumník řešení**klikněte pravým tlačítkem na DebugTest.TT a pak klikněte na **Spustit vlastní nástroj**.

     Nyní systém transformuje textovou šablonu a generuje odpovídající výstupní soubor. V okně **Seznam chyb** se nezobrazí žádné chyby.
