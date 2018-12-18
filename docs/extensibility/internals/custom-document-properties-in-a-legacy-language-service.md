---
title: Vlastní vlastnosti dokumentu ve službě starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 473b3970fe8a7d7e65b8e569420b2be6455a3d14
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499081"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Vlastní vlastnosti dokumentu ve službě starší verze jazyka
Vlastnosti dokumentu lze zobrazit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **vlastnosti** okna. Programovací jazyky obvykle nemají vlastnosti přidružené k jednotlivým zdrojové soubory. Ale podporuje vlastnosti dokumentu, které mají vliv na kódování, schéma a šablony stylů XML.  
  
## <a name="discussion"></a>Diskuse  
 Pokud váš jazyk přizpůsobených vlastností dokumentu, musí být odvozen ze třídy <xref:Microsoft.VisualStudio.Package.DocumentProperties> třídy a implementujte nezbytné vlastnosti v odvozené třídě.  
  
 Kromě toho vlastnosti dokumentu jsou obvykle uložená ve zdrojovém souboru, samotné. To vyžaduje služba jazyka analyzovat informace o vlastnosti ze zdrojového souboru pro zobrazení v **vlastnosti** okno a aktualizovat zdrojový soubor, když ke změně vlastnosti dokumentu v  **Vlastnosti** okna.  
  
## <a name="customize-the-documentproperties-class"></a>Upravit skupiny DocumentProperties třídy  
 Pro podporu přizpůsobených vlastností dokumentu, musí být odvozen ze třídy <xref:Microsoft.VisualStudio.Package.DocumentProperties> třídu a přidejte libovolný počet vlastností podle potřeby. Musí také zadat atributy uživatele a uspořádávat je v **vlastnosti** zobrazení okna. Pokud je vlastnost pouze `get` přístupový objekt, zobrazuje se jen pro čtení v **vlastnosti** okna. Pokud je vlastnost obě `get` a `set` přístupové objekty, vlastnost je také možné aktualizovat v **vlastnosti** okna.  
  
