---
title: Registrace služby staršího jazyka1 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91776382fff1818986049558c9d86e8fce4d0dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705894"
---
# <a name="registering-a-legacy-language-service"></a>Registrace služby starší verze jazyka
V rámci spravovaného balíčku (MPF) je jazyková služba nabízena balíčkem VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (viz [VSPackages)](../../extensibility/internals/vspackages.md)a je registrována přidáním klíčů registru a položek. Tento proces registrace se provádí částečně během instalace a částečně za běhu.

## <a name="register-the-language-service-by-using-attributes"></a>Registrace jazykové služby pomocí atributů
 Následující atributy se používají k registraci jazykové služby.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Tyto atributy jsou vysvětleny níže

### <a name="provideserviceattribute"></a>Atribut ProvideServiceAttribute
 Tento atribut registruje službu jazyka jako službu.

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

### <a name="providelanguageserviceattribute"></a>Atribut ProvideLanguageServiceAttribute
 Tento atribut registruje službu jazyka konkrétně jako jazykovou službu. Umožňuje nastavit možnosti, které určují funkce, které nabízí služba jazyka. Příklad ukazuje podmnožinu možností, které může jazyková služba poskytnout. Úplnou sadu možností jazykových <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>služeb naleznete v tématu .

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

### <a name="providelanguageextensionattribute"></a>Poskytnout atribut _LanguageExtensionAttribute
 Tento atribut přidruží jazykovou službu k příponě souboru. Při každém načtení souboru s tímto rozšířením je v libovolném projektu spuštěna a použita služba jazyka k zobrazení obsahu souboru.

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

### <a name="providelanguagecodeexpansionattribute"></a>Poskytnout atribut Rozšíření kódu_jazyce
 Tento atribut registruje umístění, ze kterého jsou získány šablony rozšíření kódu nebo fragmentu. Tyto informace jsou používány **prohlížečem fragmentů kódu** a editorem při vložení fragmentu kódu do zdrojového souboru.

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

### <a name="providelanguageeditoroptionpageattribute"></a>Poskytnout atribut LanguageEditorOptionPageAttribute
 Tento atribut zaregistruje stránku vlastností, která se má zobrazit v dialogovém okně **Možnosti** v kategorii **Textový editor.** Použijte jeden z těchto atributů pro každou stránku, která se zobrazí pro vaši jazykovou službu. Pokud potřebujete uspořádat stránky do stromové struktury, použijte další atributy k definování každého uzlu stromu.

### <a name="example"></a>Příklad
 Tento příklad ukazuje dvě stránky **vlastností, Možnosti** a **Odsazení**a jeden uzel, který obsahuje druhou stránku vlastnosti.

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

## <a name="proffer-the-language-service-at-run-time"></a>Proffer jazyková služba v době běhu
 Po načtení jazykového balíčku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je nutné sdělit, že je jazyková služba připravena. Můžete to provést tím, že nabízí službu. To se provádí <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> v metodě. Kromě toho je třeba spustit časovač, který volá službu jazyka během období nečinnosti, takže lze provést analýzu na pozadí. Tento časovač nečinnosti se také používá k aktualizaci <xref:Microsoft.VisualStudio.Package.DocumentProperties> vlastností dokumentu, pokud jste implementovali některé prostřednictvím třídy. Chcete-li podporovat časovač, váš balíček musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> rozhraní (pouze <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> metoda musí být plně implementována; zbývající metody mohou vrátit výchozí hodnoty).

### <a name="example"></a>Příklad
 Tento příklad ukazuje typický přístup k nabízení služby a poskytování časovače nečinnosti.

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
