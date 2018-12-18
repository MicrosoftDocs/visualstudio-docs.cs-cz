---
title: Managed Extensibility Framework v Editor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5ea47032ed2c5e4fb9b99afb214e068ca39d692
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857520"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework v editor
Editor je sestavena pomocí Managed Extensibility Framework (MEF) komponenty. Můžete vytvářet vlastní komponent MEF, rozšíření editoru, a váš kód může spotřebovat i součásti editoru.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Přehled služby Managed Extensibility Framework  
 Rozhraní MEF je knihovnu .NET, která vám umožní přidat a upravit funkce aplikace nebo komponenty, který následuje programovací model MEF. Editor sady Visual Studio můžete zadat i využívat součásti MEF.  
  
 Rozhraní MEF je obsažen v rozhraní .NET Framework verze 4 *System.ComponentModel.Composition.dll* sestavení.  
  
 Další informace o rozhraní MEF, naleznete v tématu [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>Součásti a složení kontejnery  
 Součást je třída nebo člen třídy, která můžete provést jednu (nebo obojí) z následujících akcí:  
  
- Využívat jiné komponenty  
  
- Využívat jiné komponenty  
  
  Představte si třeba nákupní aplikaci, která má komponentu pořadí položka, která závisí na produktu dostupnost dat inventáře komponenta skladu. V podmínkách MEF, součást inventáře můžete *exportovat* produktu dostupnost dat a může část položky pořadí *importovat* data. Část položky pořadí a části inventáře nemusíte vědět o sobě navzájem; *kontejner kompozic rozhraní MEF* (získaný od hostitele aplikace) je zodpovědná za údržbu sadu exporty a řešení exportuje a importuje.  
  
  Kontejner kompozic <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, obvykle vlastní hostitel. Kontejner kompozic udržuje *katalogu* exportované součásti.  
  
### <a name="export-and-import-component-parts"></a>Export a import součástí  
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
  
### <a name="import-a-mef-export"></a>Import a Export rozhraní MEF  
 Pokud chcete využívat MEF export, musíte znát kontraktu (obvykle typu), pomocí kterého jste exportovali a přidejte <xref:System.ComponentModel.Composition.ImportAttribute> atribut, který má tuto hodnotu. Ve výchozím nastavení atribut import přijímá jeden parametr, což je typ třídy, která upravuje. Následující řádky kódu importu <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> typu.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="get-editor-functionality-from-a-mef-component-part"></a>Funkce editoru získat z součást MEF  
 Pokud váš stávající kód je součást MEF, můžete využívat součásti editoru metadat rozhraní MEF.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Využívání funkce editoru v součásti MEF  
  
1.  Přidání odkazů na *System.Composition.ComponentModel.dll*, což je v globální mezipaměti sestavení (GAC) a editor sestavení.  
  
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
  
5.  Když kompilujete sestavení, vložit ho do *.. \Common7\IDE\Components\* složce instalace sady Visual Studio.  
  
## <a name="see-also"></a>Viz také:  
 [Jazykové služby a editor Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md)