### <a name="example"></a>Příklad  
 Tady je příklad třídy odvozené z <xref:Microsoft.VisualStudio.Package.DocumentProperties>, zobrazují dvě vlastnosti `Filename` a `Description`. Při aktualizaci vlastnosti, vlastní metodu na <xref:Microsoft.VisualStudio.Package.LanguageService> třída se nazývá Zapisovat vlastnosti ve zdrojovém souboru.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestDocumentProperties : DocumentProperties  
    {  
        private string m_filename;  
        private string m_description;  
  
        public TestDocumentProperties(CodeWindowManager mgr)  
            : base(mgr)  
        {  
        }  
  
        // Helper function to initialize this property without  
        // going through the FileName property (which does a lot  
        // more than we need when the filename is set).  
        public void SetFileName(string filename)  
        {  
            m_filename = filename;  
        }  
  
        // Helper function to initialize this property without  
        // going through the Description property (which does a lot  
        // more than we need when the description is set).  
        public void SetDescription(string description)  
        {  
            m_description = description;  
        }  
  
        ////////////////////////////////////////////////////////////  
        // The document properties  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Name of the file")]  
        [DisplayNameAttribute("Filename")]  
        public string FileName  
        {  
            get { return m_filename; }  
            set  
            {  
               if (value != m_filename)  
               {  
                    m_filename = value;  
                    SetPropertyValue("Filename", m_filename);  
               }  
            }  
        }  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Description of the file")]  
        [DisplayNameAttribute("Description")]  
        public string Description  
        {  
            get { return m_description; }  
            set  
            {  
                if (value != m_description)  
                {  
                    m_description = value;  
                    SetPropertyValue("Description", m_description);  
                }  
            }  
        }  
  
        ///////////////////////////////////////////////////////////  
        // Private methods.  
  
        private void SetPropertyValue(string propertyName, string propertyValue)  
        {  
            Source src = this.GetSource();  
            if (src != null)  
            {  
                TestLanguageService service = src.LanguageService as TestLanguageService;  
                if (service != null)  
                {  
                    // Set the property in to the source file.  
                    service.SetPropertyValue(src, propertyName, propertyValue);  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="instantiate-the-custom-documentproperties-class"></a>Vytvoření vlastní instance třídy skupiny DocumentProperties  
 K vytvoření instance třídy vlastnosti vaší vlastní šablony dokumentů, je nutné přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> metodu ve vaší verzi <xref:Microsoft.VisualStudio.Package.LanguageService> třídy pro vracení jedna instance vaší <xref:Microsoft.VisualStudio.Package.DocumentProperties> třídy.  
  
### <a name="example"></a>Příklad  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        private TestDocumentProperties m_documentProperties;  
  
        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)  
        {  
            if (m_documentProperties == null)  
            {  
                m_documentProperties = new TestDocumentProperties(mgr);  
            }  
            return m_documentProperties;  
        }  
    }  
}  
```  
  
## <a name="properties-in-the-source-file"></a>Vlastnosti ve zdrojovém souboru  
 Protože vlastnosti dokumentu jsou obvykle konkrétní do zdrojového souboru, hodnoty jsou uloženy ve zdrojovém souboru, samotné. To vyžaduje podporu analyzátoru jazyka nebo skener definovat tyto vlastnosti. Například vlastnosti dokumentu XML jsou uloženy na uzlu root. Při změně hodnoty na kořenový uzel **vlastnosti** byly změněny hodnoty okna a kořenový uzel se aktualizuje v editoru.  
  
### <a name="example"></a>Příklad  
 V tomto příkladu ukládá vlastnosti `Filename` a `Description` v prvních dvou řádků zdrojového souboru a součástí hlavičku speciální komentář jako:  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 Tento příklad ukazuje dvě metody, které jsou potřeba k získání a nastavení vlastnosti dokumentu z první dva řádky zdrojového souboru, jak jsou aktualizovány vlastnosti, pokud uživatel upraví zdrojový soubor přímo. `SetPropertyValue` Metodu z příkladu, zde je stejný, jeden volat z `TestDocumentProperties` třídy, jak je znázorněno *přizpůsobení třídy skupiny DocumentProperties* oddílu.  
  
 Tento příklad používá k určení typu tokeny v prvních dvou řádků skeneru. V tomto příkladu je pouze pro ilustraci. Obvyklejší přístup k této situaci je k analýze zdrojového souboru do co se nazývá strom analýzy kde každý uzel stromu obsahuje informace o konkrétní token. Kořenový uzel by obsahovala vlastnosti dokumentu.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    // TokenType.Comment is the last item in that enumeration.  
    public enum TestTokenTypes  
    {  
        DocPropertyLine = TokenType.Comment + 1,  
        DocPropertyName,  
        DocPropertyAssign,  
        DocPropertyValue  
    }  
  
    class TestLanguageService : LanguageService  
    {  
        // Search this many lines from the beginning for properties.  
        private static int maxLinesToSearch = 2;  
  
        private TestDocumentProperties m_documentProperties;  
  
        // Called whenever a full parsing operation has completed.  
        public override void OnParseComplete(ParseRequest req)  
        {  
            if (m_documentProperties != null)  
            {  
                Source src = GetSource(req.View);  
                if (src != null)  
                {  
                    string value = GetPropertyValue(src, "Filename");  
                    m_documentProperties.SetFileName(value);  
  
                    value = GetPropertyValue(src, "Description");  
                    m_documentProperties.SetDescription(value);  
  
                    // Update the Properties Window.  
                    m_documentProperties.Refresh();  
                }  
            }  
        }  
  
        // Retrieves the specified property value from the given source.  
        public string GetPropertyValue(Source src, string propertyName)  
        {  
            string propertyValue = "";  
  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    string      line;  
                    TokenInfo[] lineInfo = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line.  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                for ( ;  
                                     tokenIndex < lineInfo.Length;  
                                     tokenIndex++)  
                                {  
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)  
                                    {  
                                        break;  
                                    }  
                                }  
                                if (tokenIndex < lineInfo.Length)  
                                {  
                                    propertyValue = src.GetText(i,  
                                                          lineInfo[tokenIndex].StartIndex,  
                                                          i,  
                                                          lineInfo[tokenIndex].EndIndex + 1);  
                                }  
                                break;  
                            }  
                        }  
                    }  
                }  
            }  
            return propertyValue;  
        }  
  
        // Sets the specified property into the given source file.  
        // Called from the TestDocumentProperties class.  
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)  
        {  
            string newLine;  
  
            if (propertyName == null || propertyName == "")  
            {  
                // No property name, so nothing to do  
                return;  
            }  
            if (propertyValue == null)  
            {  
                propertyValue = "";  
            }  
            // This is the line to be inserted.  
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);  
  
            // First, find the line on which the property belongs.  
            // If line is found, replace it.  
            // Otherwise, insert the line at the beginning of the file.  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    int         lineNumber = -1;  
                    string      line;  
                    TokenInfo[] lineInfo   = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                lineNumber = i;  
                                break;  
                            }  
                        }  
                    }  
  
                    // Set up an undo context that also handles the insert/replace.  
                    EditArray editArray = new EditArray(src,  
                                                        true,  
                                                        "Update Property");  
                    if (editArray != null)  
                    {  
                        TextSpan span = new TextSpan();  
                        if (lineNumber != -1)  
                        {  
                            // Replace line.  
                            int lineLength = 0;  
                            src.GetTextLines().GetLengthOfLine(lineNumber,  
                                                               out lineLength);  
                            span.iStartLine  = lineNumber;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = lineNumber;  
                            span.iEndIndex   = lineLength;  
                        }  
                        else  
                        {  
                            // Insert new line.  
                            span.iStartLine  = 0;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = 0;  
                            span.iEndIndex   = 0;  
                            newLine += "\n";  
                        }  
                        editArray.Add(new EditSpan(span, newLine));  
                        editArray.ApplyEdits();  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:  
 [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)