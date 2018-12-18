---
title: 'Návod: Použití klávesové zkratky s rozšířením editoru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e68cf9d3e33ad07ab092de680078972dfaf2d70
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797452"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Návod: Použití klávesové zkratky s rozšířením editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klávesové zkratky můžete reagovat v rozšíření editoru. Následující návod ukazuje, jak přidat grafického doplňku zobrazení k zobrazení textu s použitím klávesovou zkratku. Tento názorný postup je založen na šabloně editor grafického doplňku zobrazení, a umožňuje vám přidat dalších úprav s použitím na znak +.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
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
  
## <a name="defining-the-command-filter"></a>Definuje filtr příkaz  
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
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Přidáte soukromé pole pro zobrazení textu, další příkaz v příkazu řetězec a příznak označuje, zda příkaz filtru již byla přidána.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
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
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementace `Exec()` metoda tak Fialová box se přidá do zobrazení, pokud + znaku.  
  
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
  
## <a name="adding-the-command-filter"></a>Přidání příkaz filtru  
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
  
2.  V definici vrstvy dalších úprav, změňte název AdornmentLayer z **KeyBindingTest** k **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  K získání adaptéru zobrazení textu, je nutné naimportovat <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Změnit <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, že se přidá `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter` Obslužná rutina získá adaptér zobrazení textu a přidá příkaz Filtr.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Provádění dalších úprav se zobrazí na každém řádku  
 Původní dalších úprav zobrazilo na každý znak "a" do textového souboru. Teď, když jsme změnili kód pro přidání dalších úprav v reakci na znak '+', přidá dalších úprav pouze na řádku kde '+' je zadán. Můžeme změnit dalších úprav kódu tak, aby zobrazil dalších úprav ještě jednou na každý "a".  
  
 V souboru KeyBindingTest.cs změníte metodu CreateVisuals() k iteraci v rámci všech řádků v zobrazení pro uspořádání "a" znak.  
  
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
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
  
1.  Sestavte řešení KeyBindingTest a spustíte ji v experimentální instanci aplikace.  
  
2.  Vytvořte nebo otevřete textový soubor. Zadejte slova, některé obsahující znak "a" a pak zadejte + kdekoli v zobrazení textu.  
  
     Na každý "a" znak v souboru by se zobrazit fialový čtverec.

