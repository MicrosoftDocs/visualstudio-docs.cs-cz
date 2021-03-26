---
title: 'Postupy: registrace knihovny pomocí Správce objektů | Microsoft Docs'
description: Naučte se registrovat knihovnu pomocí Správce objektů sady Visual Studio, abyste mohli zobrazovat symboly v nástrojích pro procházení, jako je Zobrazení tříd a Prohlížeč objektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b83b68af4c026c40aca7969068ad015a61d64321
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086063"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Postupy: registrace knihovny pomocí Správce objektů
Nástroje pro procházení symbolů, jako je **zobrazení tříd**, **Prohlížeč objektů**, **prohlížeč volání** a **hledání výsledků symbolů**, umožňují zobrazit symboly v projektu nebo externích součástech. Mezi symboly patří obory názvů, třídy, rozhraní, metody a další prvky jazyka. Knihovny sledují tyto symboly a zpřístupňují je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] správci objektů, který tyto nástroje naplní daty.

 Správce objektů sleduje všechny dostupné knihovny. Před zadáním symbolů pro nástroje pro procházení symbolů se musí každá knihovna zaregistrovat u správce objektů.

 Obvykle je knihovna registrována při načtení balíčku VSPackage. Dá se to ale udělat v jinou dobu podle potřeby. Zrušíte registraci knihovny, když se VSPackage vypíná.

 K registraci knihovny použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> metodu. Pro spravovanou knihovnu kódu použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodu.

 Chcete-li zrušit registraci knihovny, použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> metodu.

 Chcete-li získat odkaz na správce objektů, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> předejte <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID služby `GetService` metodě.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Registrace a zrušení registrace knihovny pomocí Správce objektů

### <a name="to-register-a-library-with-the-object-manager"></a>Registrace knihovny pomocí Správce objektů

1. Vytvořte knihovnu.

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. Získejte odkaz na objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> typu a zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodu.

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>Zrušení registrace knihovny pomocí Správce objektů

1. Získejte odkaz na objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> typu a zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> metodu.

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>Viz také
- [Rozšíření služby starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Podpora nástrojů pro procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Postupy: vystavení seznamů symbolů poskytovaných knihovnou správci objektů](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
