---
title: Managed Extensibility Framework v Editor | Dokumentace Microsoftu
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
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41d5768c8cfddc3474616d7a2eee16b84cd24d56
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754703"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Rozhraní Managed Extensibility Framework v editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor je sestavena pomocí Managed Extensibility Framework (MEF) komponenty. Můžete vytvářet vlastní komponent MEF, rozšíření editoru, a váš kód může spotřebovat i součásti editoru.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Přehled služby Managed Extensibility Framework  
 Rozhraní MEF je knihovnu .NET, která vám umožní přidat a upravit funkce aplikace nebo komponenty, který následuje programovací model MEF. Editor sady Visual Studio můžete zadat i využívat součásti MEF.  
  
 Rozhraní MEF je obsažen v sestavení rozhraní .NET Framework verze 4 System.ComponentModel.Composition.dll.  
  
 Další informace o rozhraní MEF, naleznete v tématu [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Součásti a složení kontejnery  
 Součást je třída nebo člen třídy, která můžete provést jednu (nebo obojí) z následujících akcí:  
  
- Využívat jiné komponenty  
  
- Využívat jiné komponenty  
  
  Představte si třeba nákupní aplikaci, která má komponentu pořadí položka, která závisí na produktu dostupnost dat inventáře komponenta skladu. V podmínkách MEF, součást inventáře můžete *exportovat* produktu dostupnost dat a může část položky pořadí *importovat* data. Část položky pořadí a části inventáře nemusíte vědět o sobě navzájem; *kontejner kompozic rozhraní MEF* (získaný od hostitele aplikace) je zodpovědná za údržbu sadu exporty a řešení exportuje a importuje.  
  
  Kontejner kompozic <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, obvykle vlastní hostitel. Kontejner kompozic udržuje *katalogu* exportované součásti.  
  
### <a name="exporting-and-importing-component-parts"></a>Export a import součástí  
 Všechny funkce, můžete exportovat, tak dlouho, dokud je implementovaný jako veřejnou třídu nebo veřejného člena třídy (vlastnosti nebo metody). Není nutné odvozovat vaše součást z <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Místo toho je nutné přidat <xref:System.ComponentModel.Composition.ExportAttribute> atribut pro třídu nebo člen třídy, která chcete exportovat. Tento atribut určuje *kontraktu* které jiné součásti můžete importovat část vaší funkce.  
  
### <a name="the-export-contract"></a>Export kontraktu  
 <xref:System.ComponentModel.Composition.ExportAttribute> Definuje entitu (třída, rozhraní nebo struktura), který je exportován. Atribut export obvykle přebírá parametr, který určuje typ exportu.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Ve výchozím nastavení <xref:System.ComponentModel.Composition.ExportAttribute> atribut definuje kontrakt, který je typem třídy exportu.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 V příkladu, výchozí `[Export]` atributu je rovna `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Můžete také exportovat vlastnosti nebo metody, jak je znázorněno v následujícím příkladu.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Import Export MEF  
 Pokud chcete využívat MEF export, musíte znát kontraktu (obvykle typu), pomocí kterého jste exportovali a přidejte <xref:System.ComponentModel.Composition.ImportAttribute> atribut, který má tuto hodnotu. Ve výchozím nastavení atribut import přijímá jeden parametr, což je typ třídy, která upravuje. Následující řádky kódu importu <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> typu.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Získávání funkce editoru v součásti MEF  
 Pokud váš stávající kód je součást MEF, můžete využívat součásti editoru metadat rozhraní MEF.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Využívání funkce editoru v součásti MEF  
  
1.  Přidání odkazů System.Composition.ComponentModel.dll, což je v globální mezipaměti sestavení (GAC), a editor sestavení.  
  
2.  Přidejte příslušné příkazy using.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Přidat `[Import]` atribut do vašeho rozhraní služby následujícím způsobem.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Když zakoupíte službu, můžete využívat některou z jeho součástí.  
  
5.  Když kompilujete sestavení, vložit ho do... Složka \Common7\IDE\Components\ instalace sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřovací body služeb jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)

