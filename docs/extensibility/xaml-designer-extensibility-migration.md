---
title: Migrace rozšíření Návrhář XAML
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 9f5085c7a655f186c3c8a4a6eecada8b440650cd
ms.sourcegitcommit: 528178a304e66c0cb7ab98b493fe3c409f87493a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273222"
---
# <a name="xaml-designer-extensibility-migration"></a>Migrace rozšíření návrháře XAML

Návrhář XAML v aplikaci Visual Studio 2019 podporuje dvě různé architektury: architektura izolace návrháře a novější architekturu izolace povrchu. Tento přechod architektury je vyžadován k podpoře cílových běhových prostředí, která nelze hostovat v procesu .NET Framework. Přechod na architekturu izolace Surface přináší zásadní změny modelu rozšiřitelnosti třetí strany. Tento článek popisuje tyto změny, které jsou k dispozici v aplikaci Visual Studio 2019 počínaje verzí 16,3.

Návrhář WPF používá **izolaci návrháře** pro projekty, které cílí na .NET Framework a podporuje rozšíření *. Design. dll* . Uživatelský kód, knihovny ovládacích prvků a rozšíření třetích stran se načítají v externím procesu (*XDesProc. exe*) společně s vlastními panely Code Designer a návrháře.

**Izolaci povrchu** používá Návrhář UWP. Je také používán návrhářem WPF pro projekty, které cílí na .NET Core. Při izolaci povrchu jsou načteny pouze uživatelské kódy a knihovny ovládacích prvků v samostatném procesu, zatímco Návrhář a jeho panely jsou načteny do procesu sady Visual Studio (*devenv. exe*). Modul runtime, který se používá pro spouštění knihoven uživatelských kódů a ovládacích prvků, se liší od použití .NET Framework pro skutečný Návrhář a kód rozšiřitelnosti třetí strany.

![Rozšiřitelnost – architektura migrace](media/xaml-designer-extensibility-migration-architecture.png)

Z důvodu tohoto přechodu architektury již nejsou rozšíření jiných výrobců načítána do stejného procesu jako knihovny ovládacích prvků třetích stran. Rozšíření již nemohou mít přímé závislosti na knihovnách ovládacích prvků nebo přímo přistupují k objektům modulu runtime. Rozšíření, která byla dříve vytvořena pro architekturu izolace návrháře pomocí rozhraní API *Microsoft. Windows. rozšiřitelnost. dll* , je nutné migrovat na nový přístup pro práci s architekturou izolace povrchu. V praxi bude nutné kompilovat existující rozšíření proti novým rozšiřujícím sestavením rozhraní API. Přístup k běhovým typům běhu prostřednictvím [typeof](/dotnet/csharp/language-reference/keywords/typeof) nebo instancí run-time musí být nahrazen nebo odebrán, protože knihovny ovládacích prvků jsou nyní načteny v jiném procesu.

## <a name="new-extensibility-api-assemblies"></a>Nová rozšiřitelná sestavení rozhraní API

Nová rozšiřující sestavení rozhraní API jsou podobná existujícím sestavením rozhraní API pro rozšiřitelnost, ale následují jiné schéma pojmenování, aby je bylo možné odlišit. Podobně se názvy oborů názvů změnily tak, aby odrážely nové názvy sestavení.

| Sestavení rozhraní API izolace návrháře            | Sestavení rozhraní API pro izolaci povrchu                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Nová přípona souboru a zjišťování

Namísto použití přípony souboru *. Design. dll* budou nové rozšíření Surface zjištěny pomocí přípony souboru *. DesignTools. dll* . Přípona *. Design. dll* a *. DesignTools. dll* mohou existovat ve stejné podsložce *návrhu* .

I když jsou knihovny ovládacích prvků třetích stran kompilovány pro skutečný cílový modul runtime (.NET Core nebo UWP), přípona *. DesignTools. dll* by měla být vždy kompilována jako sestavení .NET Framework.

## <a name="decouple-attribute-tables-from-run-time-types"></a>Oddělit tabulky atributů z běhových typů

Model rozšiřitelnosti izolace povrchu nepovoluje, aby rozšíření byla závislá na vlastních knihovnách ovládacích prvků, a proto rozšíření nemůžou odkazovat na typy z knihovny ovládacích prvků. Například *MyLibrary. DesignTools. dll* by neměl mít závislost na *MyLibrary. dll*.

