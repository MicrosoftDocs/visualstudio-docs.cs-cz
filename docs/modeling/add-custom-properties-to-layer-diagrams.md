---
title: Přidání vlastních vlastností do diagramů závislostí
description: Zjistěte, jak můžete při psaní kódu rozšíření pro diagramy závislostí ukládat hodnoty s libovolným prvkem v diagramu závislostí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70588a2d472a1170b58911eece4fa70831064f72
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389849"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Přidání vlastních vlastností do diagramů závislostí

Při psaní kódu rozšíření pro diagramy závislostí můžete ukládat hodnoty s libovolným prvkem v diagramu závislostí. Hodnoty se zachytá při uložení a opětovném otevření diagramu. Tyto vlastnosti se také dají zobrazit v **okně Vlastnosti,** aby je uživatelé mohli zobrazit a upravit. Můžete například nechat uživatele zadat regulární výraz pro každou vrstvu a napsat ověřovací kód pro ověření, že názvy tříd v každé vrstvě odpovídají vzoru určenému uživatelem.

## <a name="non-visible-properties"></a>Nezviditelněné vlastnosti

Pokud chcete, aby váš kód pouze připojoval hodnoty k libovolném prvku v diagramu závislostí, nemusíte definovat komponentu MEF. V elementu `Properties` [ILayerElement](/previous-versions/ff644511(v=vs.140))je slovník s názvem . Jednoduše přidejte zařazovatelné hodnoty do slovníku libovolného prvku vrstvy. Uloží se jako součást diagramu závislostí.

## <a name="editable-properties"></a>Upravitelné vlastnosti

**Počáteční příprava**

> [!IMPORTANT]
> Pokud chcete, aby se vlastnosti objevily, proveďte následující změnu v každém počítači, kde chcete, aby byly vlastnosti vrstvy viditelné:
>
> 1. Spusťte Poznámkový blok pomocí příkazu **Spustit jako správce.** Otevřete *soubor %ProgramFiles%\Microsoft Visual Studio [verze]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest.*
> 2. Uvnitř **elementu Content** přidejte:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. V **Visual Studio Tools** startu Visual Studio aplikace otevřete soubor **Developer Command Prompt**. Zadejte:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Restartujte Visual Studio.

**Ujistěte se, že je váš kód v projektu VSIX.**

Pokud je vaše vlastnost součástí příkazu, gesta nebo projektu ověřování, nemusíte nic přidávat. Kód vlastní vlastnosti by měl být definován v projektu Visual Studio extensibility definovaném jako komponenta MEF. Další informace najdete v tématu Přidání příkazů a gest do [diagramů závislostí](../modeling/add-commands-and-gestures-to-layer-diagrams.md) nebo Přidání vlastního ověření [architektury do diagramů závislostí.](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

**Definování vlastní vlastnosti**

Pokud chcete vytvořit vlastní vlastnost, definujte třídu tímto kódem:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Vlastnosti můžete definovat u [elementu ILayerElement](/previous-versions/ff644511(v=vs.140)) nebo kterékoli z jejích odvozených tříd, mezi které patří:

- `ILayerModel` – model

- `ILayer` – každá vrstva

- `ILayerDependencyLink` – propojení mezi vrstvami

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Příklad

Následující kód je typický popisovač vlastní vlastnosti. Definuje logickou vlastnost modelu vrstvy ( ), která uživateli umožňuje `ILayerModel` zadat hodnoty pro vlastní metodu ověřování.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Viz také

- [Rozšíření diagramů závislostí](../modeling/extend-layer-diagrams.md)
