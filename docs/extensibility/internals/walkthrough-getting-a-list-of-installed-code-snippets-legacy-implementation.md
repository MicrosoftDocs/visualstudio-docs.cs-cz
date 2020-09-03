---
title: Získání seznamu nainstalovaných fragmentů kódu (starší verze) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d5ef857973555c4b2d201f98957bd2c39328b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703653"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Návod: Získání seznamu nainstalovaných fragmentů kódu (implementace starší verze)
Fragment kódu je část kódu, kterou lze vložit do zdrojové vyrovnávací paměti buď pomocí příkazu nabídky (který umožňuje výběr ze seznamu nainstalovaných fragmentů kódu), nebo výběrem zástupce fragmentu ze seznamu dokončení technologie IntelliSense.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>Metoda získá všechny fragmenty kódu pro identifikátor GUID konkrétního jazyka. Zástupce pro tyto fragmenty kódu mohou být vloženy do seznamu dokončení technologie IntelliSense.

 V tématu [Podpora fragmentů kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) najdete podrobné informace o implementaci fragmentů kódu ve službě Managed Package Framework (MPF) Language.

### <a name="to-retrieve-a-list-of-code-snippets"></a>Načtení seznamu fragmentů kódu

1. Následující kód ukazuje, jak získat seznam fragmentů kódu pro daný jazyk. Výsledky jsou uloženy v poli <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> struktur. Tato metoda používá statickou <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodu pro získání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> rozhraní ze <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> služby. Můžete ale také použít poskytovatele služeb, který je přidělený vašemu VSPackage, a volat <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> metodu.

    ```csharp
    using System;
    using System.Collections;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Package;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.TextManager.Interop;

    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service
    namespace TestLanguage
    {
        class TestLanguageService : LanguageService
        {
            private void GetSnippets(Guid languageGuid,
                                     ref ArrayList expansionsList)
            {
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));
                if (textManager != null)
                {
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;
                    if (textManager2 != null)
                    {
                        IVsExpansionManager expansionManager = null;
                        textManager2.GetExpansionManager(out expansionManager);
                        if (expansionManager != null)
                        {
                            // Tell the environment to fetch all of our snippets.
                            IVsExpansionEnumeration expansionEnumerator = null;
                            expansionManager.EnumerateExpansions(languageGuid,
                            0,     // return all info
                            null,    // return all types
                            0,     // return all types
                            1,     // include snippets without types
                            0,     // do not include duplicates
                            out expansionEnumerator);
                            if (expansionEnumerator != null)
                            {
                                // Cache our expansions in a VsExpansion array
                                uint count   = 0;
                                uint fetched = 0;
                                VsExpansion expansionInfo = new VsExpansion();
                                IntPtr[] pExpansionInfo   = new IntPtr[1];

                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));

                                expansionEnumerator.GetCount(out count);
                                for (uint i = 0; i < count; i++)
                                {
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);
                                    if (fetched > 0)
                                    {
                                        // Convert the returned blob of data into a structure that can be read in managed code.
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));

                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))
                                        {
                                            expansionsList.Add(expansionInfo);
                                        }
                                    }
                                }
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);
                            }
                        }
                    }
                }
            }
        }
    }
    ```

### <a name="to-call-the-getsnippets-method"></a>Volání metody getfragments

1. Následující metoda ukazuje, jak zavolat `GetSnippets` metodu při dokončení operace analýzy. <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>Metoda je volána po operaci analýzy, která byla zahájena s důvodem <xref:Microsoft.VisualStudio.Package.ParseReason> .

> [!NOTE]
> `expansionsList`Seznam polí je uložen v mezipaměti z důvodů výkonu. Změny fragmentů kódu se v seznamu neprojeví, dokud se služba jazyka nezastaví a znovu nenačte (například zastavením a restartováním [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ).

```csharp
class TestLanguageService : LanguageService
{
    private ArrayList expansionsList;

    public override void OnParseComplete(ParseRequest req)
    {
        if (this.expansionsList == null)
        {
            this.expansionsList = new ArrayList();
            GetSnippets(this.GetLanguageServiceGuid(),
                ref this.expansionsList);
        }
    }
}
```

### <a name="to-use-the-snippet-information"></a>Použití informací o fragmentu

1. Následující kód ukazuje, jak použít informace o fragmentu vracené `GetSnippets` metodou. `AddSnippets`Metoda je volána z analyzátoru v reakci na libovolný důvod analýzy, který se používá k naplnění seznamu fragmentů kódu. To by mělo proběhnout po prvním provedení úplného rozboru.

     `AddDeclaration`Metoda vytvoří seznam deklarací, které jsou později zobrazeny v seznamu pro doplňování.

     `TestDeclaration`Třída obsahuje všechny informace, které mohou být zobrazeny v seznamu pro doplňování, i typ deklarace.

    ```csharp
    class TestAuthoringScope : AuthoringScope
    {
        public void AddDeclarations(TestDeclaration declaration)
        {
            if (m_declarations == null)
                m_declarations = new List<TestDeclaration>();
            m_declarations.Add(declaration);
         }
    }
    class TestDeclaration
    {
        private string m_name;
        private string m_description;
        private string m_type;

        public TestDeclaration(string name, string desc, string type)
        {
            m_name = name;
            m_description = desc;
            m_type = type;
        }

    class TestLanguageService : LanguageService
    {
        internal void AddSnippets(ref TestAuthoringScope scope)
        {
            if (this.expansionsList != null && this.expansionsList.Count > 0)
            {
                int count = this.expansionsList.Count;
                for (int i = 0; i < count; i++)
                {
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,
                         expansionInfo.description,
                         "snippet"));
                }
            }
        }
    }

    ```

## <a name="see-also"></a>Viz také
- [Podpora pro fragmenty kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
