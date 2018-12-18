---
title: Registrace starší verze jazyka1 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03e851f8da251268a44e62f9b8071648bc27a870
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821302"
---
# <a name="registering-a-legacy-language-service"></a>Registrace služby starší verze jazyka
V rámci spravovaného balíčku (MPF) je služba jazyka proffered pomocí VSPackage (viz [rozšíření VSPackages](../../extensibility/internals/vspackages.md)) a je registrovaný pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] přidáním klíče registru a položky. Tento proces registrace se provádí v částečně během instalace a částečně v době běhu.  
  
## <a name="register-the-language-service-by-using-attributes"></a>Zaregistrovat službu jazyka pomocí atributů  
 Následující atributy se používají k registraci služba jazyka.  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
  Tyto atributy jsou vysvětleny níže  
  
### <a name="provideserviceattribute"></a>ProvideServiceAttribute  
 Tento atribut zaregistruje vaše jazykové služby jako služba.  
  
### <a name="example"></a>Příklad  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideServiceAttribute(typeof(TestLanguageService),  
                             ServiceName = "Test Language Service")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute  
 Tento atribut zaregistruje vaše služba jazyka konkrétně jako služba jazyka. Umožňuje nastavit možnosti, které určují funkce, které nabízí služby jazyka. Tento příklad zobrazuje podmnožinu možností, které nabízí služba jazyka. Úplnou sadu možností služeb jazyka, najdete v části <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.  
  
### <a name="example"></a>Příklad  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),  
                             "Test Language",  
                             106,             // resource ID of localized language name  
                             CodeSense = true,             // Supports IntelliSense  
                             RequestStockColors = false,   // Supplies custom colors  
                             EnableCommenting = true,      // Supports commenting out code  
                             EnableAsyncCompletion = true  // Supports background parsing  
                             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute  
 Tento atribut přidruží vaše služba jazyka příponu souboru. Pokaždé, když je načten soubor touto příponou v jakémkoli projektu, vaše služba jazyka spuštěná a slouží k zobrazení obsahu souboru.  
  
### <a name="example"></a>Příklad  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),  
                                       ".Testext")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute  
 Tento atribut zaregistruje umístění z kódu, které jsou získány rozšíření nebo fragment kódu šablon. Tyto informace používá **prohlížeč fragmenty kódu** a Editor při vložení fragmentu kódu do zdrojového souboru.  
  
### <a name="example"></a>Příklad  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageCodeExpansionAttribute(  
             typeof(TestLanguageService),  
             "Test Language", // Name of language used as registry key.  
             106,           // Resource ID of localized name of language service.  
             "testlanguage",  // language key used in snippet templates.  
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index  
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +  
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute  
 Tento atribut zaregistruje stránky vlastností, který se má zobrazit v **možnosti** dialogového okna **textový Editor** kategorie. Použijte jednu z těchto atributů pro každou stránku, který se má zobrazit pro vaši službu jazyka. Pokud potřebujete k uspořádání stránek ve stromové struktuře, použijte další atributy definovat každý uzel stromu.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje dvě stránky vlastností **možnosti** a **Indenting**a jeden uzel, který obsahuje druhou stránku vlastností.  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Options",      // Registry key name for property page  
             "#242",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Advanced",     // Registry key name for node  
             "#243",         // Localized name of node  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             @"Advanced\Indenting",     // Registry key name for property page  
             "#244",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
## <a name="proffer-the-language-service-at-runtime"></a>Nabídnout službu jazyka za běhu  
 Při načítání jazykový balíček, je zapotřebí sdělit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , že je jazyková služba je připravená. Můžete to provést proffering služby. To se provádí v <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody. Kromě toho budete muset spustit časovač, který volá vaše služba jazyka během období nečinnosti tak dosáhnete analýzu na pozadí. Tento časovač nečinnosti slouží také k aktualizaci vlastností dokumentu, pokud jste implementovali žádné prostřednictvím <xref:Microsoft.VisualStudio.Package.DocumentProperties> třídy. Za účelem podpory časovač, musí implementovat váš balíček <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> rozhraní (pouze <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> metoda musí být plně implementovány; zbývající metody může vrátit výchozí hodnoty).  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje obvyklý postup, jak proffering služby a poskytnutí nečinnosti časovače.  
  
```csharp  
  
using System;  
using System.Runtime.InteropServices;  
using System.ComponentModel.Design;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.OLE.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,  
        AutoOutlining = true,  
        EnableCommenting = true,  
        MatchBraces = true,  
        ShowMatchingBrace = true)]  
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package  
  
    public class TestLanguagePackage : Package, IOleComponent  
    {  
        private uint m_componentID;  
  
        protected override void Initialize()  
        {  
            base.Initialize();  // required  
  
            // Proffer the service.  
            IServiceContainer serviceContainer = this as IServiceContainer;  
            TestLanguageService langService      = new TestLanguageService();  
            langService.SetSite(this);  
            serviceContainer.AddService(typeof(TestLanguageService),  
                                        langService,  
                                        true);  
  
            // Register a timer to call our language service during  
            // idle periods.  
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                       as IOleComponentManager;  
            if (m_componentID == 0 && mgr != null)  
            {  
                OLECRINFO[] crinfo = new OLECRINFO[1];  
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));  
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |  
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;  
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |  
                                              (uint)_OLECADVF.olecadvfRedrawOff |  
                                              (uint)_OLECADVF.olecadvfWarningsOff;  
                crinfo[0].uIdleTimeInterval = 1000;  
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);  
            }  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (m_componentID != 0)  
            {  
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                           as IOleComponentManager;  
                if (mgr != null)  
                {  
                    int hr = mgr.FRevokeComponent(m_componentID);  
                }  
                m_componentID = 0;  
            }  
  
            base.Dispose(disposing);  
        }  
  
        #region IOleComponent Members  
  
        public int FDoIdle(uint grfidlef)  
        {  
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;  
            // Use typeof(TestLanguageService) because we need to  
            // reference the GUID for our language service.  
            LanguageService service = GetService(typeof(TestLanguageService))  
                                      as LanguageService;  
            if (service != null)  
            {  
                service.OnIdle(bPeriodic);  
            }  
            return 0;  
        }  
  
        public int FContinueMessageLoop(uint uReason,  
                                        IntPtr pvLoopData,  
                                        MSG[] pMsgPeeked)  
        {  
            return 1;  
        }  
  
        public int FPreTranslateMessage(MSG[] pMsg)  
        {  
            return 0;  
        }  
  
        public int FQueryTerminate(int fPromptUser)  
        {  
            return 1;  
        }  
  
        public int FReserved1(uint dwReserved,  
                              uint message,  
                              IntPtr wParam,  
                              IntPtr lParam)  
        {  
            return 1;  
        }  
  
        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)  
        {  
            return IntPtr.Zero;  
        }  
  
        public void OnActivationChange(IOleComponent pic,  
                                       int fSameComponent,  
                                       OLECRINFO[] pcrinfo,  
                                       int fHostIsActivating,  
                                       OLECHOSTINFO[] pchostinfo,  
                                       uint dwReserved)  
        {  
        }  
  
        public void OnAppActivate(int fActive, uint dwOtherThreadID)  
        {  
        }  
  
        public void OnEnterState(uint uStateID, int fEnter)  
        {  
        }  
  
        public void OnLoseActivation()  
        {  
        }  
  
        public void Terminate()  
        {  
        }  
  
        #endregion  
    }  
}   
```