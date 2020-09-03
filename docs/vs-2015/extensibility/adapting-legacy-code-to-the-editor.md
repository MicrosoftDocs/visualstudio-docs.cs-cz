---
title: Přizpůsobení staršího kódu v editoru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184920"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Přizpůsobení zastaralého kódu editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor sady Visual Studio má mnoho funkcí, ke kterým můžete přistupovat z existujících součástí kódu. Následující pokyny ukazují, jak upravit komponentu nevyužívající rozhraní MEF, například VSPackage, pro využívání funkcí editoru. Pokyny také ukazují, jak pomocí adaptérů získat služby editoru v spravovaném i nespravovaném kódu.  
  
## <a name="editor-adapters"></a>Adaptéry editoru  
 Adaptéry pro Editor nebo překrytí jsou obálky pro objekty editoru, které také zveřejňují třídy a rozhraní v <xref:Microsoft.VisualStudio.TextManager.Interop> rozhraní API. Adaptéry můžete použít k přesunu mezi needitorské služby, například příkazy prostředí sady Visual Studio a služby editoru. (Toto je způsob, jakým je editor aktuálně hostovaný v aplikaci Visual Studio.) Adaptéry také umožňují, aby v aplikaci Visual Studio správně fungovaly starší Editor a rozšíření služeb jazyka.  
  
## <a name="using-editor-adapters"></a>Používání adaptérů editoru  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Poskytuje metody, které přepínají mezi novými rozhraními editoru a staršími rozhraními, a také metodami, které vytvářejí adaptéry.  
  
 Používáte-li tuto službu v části komponenty MEF, můžete službu naimportovat následujícím způsobem.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Chcete-li použít tuto službu v komponentě mimo rozhraní MEF, postupujte podle pokynů v části "použití služeb editoru sady Visual Studio v komponentě nevyužívající rozhraní MEF" dále v tomto tématu.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Přepínání mezi novým rozhraním API editoru a starším rozhraním API  
 Použijte následující metody pro přepínání mezi objektem editoru a starším rozhraním.  
  
|Metoda|Převod|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Převede <xref:Microsoft.VisualStudio.Text.ITextBuffer> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Převede <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> na <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Převede <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> na <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Převede <xref:Microsoft.VisualStudio.Text.Editor.ITextView> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Převede <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> na <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|  
  
## <a name="creating-adapters"></a>Vytváření adaptérů  
 K vytvoření adaptérů pro starší verze rozhraní použijte následující metody.  
  
|Metoda|Převod|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pro zadanou hodnotu <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Vytváření adaptérů v nespravovaném kódu  
 Všechny třídy adaptéru jsou registrovány tak, aby byly místní a lze je vytvořit pomocí `VsLocalCreateInstance()` funkce.  
  
 Všechny adaptéry jsou vytvořeny pomocí identifikátorů GUID, které jsou definovány v souboru Vsshlids. h v. Složka \VisualStudioIntegration\Common\Inc\ instalace sady Visual Studio SDK Chcete-li vytvořit instanci VsTextBufferAdapter, použijte následující kód.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Vytváření adaptérů ve spravovaném kódu  
 Ve spravovaném kódu můžete adaptéry společně vytvořit stejným způsobem jako popsaným pro nespravovaný kód. Můžete také použít službu MEF, která umožňuje vytvořit adaptéry a pracovat s nimi. Tento způsob získání adaptéru umožňuje podrobnější kontrolu nad tím, jak jste je vytvořili společně.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Vytvoření adaptéru pro IVsTextView  
  
1. Přidejte odkaz na Microsoft.VisualStudio.Editor.dll. Ujistěte se, že `CopyLocal` je nastavena na `false` .  
  
2. Vytvořte instanci <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , jak je znázorněno níže.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Zavolejte `CreateX()` metodu.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Použití editoru sady Visual Studio přímo z nespravovaného kódu  
 Obor názvů Microsoft. VisualStudio. Platform. VSEditor a obor názvů Microsoft. VisualStudio. Platform. VSEditor. Interop zpřístupňuje rozhraní s voláním COM jako rozhraní IVx *. Například rozhraní Microsoft. VisualStudio. Platform. VSEditor. Interop. IVxTextBuffer je verze <xref:Microsoft.VisualStudio.Text.ITextBuffer> rozhraní COM rozhraní. Z nástroje `IVxTextBuffer` můžete získat přístup k snímkům vyrovnávací paměti, upravit vyrovnávací paměť, naslouchat událostem změny textu ve vyrovnávací paměti a vytvořit body sledování a rozsahy. Následující kroky ukazují, jak získat přístup k `IVxTextBuffer` z `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Získání IVxTextBuffer  
  
1. Definice pro rozhraní IVx * jsou v souboru VSEditor. h v.. Složka \VisualStudioIntegration\Common\Inc\ instalace sady Visual Studio SDK  
  
2. Následující kód vytvoří instanci textové vyrovnávací paměti pomocí `IVsUserData->GetData()` metody. V následujícím kódu `pData` je ukazatel na `IVsUserData` objekt.  
  
    ```  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Použití služeb editoru sady Visual Studio v komponentě nevyužívající rozhraní MEF  
 Máte-li existující komponentu spravovaného kódu, která nepoužívá rozhraní MEF a chcete použít služby editoru sady Visual Studio, je nutné přidat odkaz na sestavení, které obsahuje rozhraní VSPackage ComponentModelHost a získat jeho službu SComponentModel.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Používání komponent editoru aplikace Visual Studio z komponenty mimo rozhraní MEF  
  
1. Přidejte odkaz na sestavení Microsoft.VisualStudio.ComponentModelHost.dll v.. Složka \Common7\IDE\ instalace sady Visual Studio Ujistěte se, že `CopyLocal` je nastavena na `false` .  
  
2. Přidejte soukromého `IComponentModel` člena do třídy, ve které chcete použít služby sady Visual Studio editor, následovně.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Vytvořte instanci modelu komponenty v inicializační metodě pro komponentu.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Potom můžete získat libovolnou ze služeb editoru sady Visual Studio voláním `IComponentModel.GetService<T>()` metody pro službu, kterou požadujete.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
