---
title: Přizpůsobení starší verze kódu pro Editor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e04ae5484b6c1fd5bcc56154c6cec23334e7ef8d
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307788"
---
# <a name="adapt-legacy-code-to-the-editor"></a>Přizpůsobení staršího kódu do editoru
Editor sady Visual Studio obsahuje řadu funkcí, které se dá dostat z existujícího kódu komponenty. Následující pokyny ukazují, jak přizpůsobit komponentu rozhraní MEF, například VSPackage, využívat funkce editoru. Podle pokynů také ukazují, jak využít adaptéry služby editoru spravovaným a nespravovaným kódem.  
  
## <a name="editor-adapters"></a>Editor adaptéry  
 Editor adaptéry nebo překrytí, jsou obálky pro editor objektů, které také poskytují třídy a rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop> rozhraní API. Můžete použít adaptéry pro přesun mezi službami jiných editor například příkazy prostředí sady Visual Studio a editor služby. (To je, jak se aktuálně hostuje editoru v sadě Visual Studio.) Adaptéry také povolit starší verze jazyk a editor služby rozšíření fungovat správně v sadě Visual Studio.  
  
## <a name="use-editor-adapters"></a>Použití editoru adaptéry  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> Poskytuje metody, které přepínat mezi nové rozhraní editoru a starší verze rozhraní a metody, které vytvářejí adaptéry.  
  
 Pokud použijete tuto službu v součásti MEF, můžete importovat službu následujícím způsobem.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Pokud chcete používat tuto službu v komponentě rozhraní MEF, postupujte podle pokynů v části "Pomocí Visual Studio Editor služby v Non-Komponenta MEF" dále v tomto tématu.  
  
## <a name="switch-between-the-new-editor-api-and-the-legacy-api"></a>Přepínání mezi nové rozhraní API editoru a starší verze rozhraní API  
 Pomocí následující metody můžete přepínat mezi objektem editoru a starší verze rozhraní.  
  
|Metoda|Převod|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Převede <xref:Microsoft.VisualStudio.Text.ITextBuffer> do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Převede <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Převede <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Převede <xref:Microsoft.VisualStudio.Text.Editor.ITextView> do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Převede <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="create-adapters"></a>Vytvořit adaptéry  
 Použijte následující metody k vytvoření adaptérů pro starší verze rozhraní.  
  
|Metoda|Převod|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pro určitou vlastnost <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Vytváření adaptérů v nespravovaném kódu  
 Všechny třídy adaptér jsou registrované na místním společně vytvořitelné a můžete vytvořit instanci pomocí `VsLocalCreateInstance()` funkce.  
  
 Všechny adaptéry jsou vytvářeny instalační sadou identifikátory GUID, které jsou definovány v *vsshlids.h* soubor *\..\VisualStudioIntegration\Common\Inc\\* složky sady Visual Studio SDK instalace. Pokud chcete vytvořit instanci VsTextBufferAdapter, použijte následující kód.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="create-adapters-in-managed-code"></a>Vytvořit adaptéry ve spravovaném kódu  
 Ve spravovaném kódu můžete vytvořit společně adaptéry stejným způsobem jako pro nespravovaný kód. Můžete také použít služby MEF, které vám umožní vytvořit a pracovat s adaptéry. Tento způsob získávání adaptér umožňuje další velice přesně kontrolovat, než budete mít, když vytvoříte společně.  
  
### <a name="to-create-an-adapter-for-ivstextview"></a>Chcete-li vytvořit adaptér pro IVsTextView  
  
1.  Přidejte odkaz na *Microsoft.VisualStudio.Editor.dll*. Ujistěte se, že `CopyLocal` je nastavena na `false`.  
  
2.  Vytvoření instance <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, následujícím způsobem.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Volání `CreateX()` metody.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="use-the-visual-studio-editor-directly-from-unmanaged-code"></a>Použití editoru Visual Studio přímo z nespravovaného kódu  
 Obor názvů Microsoft.VisualStudio.Platform.VSEditor a obor názvů Microsoft.VisualStudio.Platform.VSEditor.Interop vystavit rozhraní COM-callable jako IVx * rozhraní. Například rozhraní Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer je verzi modelu COM <xref:Microsoft.VisualStudio.Text.ITextBuffer> rozhraní. Z `IVxTextBuffer`, můžete získat přístup k vyrovnávací paměti snímků, mění vyrovnávací paměť, naslouchat událostem změny textu ve vyrovnávací paměti a vytvořte body sledování a rozsahy. Následující kroky ukazují, jak přistupovat `IVxTextBuffer` z `IVsTextBuffer`.  
  
### <a name="to-get-an-ivxtextbuffer"></a>Chcete-li získat IVxTextBuffer  
  
1.  Definice IVx\* rozhraní jsou v *VSEditor.h* soubor *\..\VisualStudioIntegration\Common\Inc\\* složky sady Visual Studio Instalace sady SDK.  
  
2.  Následující kód vytvoří instanci vyrovnávací paměť textu s použitím `IVsUserData->GetData()` metody. V následujícím kódu `pData` je ukazatel `IVsUserData` objektu.  
  
    ```cpp  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="use-visual-studio-editor-services-in-a-non-mef-component"></a>Pomocí editoru služby Visual Studio v komponentě rozhraní MEF  
 Pokud máte existující komponentu spravovaný kód, který nepoužívá MEF a chcete použít služby editoru sady Visual Studio, musíte přidat odkaz na sestavení, které obsahuje ComponentModelHost VSPackage a získat jeho SComponentModel službu.  
  
### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Pro zpracování součástí editoru sady Visual Studio z komponenty – rozhraní MEF  
  
1.  Přidejte odkaz na *Microsoft.VisualStudio.ComponentModelHost.dll* sestavení v *\..\Common7\IDE\\* složce instalace sady Visual Studio. Ujistěte se, že `CopyLocal` je nastavena na `false`.  
  
2.  Přidat soukromé `IComponentModel` člena třídy, ve které chcete použít editor služby Visual Studio, následujícím způsobem.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Vytvoření instance komponenty modelu v metodě inicializace pro komponentu.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Potom můžete získat kterékoli služby editoru sady Visual Studio voláním `IComponentModel.GetService<T>()` metody pro požadovanou službu.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