Tyto závislosti byly nejběžnější při registraci metadat pro typy prostřednictvím tabulek atributů. Kód rozšíření, který odkazuje na typy knihovny ovládacích prvků přímo pomocí [typeof](/dotnet/csharp/language-reference/keywords/typeof) nebo [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) , je nahrazen v nových rozhraních API pomocí názvů typů založených na řetězci:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      var builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>Poskytovatelé funkcí a rozhraní API modelu

Poskytovatelé funkcí jsou implementováni v sestaveních rozšíření a načteny do procesu sady Visual Studio. `FeatureAttribute`bude nadále odkazovat na typy poskytovatele funkcí přímo pomocí [typeof](/dotnet/csharp/language-reference/keywords/typeof).

V současné době jsou podporovány následující poskytovatelé funkcí:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`
* `DesignModeValueProvider`je podporován s omezením, `TranslatePropertyValue` které bude voláno `InvalidateProperty` prostřednictvím nebo při změně v návrháři. Nevolá se, když se upraví v běhovém kódu.

Vzhledem k tomu, že poskytovatelé funkcí jsou nyní načítány v jiném procesu než vlastní knihovny kódu run-time a Control, již nejsou schopny přistupovat přímo k objektům modulu runtime. Místo toho je nutné všechny takové interakce převést tak, aby používaly odpovídající rozhraní API založených na modelu. Rozhraní API modelu bylo aktualizováno a přístup <xref:System.Type> k nebo <xref:System.Object> již není k dispozici nebo byl nahrazen pomocí `TypeIdentifier` a `TypeDefinition`.

`TypeIdentifier`představuje řetězec bez názvu sestavení identifikující typ. Lze ji přeložit `TypeDefinition` na, chcete-li zadat dotaz na Další informace o typu. `TypeIdenfifier` `TypeDefinition`instance se nedají ukládat do mezipaměti v kódu rozšíření.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

Rozhraní API, která se odebrala ze sady rozhraní API pro rozšíření izolace povrchu:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`
* `AssemblyReferences.GetTypes(Type baseType)`

Rozhraní API, `TypeIdentifier` která se <xref:System.Type>používají místo:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ModelFactory.ResolveType(EditingContext context, Type)`změněno na`MetadataFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ModelService.ResolveType(TypeIdentifier typeIdentifier)`změněno na`MetadataService.ResolveType(TypeIdentifier typeIdentifier)`
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

Rozhraní API, `TypeIdentifier` která používají <xref:System.Type> místo a již nadále nepodporují argumenty konstruktoru:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

Rozhraní API, `TypeDefinition` která se <xref:System.Type>používají místo:

* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`
* `PropertyEntry.PropertyType`

Rozhraní API, `AssemblyIdentifier` která se `<xref:System.Reflection.AssemblyName?displayProperty=fullName>`používají místo:

* `AssemblyReferences.ReferencedAssemblies`
* `AssemblyReferences.LocalAssemblyName`změněno na`AssemblyReferences.LocalAssemblyIdentifier`

Rozhraní API podobně jako `SetValue` budou podporovat pouze instance primitivních typů nebo předdefinované .NET Framework typy, které lze převést pro cílový modul runtime. `ModelItem` V současné době jsou tyto typy podporovány:

* Primitivní .NET Framework typy: `Boolean`, `Byte`, `Char`, `DateTime`, `Double`, ,`Enum` ,`Int16`, ,`Int64`,, `Int32` `Guid` `Nullable` `SByte` , `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* Známé typy .NET Framework WPF (a odvozené typy): `Brush`, `Color`, `CompositeTransform`, `CornerRadius`, `Duration`, `EasingFunctionBase`, `EasingMode`, `EllipseGeometry`, `FontFamily`, `GeneralTransform` ,`Geometry` , `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

Příklad:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

Další ukázky kódu jsou k dispozici v úložišti [XAML-Designer-Samples-Samples](https://github.com/microsoft/xaml-designer-extensibility-samples) .

## <a name="limited-support-for-designdll-extensions"></a>Omezená podpora pro rozšíření. Design. dll

Pokud je pro knihovnu ovládacích prvků zjištěno jakékoli rozšíření *. DesignTools. dll* , je nejprve načteno a zjišťování pro příponu *. Design. dll* je vynecháno.

Pokud nejsou k dispozici žádná přípona *. DesignTools. dll* , ale je nalezena přípona. *design. dll* , služba jazyka XAML se pokusí načíst toto sestavení a extrahovat informace tabulky atributu pro podporu scénářů základního editoru a inspektoru vlastností. Tento mechanismus je omezený v oboru. Neumožňuje načítání rozšíření izolace návrháře pro provádění poskytovatelů funkcí, ale může poskytovat základní podporu pro stávající knihovny ovládacích prvků WPF.
