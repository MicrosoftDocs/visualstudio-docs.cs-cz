---
title: 'Návod: Použití klávesové zkratky s rozšířením editoru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d009351efdd36e0d415d0e2e457f7974608ab665
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886497"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Návod: Použití klávesové zkratky s rozšířením editoru
Klávesové zkratky můžete reagovat v rozšíření editoru. Následující návod ukazuje, jak přidat grafického doplňku zobrazení k zobrazení textu s použitím klávesovou zkratku. Tento názorný postup je založen na šabloně editor grafického doplňku zobrazení, a umožňuje vám přidat dalších úprav s použitím na znak +.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
1. Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `KeyBindingTest`.  
  
2. Přidání dalších úprav editoru textu šablony položky do projektu a pojmenujte ho `KeyBindingTest`. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Přidejte následující odkazy a nastavte **CopyLocal** k `false`:  
  
    Microsoft.VisualStudio.Editor  
  
    Sestavení Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft.VisualStudio.Shell.14.0  
  
    Microsoft.VisualStudio.TextManager.Interop  
  
   V souboru třídy KeyBindingTest změňte název třídy na PurpleCornerBox. Abyste provedli odpovídající změny pomocí žárovky, který se zobrazí na levém okraji. Uvnitř konstruktoru, změňte název vrstvy grafického doplňku z **KeyBindingTest** k **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  

V souboru třídy KeyBindingTestTextViewCreationListener.cs, změňte název AdornmentLayer z **KeyBindingTest** k **PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handle-typechar-command"></a>Příkaz TYPECHAR popisovač
Před Visual Studio 2017 verze 15.6 se implementace jediný způsob, jak zpracovávat příkazy v rozšíření editoru <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> na základě příkaz filtru. Visual Studio 2017 verze 15.6 zavedené moderní zjednodušený přístup podle obslužné rutiny příkazů editoru. V následujících dvou částech ukazují, jak zpracovat příkaz pomocí i starší a moderní přístup.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Zadejte příkaz Filtr (před Visual Studio 2017 verze 15.6)

 Příkaz filtru je implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, která zpracovává příkaz po vytvoření instance dalších úprav.  
  
1.  Přidejte soubor třídy a pojmenujte ho `KeyBindingCommandFilter`.  
  
2.  Přidejte následující příkazy using.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  Třída s názvem KeyBindingCommandFilter by měla dědit z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Přidáte soukromé pole pro zobrazení textu, další příkaz v příkazu řetězec a příznak označuje, zda příkaz filtru již byla přidána.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Přidáte konstruktor, který nastaví zobrazení textu.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implementace `QueryStatus()` metodu následujícím způsobem.  
  
    ```csharp  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementace `Exec()` metoda tak Fialová box se přidá do zobrazení, pokud znaménko plus (**+**) znaku.  
  
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
  
## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Přidat filtr příkazu (před Visual Studio 2017 verze 15.6)
 Zprostředkovatel grafického doplňku musíte přidat příkaz filtru k zobrazení textu. V tomto příkladu poskytovateli implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> k naslouchání události vytváření zobrazení textu. Tento zprostředkovatel dalších úprav zároveň exportuje dalších úprav vrstvu, která definuje pořadí vykreslování dalších úprav.  
  
1.  V souboru KeyBindingTestTextViewCreationListener, přidejte následující příkazy using:  
  
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
  
2.  K získání adaptéru zobrazení textu, je nutné naimportovat <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  Změnit <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, že se přidá `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  `AddCommandFilter` Obslužná rutina získá adaptér zobrazení textu a přidá příkaz Filtr.  
  
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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementujte obslužnou rutinu příkazu (od verze Visual Studio 2017 verze 15.6)

Nejprve aktualizujte odkazy projektu Nuget tak, aby odkazovaly editoru nejnovější rozhraní API:

1. Klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky Nuget**.

2. V **Správce balíčků Nuget**, vyberte **aktualizace** kartu, vyberte **vybrat všechny balíčky** zaškrtávací políčko a pak vyberte **aktualizace**.

Obslužná rutina příkazu je implementace <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, která zpracovává příkaz po vytvoření instance dalších úprav.  
  
1. Přidejte soubor třídy a pojmenujte ho `KeyBindingCommandHandler`.  
  
2. Přidejte následující příkazy using.  
  
   ```csharp  
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;   
   ```  
  
3. Třída s názvem KeyBindingCommandHandler by měla dědit z `ICommandHandler<TypeCharCommandArgs>`a exportujte ho jako <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
   ```csharp  
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
   ```  
  
4. Přidáte zobrazovaný název obslužné rutiny příkazu:  
  
   ```csharp  
   public string DisplayName => "KeyBindingTest";
   ```  
    
5. Implementace `GetCommandState()` metodu následujícím způsobem. Protože tato obslužná rutina zpracovává příkaz TYPECHAR core editor, můžete delegovat, povolení příkazu základní editor.
  
   ```csharp  
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   } 
   ```  
  
6. Implementace `ExecuteCommand()` metoda tak Fialová box se přidá do zobrazení, pokud znaménko plus (**+**) znaku. 
  
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
   7. Zkopírujte definici dalších úprav vrstvy z *KeyBindingTestTextViewCreationListener.cs* do souboru *KeyBindingCommandHandler.cs* a odstraňte  *KeyBindingTestTextViewCreationListener.cs* souboru:
 
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

## <a name="make-the-adornment-appear-on-every-line"></a>Ujistěte se, dalších úprav se zobrazí na každém řádku  

Původní dalších úprav zobrazilo na každý znak "a" do textového souboru. Teď, když jsme změnili kód pro přidání dalších úprav v reakci **+** znak, přidá dalších úprav pouze na řádku kde **+** znaku. Můžeme změnit dalších úprav kódu tak, aby zobrazil dalších úprav ještě jednou na každý "a".  
  
V *KeyBindingTest.cs* změňte `CreateVisuals()` metoda k iteraci v rámci všech řádků v zobrazení pro uspořádání "a" znak.  
  
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
  
## <a name="build-and-test-the-code"></a>Vytváření a testování kódu  
  
1.  Sestavte řešení KeyBindingTest a spustíte ji v experimentální instanci aplikace.  
  
2.  Vytvořte nebo otevřete textový soubor. Zadejte slova, některé obsahující znak "a" a pak zadejte **+** kdekoli v zobrazení textu.  
  
     Na každý "a" znak v souboru by se zobrazit fialový čtverec.
