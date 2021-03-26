---
title: Registrace starší verze jazyka Service1 | Microsoft Docs
description: Přečtěte si o registraci starší verze jazykové služby ze sady VSPackage v aplikaci Visual Studio přidáním klíčů registru a záznamů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5fa94fbd514e5fb162bc569438197dd8c65444b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060767"
---
# <a name="registering-a-legacy-language-service-1"></a>Registrace služby starší verze jazyka 1
V rámci spravovaného balíčku rozhraní (MPF) je jazyková služba proffered pomocí VSPackage (viz [VSPackage](../../extensibility/internals/vspackages.md)) a je zaregistrována přidáním [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] klíčů registru a záznamů. Tento proces registrace se provádí částečně během instalace a částečně v době běhu.

## <a name="register-the-language-service-by-using-attributes"></a>Registrace jazykové služby pomocí atributů
 Následující atributy se používají k registraci jazykové služby.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Tyto atributy jsou vysvětleny níže.

### <a name="provideserviceattribute"></a>ProvideServiceAttribute
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

### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute
 Tento atribut registruje službu jazyka specificky jako službu jazyka. Umožňuje nastavit možnosti, které určují funkce, které vaše služba jazyka nabízí. V příkladu se zobrazuje podmnožina možností, kterou může poskytovat služba jazyka. Úplnou sadu možností jazykové služby najdete v tématu <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .

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
 Tento atribut přidruží službu jazyka k příponě souboru. Pokaždé, když se načte soubor s tímto rozšířením, v jakémkoli projektu se spustí vaše jazyková služba a použije se k zobrazení obsahu souboru.

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
 Tento atribut zaregistruje umístění, ze kterého jsou získány rozšíření kódu nebo šablony fragmentů. Tyto informace jsou používány **prohlížečem fragmentů kódu** a editorem při vložení fragmentu kódu do zdrojového souboru.

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
 Tento atribut zaregistruje stránku vlastností, která se má zobrazit v dialogovém okně **Možnosti** v kategorii **textový editor** . Pro každou stránku, která se má zobrazit pro vaši jazykovou službu, použijte jeden z těchto atributů. Pokud potřebujete uspořádat své stránky ve stromové struktuře, použijte další atributy k definování každého uzlu stromu.

### <a name="example"></a>Příklad
 Tento příklad ukazuje dvě stránky vlastností, **Možnosti** a **odsazení** a jeden uzel, který obsahuje druhou stránku vlastností.

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

## <a name="proffer-the-language-service-at-run-time"></a>Nabídnout službu jazyka za běhu
 Když je váš jazykový balíček načtený, musíte říct [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , že je vaše jazyková služba připravená. Provedete to tak, že Proffering službu. To se provádí v <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodě. Kromě toho je třeba spustit časovač, který volá vaši službu jazyka během nečinnosti, aby bylo možné provést analýzu na pozadí. Tento časovač nečinnosti slouží také k aktualizaci vlastností dokumentu, pokud jste provedli implementaci přes <xref:Microsoft.VisualStudio.Package.DocumentProperties> třídu. Aby bylo možné podporovat časovač, musí balíček implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> rozhraní (pouze <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> Metoda musí být plně implementována; zbývající metody mohou vracet výchozí hodnoty).

### <a name="example"></a>Příklad
 Tento příklad ukazuje typický přístup k Proffering služby a poskytnutí časovače nečinnosti.

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
