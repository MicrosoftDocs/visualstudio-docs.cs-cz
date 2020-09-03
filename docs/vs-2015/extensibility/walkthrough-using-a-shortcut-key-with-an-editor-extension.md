---
title: 'Návod: použití klávesových zkratek s rozšířením editoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201945"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Návod: Použití klávesové zkratky s rozšířením editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete reagovat na klávesové zkratky v rozšíření editoru. Následující návod ukazuje, jak přidat doplňky zobrazení do textového zobrazení pomocí klávesových zkratek. Tento návod je založen na šabloně editoru doplňků zobrazení a umožňuje přidat doplňky pomocí znaku +.  
  
## <a name="prerequisites"></a>Požadavky  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost**a potom **projekt VSIX**.) Pojmenujte řešení `KeyBindingTest` .  
  
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
  
## <a name="defining-the-command-filter"></a>Definování filtru příkazů  
 Filtr příkazů je implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , která zpracovává příkaz tím, že vytváří doplňky.  
  
1. Přidejte soubor třídy a pojmenujte ho `KeyBindingCommandFilter` .  
  
2. Přidejte následující příkazy using.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. Třída s názvem KeyBindingCommandFilter by měla dědit z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. Přidejte soukromá pole pro textové zobrazení, další příkaz v řetězu příkazů a příznak, který představuje, zda byl filtr příkazů již přidán.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
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
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. Implementujte `Exec()` metodu tak, aby do zobrazení přidala fialové pole, pokud je zadán znak +.  
  
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
  
## <a name="adding-the-command-filter"></a>Přidání filtru příkazů  
 Poskytovatel doplňků musí do textového zobrazení přidat filtr příkazů. V tomto příkladu poskytovatel implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> k naslouchání událostem vytváření zobrazení textu. Tento poskytovatel vylepšení také exportuje vrstvu pro úpravy, která definuje pořadí vykreslování doplňku.  
  
1. V souboru KeyBindingTestTextViewCreationListener přidejte následující příkazy using:  
  
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
  
2. V definici vrstvy pro doplňky změňte název AdornmentLayer z **KeyBindingTest** na **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. Chcete-li získat adaptér pro zobrazení textu, je nutné importovat <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. Změňte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, aby přidala `KeyBindingCommandFilter` .  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. `AddCommandFilter`Obslužná rutina získá adaptér pro zobrazení textu a přidá filtr příkazů.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Zobrazení přívylepšení na každém řádku  
 Původní doplňky se objevily u každého znaku a v textovém souboru. Teď, když jsme změnili kód, abychom přidali doplňky jako odpověď na znak "+", přidá se doplňky jenom na řádek, kde je zadaný znak +. Kód pro úpravy můžeme změnit tak, aby se doplňky zobrazovaly na všech znakech a.  
  
 V souboru KeyBindingTest.cs změňte metodu CreateVisuals () tak, aby procházela přes všechny řádky v zobrazení a vyplní znak "a".  
  
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
  
## <a name="building-and-testing-the-code"></a>Sestavování a testování kódu  
  
1. Sestavte řešení KeyBindingTest a spusťte ho v experimentální instanci.  
  
2. Vytvořte nebo otevřete textový soubor. Zadejte slova, která obsahují znak "a", a potom v textovém zobrazení zadejte + kdekoli.  
  
     Do každého znaku a v souboru by se měl objevit fialový čtverec.
