---
title: Managed Extensibility Framework v editoru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f19b71c86d972b59a9d46f379bf7ec93f63aeb9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679961"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Rozhraní Managed Extensibility Framework v editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor je sestaven pomocí komponent Managed Extensibility Framework (MEF). Můžete sestavit vlastní komponenty rozhraní MEF pro rozšiřování editoru a váš kód může také spotřebovávat komponenty editoru.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Přehled Managed Extensibility Framework  
 MEF je knihovna .NET, která umožňuje přidat a upravit funkce aplikace nebo komponenty, které následují programovací model MEF. Editor sady Visual Studio může současně poskytovat a spotřebovávat součásti komponenty MEF.  
  
 Rozhraní MEF je obsaženo v sestavení System.ComponentModel.Composition.dll .NET Framework verze 4.  
  
 Další informace o MEF naleznete v tématu [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Části komponent a kontejnery kompozice  
 Součást komponenty je třída nebo člen třídy, která může provádět jednu (nebo obě) z následujících možností:  
  
- Využití jiné součásti  
  
- Využíváno jinou komponentou  
  
  Představte si například aplikaci nákupu, která má komponentu pro zadání objednávky, která závisí na datech o dostupnosti produktů poskytovaných komponentou inventáře skladu. V rámci podmínek MEF může součást inventarizace *exportovat* data o dostupnosti produktu a část objednávky může data *importovat* . Část objednávky a část inventarizace nemusejí o sobě navzájem informovat. *kontejner kompozice* (poskytnutý hostitelskou aplikací) zodpovídá za údržbu sady exportů a řešení exportů a importů.  
  
  Kontejner kompozice, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> , je obvykle vlastněn hostitelem. Kontejner kompozice udržuje *katalog* exportovaných součástí komponent.  
  
### <a name="exporting-and-importing-component-parts"></a>Export a import částí komponent  
 Můžete exportovat jakékoli funkce, pokud jsou implementovány jako veřejná třída nebo veřejný člen třídy (vlastnost nebo metoda). Nemusíte odvodit část komponenty z <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . Místo toho je nutné přidat <xref:System.ComponentModel.Composition.ExportAttribute> atribut ke třídě nebo členu třídy, který chcete exportovat. Tento atribut určuje *kontrakt* , podle kterého může další součást součásti importovat vaše funkce.  
  
### <a name="the-export-contract"></a>Kontrakt exportu  
 <xref:System.ComponentModel.Composition.ExportAttribute>Definuje entitu (třídu, rozhraní nebo strukturu), která se exportuje. Obvykle atribut exportu přebírá parametr, který určuje typ exportu.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Ve výchozím nastavení <xref:System.ComponentModel.Composition.ExportAttribute> atribut definuje kontrakt, který je typem exportované třídy.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 V příkladu `[Export]` je výchozí atribut ekvivalentní `[Export(typeof(TestAdornmentLayerDefinition))]` .  
  
 Můžete také exportovat vlastnost nebo metodu, jak je znázorněno v následujícím příkladu.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Import exportu MEF  
 Pokud chcete použít export MEF, musíte znát kontrakt (obvykle typ), pomocí kterého byl exportován, a přidat <xref:System.ComponentModel.Composition.ImportAttribute> atribut, který má tuto hodnotu. Ve výchozím nastavení atribut import přijímá jeden parametr, což je typ třídy, kterou upravuje. Následující řádky kódu importují <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> typ.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Získávání funkcí editoru z části součásti MEF  
 Pokud je váš stávající kód součástí komponenty MEF, můžete použít metadata rozhraní MEF pro použití částí komponenty editoru.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Pro využívání funkcí editoru z součásti MEF  
  
1. Přidejte odkazy na System.Composition.ComponentModel.dll, které jsou v globální mezipaměti sestavení (GAC), a do sestavení editoru.  
  
2. Přidejte relevantní příkazy using.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3. Přidejte `[Import]` atribut do rozhraní služby následujícím způsobem.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4. Po získání služby můžete využít některou z jejích komponent.  
  
5. Po zkompilování sestavení jej vložte do.. \Common7\IDE\Components\ složka instalace sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřovací body služeb jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
