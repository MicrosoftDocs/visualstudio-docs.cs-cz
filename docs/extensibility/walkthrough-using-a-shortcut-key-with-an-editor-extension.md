---
title: 'Návod: Použití klávesové zkratky s rozšířením editoru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697155"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Návod: Použití klávesové zkratky s rozšířením editoru
Můžete reagovat na klávesové zkratky v rozšíření editoru. Následující návod ukazuje, jak přidat vylepšení zobrazení do zobrazení textu pomocí klávesové zkratky. Tento návod je založen na šabloně editoru vylepšení výřezu a umožňuje přidat vylepšení pomocí znaku +.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu spravovaného rámce rozšiřitelnosti (MEF)

1. Vytvořte projekt C# VSIX. (V dialogovém okně **Nový projekt** vyberte možnost **Vizuální C# / Rozšiřitelnost**a potom **v six projectu**.) Pojmenujte `KeyBindingTest`řešení .

2. Přidejte do projektu šablonu položky Vylepšení `KeyBindingTest`textu editoru a pojmenujte ji . Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Přidejte následující odkazy a nastavte `false` **CopyLocal** na :

    Microsoft.VisualStudio.Editor

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   V souboru třídy KeyBindingTest změňte název třídy na PurpleCornerBox. Použijte žárovku, která se zobrazí v levém okraji, abyste udělali další vhodné změny. Uvnitř konstruktoru změňte název vrstvy vylepšení z **KeyBindingTest** na **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

V souboru třídy KeyBindingTestTextViewCreationListener.cs změňte název AdornmentLayer z **KeyBindingTest** na **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Popisovač TYPECHAR, příkaz
Před Visual Studio 2017 verze 15.6 jediný způsob, jak pracovat s <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> příkazy v rozšíření editoru byla implementace filtru příkazů na základě. Visual Studio 2017 verze 15.6 zavedlo moderní zjednodušený přístup založený na obslužných rutinách příkazů editoru. Následující dvě části ukazují, jak zpracovat příkaz pomocí starší verze a moderní přístup.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definování filtru příkazů (před Visual Studio 2017 verze 15.6)

 Příkaz ový filtr je <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>implementace aplikace , která zpracovává příkaz vytvořením instance vylepšení.

1. Přidejte soubor třídy `KeyBindingCommandFilter`a pojmenujte jej .

2. Přidejte následující pomocí direktiv.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. Třída s názvem KeyBindingCommandFilter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>by měla dědit z .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Přidejte soukromá pole pro zobrazení textu, další příkaz v řetězci příkazů a příznak představující, zda již byl přidán filtr příkazů.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Přidejte konstruktor, který nastaví zobrazení textu.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Implementujte `QueryStatus()` metodu následujícím způsobem.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Implementujte `Exec()` metodu tak, aby přidala do zobrazení**+** fialové pole, pokud je zadán znak znaménko plus ( ).

    ```csharp
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
    {
        if (m_adorned == false)
        {
            char typedChar = char.MinValue;

            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)
            {
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);
                if (typedChar.Equals('+'))
                {
                    new PurpleCornerBox(m_textView);
                    m_adorned = true;
                }
            }
        }
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);
    }

    ```

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Přidání filtru příkazů (před Visual Studio 2017 verze 15.6)
 Zprostředkovatel vylepšení musí do textového zobrazení přidat filtr příkazů. V tomto příkladu zprostředkovatel <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> implementuje naslouchat události vytváření zobrazení textu. Tento zprostředkovatel vylepšení také exportuje vrstvu vylepšení, která definuje pořadí vykreslování vylepšení.

