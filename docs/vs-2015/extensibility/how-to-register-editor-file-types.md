---
title: 'Postupy: registrace typů souborů Editor | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 39b1cde8dec71df9cb85bf737c23c883fbdcd615
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777255"
---
# <a name="how-to-register-editor-file-types"></a>Postupy: registrace Editor typů souborů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejjednodušší způsob, jak zaregistrovat editor typů souborů se s použitím atributů registrace k dispozici jako součást [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] managed package framework (MPF) třídy. Při implementaci vašeho balíčku v nativním [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], můžete také napsat skript registru, která se registruje editor a související rozšíření.  
  
## <a name="registration-using-mpf-classes"></a>Registrace pomocí třídy MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Editor typů souborů pomocí třídy MPF registrace  
  
1.  Zadejte <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> třídy s příslušnými parametry pro editor ve třídě vašeho balíčku VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Kde ". Ukázka"je rozšíření, který je registrovaný pro tento editor a"32"je její úroveň priority.  
  
     `projectGuid` Je identifikátor GUID pro soubor různé typy, definované v <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Poskytuje různé přípony, tak, aby výsledný soubor nebude jako součást procesu sestavení.  
  
     `TemplateDir` představuje složku obsahující soubory šablon, které jsou součástí ukázkové spravované základní editor.  
  
     `NameResourceID` je definována v souboru Resources.h BasicEditorUI projektu a identifikuje editor jako "Moje editoru".  
  
2.  Přepsat <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
     Ve vaší implementaci <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody, volání <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> a předáte instanci továrna pro editaci jako znázorněno níže.  
  
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
  
     Tento krok zaregistruje objekt factory editoru a přípony souborů editoru.  
  
3.  Zrušit registraci objekty pro vytváření editoru.  
  
     Objekty pro vytváření editoru jsou automaticky odregistrovat při uvolnění sady VSPackage. Pokud objekt factory editoru, který implementuje <xref:System.IDisposable> rozhraní, jeho `Dispose` metoda se volá, když byla Neregistrovaný objekt pro vytváření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="registration-using-a-registry-script"></a>Registrace pomocí skript registru  
 Zaregistrovat objekty pro vytváření editoru a typy souborů v nativním [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] se provádí pomocí skriptu registru k zápisu do registru systému windows, jak je znázorněno v následující.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>K registraci skripty registru typy souborů editoru  
  
1.  Ve vašem skriptu registru definovat objekt pro vytváření editoru a objektu pro vytváření editoru řetězec GUID jak je znázorněno `GUID_BscEditorFactory` část tento skript registru. Navíc definujte rozšíření a prioritu rozšíření editoru:  
  
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
  
     Přípona souboru editoru v tomto příkladu je označen jako ".rtf" a jeho priorita je "50". Identifikátor GUID řetězce jsou definovány v souboru Resource.h BscEdit ukázkového projektu.  
  
2.  Registrace sady VSPackage.  
  
3.  Zaregistrujte objekt pro vytváření editoru.  
  
     Objekt factory editoru je registrován v <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementace.  
  
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
  
     Identifikátor GUID řetězce jsou definovány v souboru Resource.h BscEdit projektu.

