---
title: 'Postupy: registrace typů souborů editoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204121"
---
# <a name="how-to-register-editor-file-types"></a>Postupy: Registrace typů souborů editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejjednodušší způsob, jak registrovat typy souborů editoru, je použití registračních atributů, které jsou k dispozici jako součást [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] tříd třídy MPF (Managed Package Framework). Pokud balíček implementujete v nativním režimu [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , můžete také napsat skript registru, který registruje Editor a přidružená rozšíření.  
  
## <a name="registration-using-mpf-classes"></a>Registrace pomocí tříd MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Registrace typů souborů editoru pomocí tříd MPF  
  
1. Poskytněte <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> třídu příslušným parametrům pro váš Editor ve třídě VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Kde ". Ukázka "je přípona, která je zaregistrovaná pro tento editor, a" 32 "je úroveň priority.  
  
     `projectGuid`Je identifikátor GUID pro různé typy souborů definované v <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . K dispozici je typ souboru různé, takže výsledný soubor nebude součástí procesu sestavení.  
  
     `TemplateDir` představuje složku, která obsahuje soubory šablony, které jsou součástí ukázky spravovaného základního editoru.  
  
     `NameResourceID` je definována v souboru Resources. h projektu BasicEditorUI a identifikuje editor jako "můj editor".  
  
2. Přepsat <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodu.  
  
     V implementaci <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody zavolejte <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> metodu a předejte instanci objektu pro vytváření editoru, jak je znázorněno níže.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Tento krok registruje jak objekt pro vytváření editoru, tak i přípony souborů editoru.  
  
3. Zrušte registraci pro objekty editory.  
  
     Objekty pro vytváření editorů jsou při uvolnění VSPackage automaticky odregistrovány. Pokud objekt factory editoru implementuje <xref:System.IDisposable> rozhraní, `Dispose` je jeho metoda volána po zrušení registrace továrny [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>Registrace pomocí skriptu registru  
 Registrace tříd pro vytváření editorů a typů souborů v nativním formátu [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] se provádí pomocí skriptu registru pro zápis do registru Windows, jak je znázorněno v následujícím seznamu.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Registrace typů souborů editoru pomocí skriptu registru  
  
1. Ve svém skriptu registru Definujte objekt pro vytváření editoru a řetězec GUID objektu pro vytváření editoru, jak je znázorněno v `GUID_BscEditorFactory` části následujícího skriptu registru. Také definujte rozšíření a prioritu rozšíření editoru:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     Přípona souboru editoru v tomto příkladu je označena jako ". RTF" a její priorita je "50". Řetězce GUID jsou definovány v souboru Resource. h v ukázkovém projektu BscEdit.  
  
2. Zaregistrujte VSPackage.  
  
3. Zaregistrujte objekt pro vytváření editoru.  
  
     Objekt pro vytváření editoru je zaregistrován v <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementaci.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     Řetězce GUID jsou definovány v souboru Resource. h v projektu BscEdit.