1. V souboru KeyBindingTestTextViewCreationListener přidejte pomocí direktiv následující:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio.Utilities;
    using Microsoft.VisualStudio.Editor;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.TextManager.Interop;

    ```

2. Chcete-li získat adaptér zobrazení textu, je nutné importovat . <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Změňte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, `KeyBindingCommandFilter`aby přidá .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. Obslužná rutina `AddCommandFilter` získá adaptér zobrazení textu a přidá filtr příkazů.

    ```csharp
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)
    {
        if (commandFilter.m_added == false)
        {
            //get the view adapter from the editor factory
            IOleCommandTarget next;
            IVsTextView view = editorFactory.GetViewAdapter(textView);

            int hr = view.AddCommandFilter(commandFilter, out next);

            if (hr == VSConstants.S_OK)
            {
                commandFilter.m_added = true;
                 //you'll need the next target for Exec and QueryStatus
                if (next != null)
                commandFilter.m_nextTarget = next;
            }
        }
    }
    ```

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementace obslužné rutiny příkazů (počínaje visual studio 2017 verze 15.6)

Nejprve aktualizujte odkazy na Nuget projektu tak, aby odkazovaly na nejnovější rozhraní API editoru:

1. Klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky Nuget**.

2. Ve **Správci balíčků aplikace Nuget**vyberte kartu **Aktualizace,** zaškrtněte políčko **Vybrat všechny balíčky** a pak vyberte **Aktualizovat**.

Obslužná rutina příkazu je implementace aplikace <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, která zpracovává příkaz vytvořením instance vylepšení.

1. Přidejte soubor třídy `KeyBindingCommandHandler`a pojmenujte jej .

2. Přidejte následující pomocí direktiv.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. Třída s názvem KeyBindingCommandHandler `ICommandHandler<TypeCharCommandArgs>`by měla <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>dědit z a exportovat ji jako :

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Přidejte zobrazovaný název obslužné rutiny příkazu:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Implementujte `GetCommandState()` metodu následujícím způsobem. Vzhledem k tomu, že tento příkaz obslužná rutina zpracovává příkaz typechar základního editoru, může delegovat povolení příkazu do základního editoru.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implementujte `ExecuteCommand()` metodu tak, aby přidala do zobrazení**+** fialové pole, pokud je zadán znak znaménko plus ( ).

   ```csharp
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```

   7. Zkopírujte definici vrstvy vylepšení ze souboru *KeyBindingTestTextViewCreationListener.cs* do *KeyBindingCommandHandler.cs* a poté *KeyBindingTestTextViewCreationListener.cs* soubor odstraňte:

   ```csharp
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;
   ```

## <a name="make-the-adornment-appear-on-every-line"></a>Aby se ozdoba objevila na každém řádku

Původní ozdoba se objevila na každém znaku "a" v textovém souboru. Nyní, když jsme změnili kód přidat vylepšení **+** v reakci na znak, přidá vylepšení **+** pouze na řádku, kde je zadán znak. Můžeme změnit kód ozdoby tak, aby ozdoba opět objeví na každém 'a'.

V *souboru KeyBindingTest.cs* `CreateVisuals()` změňte metodu iterátpřes všechny řádky v zobrazení k dekoraci znaku 'a'.

```csharp
private void CreateVisuals(ITextViewLine line)
{
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;

    foreach (ITextViewLine textViewLine in textViewLines)
    {
        if (textViewLine.ToString().Contains("a"))
        {
            // Loop through each character, and place a box around any 'a'
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)
            {
                if (this.view.TextSnapshot[charIndex] == 'a')
                {
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);
                    if (geometry != null)
                    {
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);
                        drawing.Freeze();

                        var drawingImage = new DrawingImage(drawing);
                        drawingImage.Freeze();

                        var image = new Image
                        {
                            Source = drawingImage,
                        };

                        // Align the image with the top of the bounds of the text geometry
                        Canvas.SetLeft(image, geometry.Bounds.Left);
                        Canvas.SetTop(image, geometry.Bounds.Top);

                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);
                    }
                }
            }
        }
    }
}
```

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu

1. Vytvořte řešení KeyBindingTest a spusťte jej v experimentální instanci.

2. Vytvořte nebo otevřete textový soubor. Zadejte některá slova obsahující znak "a" a pak zadejte **+** kdekoli v textovém zobrazení.

     Na každém znaku "a" v souboru by se měl objevit fialový čtverec.
