---
title: Managed Extensibility Framework v editoru | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f376a43b6d59ba494db2ad4e5ef26b260d91f6ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632608"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework v editoru
Editor je sestaven pomocí komponent Managed Extensibility Framework (MEF). Můžete sestavit vlastní komponenty rozhraní MEF pro rozšiřování editoru a váš kód může také spotřebovávat komponenty editoru.

## <a name="overview-of-the-managed-extensibility-framework"></a>Přehled Managed Extensibility Framework
 MEF je knihovna .NET, která umožňuje přidat a upravit funkce aplikace nebo komponenty, které následují programovací model MEF. Editor sady Visual Studio může současně poskytovat a spotřebovávat součásti komponenty MEF.

 Rozhraní MEF je obsaženo v sestavení *System. ComponentModel. kompozice. dll* .NET Framework verze 4.

 Další informace o MEF naleznete v tématu [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Části komponent a kontejnery kompozice
 Součást komponenty je třída nebo člen třídy, která může provádět jednu (nebo obě) z následujících možností:

- Využití jiné součásti

- Využíváno jinou komponentou

  Představte si například aplikaci nákupu, která má komponentu pro zadání objednávky, která závisí na datech o dostupnosti produktů poskytovaných komponentou inventáře skladu. V rámci podmínek MEF může součást inventarizace *exportovat* data o dostupnosti produktu a část objednávky může data *importovat* . Část objednávky a část inventarizace nemusejí o sobě navzájem informovat. *kontejner kompozice* (poskytnutý hostitelskou aplikací) zodpovídá za údržbu sady exportů a řešení exportů a importů.

  Kontejner kompozice, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, je obvykle vlastněn hostitelem. Kontejner kompozice udržuje *katalog* exportovaných součástí komponent.

### <a name="export-and-import-component-parts"></a>Exportovat a importovat části součásti
 Můžete exportovat jakékoli funkce, pokud jsou implementovány jako veřejná třída nebo veřejný člen třídy (vlastnost nebo metoda). Nemusíte odvodit součást komponenty z <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Místo toho je nutné přidat atribut <xref:System.ComponentModel.Composition.ExportAttribute> ke třídě nebo členu třídy, který chcete exportovat. Tento atribut určuje *kontrakt* , podle kterého může další součást součásti importovat vaše funkce.

### <a name="the-export-contract"></a>Kontrakt exportu
 @No__t_0 definuje entitu (třídu, rozhraní nebo strukturu), která se exportuje. Obvykle atribut exportu přebírá parametr, který určuje typ exportu.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Ve výchozím nastavení atribut <xref:System.ComponentModel.Composition.ExportAttribute> definuje kontrakt, který je typem exportované třídy.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 V příkladu je výchozí atribut `[Export]` ekvivalentem `[Export(typeof(TestAdornmentLayerDefinition))]`.

 Můžete také exportovat vlastnost nebo metodu, jak je znázorněno v následujícím příkladu.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Import exportu MEF
 Pokud chcete použít export MEF, musíte znát kontrakt (obvykle typ), pomocí kterého byl exportován, a přidat atribut <xref:System.ComponentModel.Composition.ImportAttribute>, který má tuto hodnotu. Ve výchozím nastavení atribut import přijímá jeden parametr, což je typ třídy, kterou upravuje. Následující řádky kódu importují typ <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Získat funkce editoru z části součásti MEF
 Pokud je váš stávající kód součástí komponenty MEF, můžete použít metadata rozhraní MEF pro použití částí komponenty editoru.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Pro využívání funkcí editoru z součásti MEF

1. Přidejte odkazy na *System. kompozice. ComponentModel. dll*, který je v globální mezipaměti sestavení (GAC), a do sestavení editoru.

2. Přidejte relevantní direktivy using.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Následujícím způsobem přidejte atribut `[Import]` do rozhraní služby.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Po získání služby můžete využít některou z jejích komponent.

5. Po zkompilování sestavení jej vložte do složky *.. \Common7\IDE\Components \* složku instalace sady Visual Studio.

## <a name="see-also"></a>Viz také:
- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
