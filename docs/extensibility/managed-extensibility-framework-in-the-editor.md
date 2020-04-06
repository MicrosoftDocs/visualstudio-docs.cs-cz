---
title: Rozhraní Spravované rozšiřitelnosti v editoru | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702868"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Rozhraní Spravované rozšiřitelnosti v editoru
Editor je sestaven pomocí součástí Managed Extensibility Framework (MEF). Můžete vytvořit vlastní mef komponenty rozšířit editor a váš kód může využívat editor komponenty také.

## <a name="overview-of-the-managed-extensibility-framework"></a>Přehled rámce spravované rozšiřitelnosti
 MEF je knihovna .NET, která umožňuje přidávat a upravovat funkce aplikace nebo součásti, která následuje za programovacím modelem MEF. Editor Visual Studio může poskytovat i využívat součásti MEF.

 MEF je obsažen v sestavení rozhraní .NET Framework verze 4 *System.ComponentModel.Composition.dll.*

 Další informace o MEF naleznete [v tématu Spravované rozšíření framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Součásti a kompozice kontejnery
 Součást součásti je třída nebo člen třídy, který může provést jednu (nebo obě) následující:

- Spotřebovávat jinou součást

- Spotřebovávat jinou komponentou

  Zvažte například nákupní aplikaci, která má komponentu položky objednávky, která závisí na datech dostupnosti produktu poskytnutých komponentou skladových zásob. Z hlediska MEF může skladová část *exportovat* data dostupnosti produktu a část položky objednávky může *data importovat.* Část položky objednávky a skladová část o sobě nemusí vědět; *kontejner složení* (poskytnutý hostitelskou aplikací) je zodpovědný za udržování souboru vývozů a řešení vývozů a importů.

  Kontejner složení <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, je obvykle vlastněn hostitelem. Kontejner složení udržuje *katalog* exportovaných součástí.

### <a name="export-and-import-component-parts"></a>Export a import součástí
 Můžete exportovat všechny funkce, tak dlouho, dokud je implementována jako veřejná třída nebo veřejný člen třídy (vlastnost nebo metoda). Součást není třeba odvozovat <xref:System.ComponentModel.Composition.Primitives.ComposablePart>z aplikace . Místo toho je <xref:System.ComponentModel.Composition.ExportAttribute> nutné přidat atribut do třídy nebo člena třídy, který chcete exportovat. Tento atribut určuje *smlouvu,* podle které může jiná součást importovat vaše funkce.

### <a name="the-export-contract"></a>Vývozní smlouva
 Definuje <xref:System.ComponentModel.Composition.ExportAttribute> entitu (třídu, rozhraní nebo strukturu), která je exportována. Atribut exportu obvykle přebírá parametr, který určuje typ exportu.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Ve výchozím <xref:System.ComponentModel.Composition.ExportAttribute> nastavení atribut definuje smlouvu, která je typem exportující třídy.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 V příkladu je `[Export]` výchozí atribut `[Export(typeof(TestAdornmentLayerDefinition))]`ekvivalentní .

 Můžete také exportovat vlastnost nebo metodu, jak je znázorněno v následujícím příkladu.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Import exportu MEF
 Pokud chcete spotřebovat export MEF, musíte znát smlouvu (obvykle typ), podle kterého byla <xref:System.ComponentModel.Composition.ImportAttribute> exportována, a přidat atribut, který má tuto hodnotu. Ve výchozím nastavení má atribut import u jednoho parametru, což je typ třídy, kterou upravuje. Následující řádky kódu importují <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> typ.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Získání funkce editoru z součásti MEF
 Pokud je váš existující kód součástí MEF, můžete použít metadata MEF ke spotřebování součástí editoru.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Využití funkcí editoru z součásti MEF

1. Přidejte odkazy na *soubor System.Composition.ComponentModel.dll*, který je v globální mezipaměti sestavení (GAC), a na sestavení editoru.

2. Přidejte příslušné direktivy pomocí.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Přidejte `[Import]` atribut do rozhraní služby následujícím způsobem.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Po získání služby můžete spotřebovat některou z jejích součástí.

5. Po kompilaci sestavení jej vložte do *.. \Common7\IDE\Components\* v instalaci sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)
