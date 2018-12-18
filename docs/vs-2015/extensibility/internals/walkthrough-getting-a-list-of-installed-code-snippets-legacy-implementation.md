---
title: 'Návod: Získání seznamu nainstalované fragmenty kódu (implementace starší verze) | Dokumentace Microsoftu'
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
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8d132de9773614b966b6fe3a7ae84392fba4f35
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759982"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Návod: Získání seznamu nainstalovaných fragmentů kódu (implementace starší verze)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fragment kódu je část kódu, který může být vložen do zdrojové vyrovnávací paměti pomocí příkazu nabídky (která umožňuje vybrat ze seznamu nainstalovaných fragmentů kódu,) nebo pomocí zástupce fragment výběrem ze seznamu doplňování technologie IntelliSense.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Metoda získá všechny fragmenty kódu pro konkrétní jazyk identifikátor GUID. Klávesové zkratky pro tyto fragmenty kódu lze vložit do seznamu doplňování technologie IntelliSense.  
  
 Zobrazit [podpora pro fragmenty kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) podrobnosti implementace fragmentů kódu ve službě jazyka spravovaného balíčku rozhraní framework (MPF).  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>K načtení seznamu fragmentů kódu  
  
1.  Následující kód ukazuje, jak získat seznam fragmenty kódu pro daný jazyk. Výsledky jsou uloženy v poli <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> struktury. Tato metoda používá statickou <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodu k získání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> rozhraní z <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> služby. Ale můžete také použít poskytovatele služeb na VSPackage a volání <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> metody.  
  
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
  
### <a name="to-call-the-getsnippets-method"></a>Volání metody GetSnippets  
  
1.  Následující metoda ukazuje, jak volat `GetSnippets` metoda po dokončení operace analýzy. <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> Metoda je volána pro provedení operace analýzy, která byla spuštěna s odůvodněním <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
>  `expansionsList` Pole listis uložené v mezipaměti z důvodů výkonu. Změny fragmenty kódu se neprojeví v seznamu, dokud služba jazyka je zastavit a znovu načíst (třeba podle zastavení a restartování [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]).  
  
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
  
### <a name="to-use-the-snippet-information"></a>Použít informace o fragmentu kódu  
  
1.  Následující kód ukazuje, jak použít informace o fragmentu kódu, vrácené `GetSnippets` metody. `AddSnippets` Metoda je volána z analyzátor v reakci na z jakéhokoli důvodu analýzy, který se používá k naplnění seznamu fragmentů kódu. To má být provedena po úplné analýzy byla provedena poprvé.  
  
     `AddDeclaration` Metoda sestaví seznam deklarací, které se později zobrazí v seznamu dokončení.  
  
     `TestDeclaration` Třída obsahuje všechny informace, které lze zobrazit v seznamu dokončení, stejně jako typ deklarace.  
  
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
 [Podpora pro fragmenty kódu ve službě starší verze jazyka](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

