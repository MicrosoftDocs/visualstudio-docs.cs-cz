---
title: Přidání vlastních vlastností do diagramů závislostí
description: Přečtěte si, jak můžete ukládat hodnoty pomocí libovolného elementu v diagramu závislostí při psaní kódu rozšíření pro diagramy závislostí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3073a42faf0dcc6fbf586847382ba3a83d88ed4
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360764"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Přidání vlastních vlastností do diagramů závislostí

Při psaní kódu rozšíření pro diagramy závislosti můžete uložit hodnoty s libovolným prvkem v diagramu závislostí. Hodnoty zůstanou při uložení a opětovném otevření diagramu. Tyto vlastnosti lze také zobrazit v okně **vlastnosti** , aby je uživatelé mohli zobrazit a upravit. Můžete například umožnit uživatelům zadat regulární výraz pro každou vrstvu a zapsat ověřovací kód pro ověření, že názvy tříd v jednotlivých vrstvách odpovídají vzoru určenému uživatelem.

## <a name="non-visible-properties"></a>Neviditelné vlastnosti

Pokud chcete, aby kód připojil hodnoty k jakémukoli prvku v diagramu závislostí, nemusíte definovat komponentu MEF. V ILayerElement je slovník s `Properties` názvem [](/previous-versions/ff644511(v=vs.140)). Stačí přidat zařazovací hodnoty do slovníku libovolného elementu vrstvy. Budou uloženy jako součást diagramu závislostí.

## <a name="editable-properties"></a>Upravitelné vlastnosti

**Počáteční Příprava**

> [!IMPORTANT]
> Chcete-li zobrazit vlastnosti, proveďte následující změnu v každém počítači, kde chcete zobrazit vlastnosti vrstvy:
>
> 1. Spusťte Poznámkový blok pomocí příkazu **Spustit jako správce**. Otevřete *%ProgramFiles%\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. Uvnitř elementu **Content** přidejte:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. V části **Visual Studio Tools** v nabídce Start aplikace Visual Studio otevřete **Developer Command Prompt**. Zadejte:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Restartujte Visual Studio.

**Ujistěte se, že je váš kód v projektu VSIX**

Pokud je vaše vlastnost součástí projektu příkazu, gesta nebo ověřování, nemusíte nic přidávat. Kód vlastní vlastnosti by měl být definován v projektu rozšiřitelnosti sady Visual Studio definovaném jako Komponenta MEF. Další informace najdete v tématech [Přidání příkazů a gest do diagramů závislostí](../modeling/add-commands-and-gestures-to-layer-diagrams.md) nebo [Přidání ověření vlastní architektury do diagramů závislostí](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Definovat vlastní vlastnost**

Chcete-li vytvořit vlastní vlastnost, Definujte třídu takto:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Můžete definovat vlastnosti v [ILayerElement](/previous-versions/ff644511(v=vs.140)) nebo kterékoli z jeho odvozených tříd, které zahrnují:

- `ILayerModel` – model

- `ILayer` – jednotlivé vrstvy

- `ILayerDependencyLink` – propojení mezi vrstvami

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Příklad

Následující kód je typický popisovač vlastní vlastnosti. Definuje logickou vlastnost v modelu vrstvy ( `ILayerModel` ), která umožňuje uživateli zadat hodnoty pro vlastní metodu ověřování.

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

## <a name="see-also"></a>Viz také:

- [Rozšíření diagramů závislostí](../modeling/extend-layer-diagrams.md)
