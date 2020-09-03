---
title: Vlastní vlastnosti dokumentu ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b3db7f4cfa45ea96e3da3056f39c2a5c78a25ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708969"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Vlastní vlastnosti dokumentu ve službě starší verze jazyka
Vlastnosti dokumentu lze zobrazit v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] okně **vlastnosti** . Programovací jazyky obecně nemají vlastnosti spojené s jednotlivými zdrojovými soubory. XML však podporuje vlastnosti dokumentu, které mají vliv na kódování, schéma a šablonu stylů.

## <a name="discussion"></a>Diskuse
 Pokud jazyk potřebuje vlastní vlastnosti dokumentu, musíte z třídy odvodit třídu <xref:Microsoft.VisualStudio.Package.DocumentProperties> a implementovat potřebné vlastnosti pro odvozenou třídu.

 Kromě toho se vlastnosti dokumentu většinou ukládají do samotného zdrojového souboru. Tato operace vyžaduje, aby služba jazyka analyzovala informace o vlastnostech ze zdrojového souboru pro zobrazení v okně **vlastnosti** a aktualizovala zdrojový soubor při změně vlastností dokumentu v okně **vlastnosti** .

## <a name="customize-the-documentproperties-class"></a>Přizpůsobení třídy skupiny DocumentProperties
 Pro podporu vlastních vlastností dokumentu musíte z třídy odvodit třídu <xref:Microsoft.VisualStudio.Package.DocumentProperties> a přidat tolik vlastností, kolik potřebujete. Měli byste také dodat atributy uživatele a uspořádat je v zobrazení okna **vlastnosti** . Pokud má vlastnost pouze `get` přistupující objekt, zobrazí se v okně **vlastnosti** jako jen pro čtení. Pokud má vlastnost oba i `get` `set` přistupující objekty, lze vlastnost také aktualizovat v okně **vlastnosti** .

### <a name="example"></a>Příklad
 Tady je ukázková třída odvozená z <xref:Microsoft.VisualStudio.Package.DocumentProperties> , která zobrazuje dvě vlastnosti `Filename` a `Description` . Když je vlastnost aktualizována, <xref:Microsoft.VisualStudio.Package.LanguageService> je volána vlastní metoda třídy pro zápis vlastnosti do zdrojového souboru.

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

## <a name="instantiate-the-custom-documentproperties-class"></a>Vytvoření instance vlastní třídy skupiny DocumentProperties
 Chcete-li vytvořit instanci vlastní třídy dokumentu vlastností, je nutné přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> metodu ve vaší verzi třídy, <xref:Microsoft.VisualStudio.Package.LanguageService> aby vracela jedinou instanci vaší <xref:Microsoft.VisualStudio.Package.DocumentProperties> třídy.

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
 Vzhledem k tomu, že vlastnosti dokumentu jsou obvykle specifické pro zdrojový soubor, jsou hodnoty uloženy do samotného zdrojového souboru. K definování těchto vlastností se vyžaduje podpora analyzátoru jazyka nebo skeneru. Například vlastnosti dokumentu XML jsou uloženy v kořenovém uzlu. Hodnoty v kořenovém uzlu jsou upraveny při změně hodnot okna **vlastnosti** a kořenový uzel je aktualizován v editoru.

### <a name="example"></a>Příklad
 V tomto příkladu jsou uloženy vlastnosti `Filename` a `Description` v prvních dvou řádcích zdrojového souboru vložené do hlavičky speciálního komentáře, jako:

```
//!Filename = file.testext
//!Description = A sample file
```

 Tento příklad ukazuje dvě metody potřebné pro získání a nastavení vlastností dokumentu z prvních dvou řádků zdrojového souboru a také způsob aktualizace vlastností, pokud uživatel změní zdrojový soubor přímo. `SetPropertyValue`Metoda v příkladu, která je zde uvedena, je stejná jako ta, která je volána z `TestDocumentProperties` třídy, jak je znázorněno v oddílu *přizpůsobení třídy skupiny DocumentProperties* .

 V tomto příkladu se používá skener k určení typu tokenů v prvních dvou řádcích. Tento příklad je určen pouze pro ilustrativní účely. Typickým přístupem k této situaci je analyzovat zdrojový soubor do toho, co se nazývá strom analýzy, kde každý uzel stromu obsahuje informace o konkrétním tokenu. Kořenový uzel by měl obsahovat vlastnosti dokumentu.

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

## <a name="see-also"></a>Viz také
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
