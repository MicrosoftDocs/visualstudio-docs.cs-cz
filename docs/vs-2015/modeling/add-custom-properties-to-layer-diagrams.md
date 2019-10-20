---
title: Přidání vlastních vlastností do diagramů vrstev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec1c7c94c8a0e6aa233cf21f9b57e093cc430d48
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655291"
---
# <a name="add-custom-properties-to-layer-diagrams"></a>Přidání vlastních vlastností do diagramů vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při psaní kódu rozšíření pro diagramy vrstev můžete uložit hodnoty s libovolným prvkem v diagramu vrstev. Hodnoty zůstanou při uložení a opětovném otevření diagramu. Tyto vlastnosti lze také zobrazit v okně **vlastnosti** , aby je uživatelé mohli zobrazit a upravit. Můžete například umožnit uživatelům zadat regulární výraz pro každou vrstvu a zapsat ověřovací kód pro ověření, že názvy tříd v jednotlivých vrstvách odpovídají vzoru určenému uživatelem.

## <a name="properties-not-visible-to-the-user"></a>Vlastnosti nejsou viditelné pro uživatele.
 Pokud chcete, aby kód připojil hodnoty k jakémukoli prvku v diagramu vrstvy, nemusíte definovat komponentu MEF. V [ILayerElement](/previous-versions/ff644511(v=vs.140))je slovník s názvem `Properties`. Stačí přidat zařazovací hodnoty do slovníku libovolného elementu vrstvy. Budou uloženy jako součást diagramu vrstev. Další informace najdete v tématu [navigace a aktualizace modelů vrstev v programovém kódu](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="properties-that-the-user-can-edit"></a>Vlastnosti, které může uživatel upravovat
 **Počáteční Příprava**

> [!IMPORTANT]
> Chcete-li zobrazit vlastnosti, je nutné provést následující změnu v každém počítači, kde chcete zobrazit vlastnosti vrstvy.
>
>  1. Spusťte Poznámkový blok pomocí příkazu **Spustit jako správce**. Otevřít `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`
>
>  2. Uvnitř prvku `Content` přidejte:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
>  3. V části **Visual Studio Tools** v nabídce Start aplikace Visual Studio otevřete **Developer Command Prompt**.
>
>     Napište
>
>     `devenv /rootSuffix /updateConfiguration`
>
>     `devenv /rootSuffix Exp /updateConfiguration`
>
>  4. Restartujte sadu Visual Studio.

 **Ujistěte se, že je váš kód v projektu VSIX**

 Pokud je vaše vlastnost součástí projektu příkazu, gesta nebo ověřování, nemusíte nic přidávat. Kód vlastní vlastnosti by měl být definován v projektu rozšiřitelnosti sady Visual Studio definovaném jako Komponenta MEF. Další informace najdete v tématech [Přidání příkazů a gest do diagramů vrstev](../modeling/add-commands-and-gestures-to-layer-diagrams.md) nebo [Přidání ověření vlastní architektury do diagramů vrstev](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 **Definovat vlastní vlastnost**

 Chcete-li vytvořit vlastní vlastnost, Definujte třídu takto:

```
[Export(typeof(IPropertyExtension))]
public class MyProperty
      : PropertyExtension<ILayerElement>
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
 Následující kód je typický popisovač vlastní vlastnosti. Definuje logickou vlastnost v modelu vrstvy (`ILayerModel`), která umožňuje uživateli zadat hodnoty pro vlastní metodu ověřování.

```
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
 [Rozšíření diagramů vrstev](../modeling/extend-layer-diagrams.md)
