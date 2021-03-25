---
title: Použití klávesových zkratek s rozšířením editoru
description: Naučte se, jak přidat doplňky zobrazení k textovému zobrazení pomocí klávesových zkratek. Tento návod je založen na šabloně editoru doplňků zobrazení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2d49fa9e858d65529e466f6ed960835ab8c2324
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061950"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Návod: použití klávesových zkratek s rozšířením editoru
Můžete reagovat na klávesové zkratky v rozšíření editoru. Následující návod ukazuje, jak přidat doplňky zobrazení do textového zobrazení pomocí klávesových zkratek. Tento návod je založen na šabloně editoru doplňků zobrazení a umožňuje přidat doplňky pomocí znaku +.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvořit projekt Managed Extensibility Framework (MEF)

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `KeyBindingTest` .

2. Přidejte do projektu šablonu položky vylepšení textu editoru a pojmenujte ji `KeyBindingTest` . Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Přidejte následující odkazy a nastavte **CopyLocal** na `false` :

    Microsoft. VisualStudio. Editor

    Microsoft. VisualStudio. OLE. Interop

    Microsoft. VisualStudio. Shell. 14.0

    Microsoft. VisualStudio. TextManager. Interop

   V souboru třídy KeyBindingTest změňte název třídy na PurpleCornerBox. Použijte žárovku, která se zobrazí na levém okraji, a proveďte další příslušné změny. Uvnitř konstruktoru změňte název přípředné vrstvy z **KeyBindingTest** na **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

V souboru třídy KeyBindingTestTextViewCreationListener. cs změňte název AdornmentLayer z **KeyBindingTest** na **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Zpracovat příkaz TYPECHAR
Před vydáním sady Visual Studio 2017 verze 15,6 jediným způsobem, jak zpracovávat příkazy v rozšíření editoru, byla implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> filtru příkazů založeného na příkazu. Visual Studio 2017 verze 15,6 představila moderní zjednodušený přístup na základě obslužných rutin příkazů editoru. Následující dvě části ukazují, jak zpracovat příkaz pomocí staršího i moderního přístupu.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definice filtru příkazů (před verzí sady Visual Studio 2017 15,6)

 Filtr příkazů je implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , která zpracovává příkaz tím, že vytváří doplňky.

1. Přidejte soubor třídy a pojmenujte ho `KeyBindingCommandFilter` .

2. Přidejte následující direktivy using.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. Třída s názvem KeyBindingCommandFilter by měla dědit z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Přidejte soukromá pole pro textové zobrazení, další příkaz v řetězu příkazů a příznak, který představuje, zda byl filtr příkazů již přidán.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Přidejte konstruktor, který nastaví textové zobrazení.

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

7. Implementujte `Exec()` metodu tak, aby do zobrazení přidala fialové pole, pokud **+** je zapsán znak plus ().

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Přidejte filtr příkazů (před verzí Visual Studio 2017 15,6)
 Poskytovatel doplňků musí do textového zobrazení přidat filtr příkazů. V tomto příkladu poskytovatel implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> k naslouchání událostem vytváření zobrazení textu. Tento poskytovatel vylepšení také exportuje vrstvu pro úpravy, která definuje pořadí vykreslování doplňku.

1. Do souboru KeyBindingTestTextViewCreationListener přidejte následující direktivy using:

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

2. Chcete-li získat adaptér pro zobrazení textu, je nutné importovat <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Změňte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, aby přidala `KeyBindingCommandFilter` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. `AddCommandFilter`Obslužná rutina získá adaptér pro zobrazení textu a přidá filtr příkazů.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementace obslužné rutiny příkazu (počínaje verzí Visual Studio 2017 verze 15,6)

Nejdřív aktualizujte odkazy NuGet projektu tak, aby odkazovaly na nejnovější Editor API:

1. Klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.

2. Ve **Správci balíčků NuGet** vyberte kartu **aktualizace** , zaškrtněte políčko **Vybrat všechny balíčky** a pak vyberte **aktualizovat**.

Obslužná rutina příkazu je implementace <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601> , která zpracovává příkaz vytvořením doplňku.

1. Přidejte soubor třídy a pojmenujte ho `KeyBindingCommandHandler` .

2. Přidejte následující direktivy using.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. Třída s názvem KeyBindingCommandHandler by měla dědit z `ICommandHandler<TypeCharCommandArgs>` a exportovat jako <xref:Microsoft.VisualStudio.Commanding.ICommandHandler> :

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

5. Implementujte `GetCommandState()` metodu následujícím způsobem. Vzhledem k tomu, že tato obslužná rutina příkazu zpracovává základní editor příkazu TYPECHAR, může delegovat povolení příkazu základnímu editoru.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implementujte `ExecuteCommand()` metodu tak, aby do zobrazení přidala fialové pole, pokud **+** je zapsán znak plus ().

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

   7. Zkopírujte definici vrstvy doplňků ze souboru *KeyBindingTestTextViewCreationListener. cs* do souboru *KeyBindingCommandHandler.* cs a pak odstraňte soubor *KeyBindingTestTextViewCreationListener. cs* :

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

## <a name="make-the-adornment-appear-on-every-line"></a>Zobrazení přívylepšení na každém řádku

Původní doplňky se objevily u každého znaku a v textovém souboru. Teď, když jsme kód změnili tak, aby přidal doplňky jako odpověď na daný **+** znak, přidá doplňky jenom na řádek, kde **+** je znak zadaný. Kód pro úpravy můžeme změnit tak, aby se doplňky zobrazovaly na všech znakech a.

V souboru *KeyBindingTest. cs* změňte `CreateVisuals()` metodu tak, aby procházela všemi řádky v zobrazení, aby se vyměnila znak "a".

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

1. Sestavte řešení KeyBindingTest a spusťte ho v experimentální instanci.

2. Vytvořte nebo otevřete textový soubor. Zadejte některá slova obsahující znak "a" a potom zadejte **+** libovolné místo v textovém zobrazení.

     Do každého znaku a v souboru by se měl objevit fialový čtverec.
