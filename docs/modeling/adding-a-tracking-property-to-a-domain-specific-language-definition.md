---
title: Přidání vlastnosti sledování do definice jazyka specifického pro doménu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0417507323a627753bc62e50b424c37b547d4dad
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967477"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Přidání vlastnosti sledování do definice jazyka specifického pro doménu

Tento návod ukazuje, jak přidat vlastnosti sledování do modelu domény.

A *sledování domény* je vlastnost, která je možné aktualizovat podle uživatele, ale který má výchozí hodnotu, která se počítá na základě hodnot jiných vlastnosti domény nebo elementy.

Například v nástroje jazyka specifického pro doménu (DSL Tools), zobrazovaný název vlastnosti třídy domény má výchozí hodnotu, která se počítá pomocí názvu doménové třídy, ale uživatel změňte hodnotu v době návrhu nebo ho resetovat do počítanou hodnotu.

V tomto podrobném návodu vytvoření jazyka specifického pro doménu (DSL), který má Namespace sledování vlastnost, která má výchozí hodnotu na základě Namespace výchozí vlastnosti modelu. Další informace o sledování vlastnosti najdete v tématu [definování sledování vlastnosti](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- Podpora nástroje DSL sledování popisovače vlastnosti. Návrhář DSL však nelze použít pro přidání vlastnosti sledování do jazyka. Proto je nutné přidat vlastní kód musel definovat a implementovat vlastnosti sledování.

  Vlastnosti sledování do má dva stavy: sledování a aktualizované uživatelem. Sledování vlastnosti mají tyto funkce:

- Při sledování stavu, vypočítá hodnotu vlastnosti sledování a hodnota je aktualizována tak další vlastnosti v Změna modelu.

- Když v aktualizovaném podle stavu uživatele, hodnota vlastnosti sledování uchovává hodnotu, která uživatel naposledy nastavit vlastnost.

- V **vlastnosti** okně **resetování** příkaz pro vlastnosti sledování je povolená jenom při vlastnost se v aktualizovaném podle stavu uživatele. **Resetování** příkaz nastaví vlastnosti sledování do sledování stavu.

- V **vlastnosti** okno, když je vlastnost sledování ve sledování stavu, jeho hodnota se zobrazí v pravidelných písma.

- V **vlastnosti** okno, když je vlastnost sledování v aktualizovaném ve stavu uživatele, jeho hodnota se zobrazí tučným písmem.

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu, je třeba nejprve nainstalovat tyto komponenty:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581) |

## <a name="create-the-project"></a>Vytvoření projektu

1.  Vytvoření projektu návrháře jazyka specifického pro doménu. Pojmenujte ji `TrackingPropertyDSL`.

2.  V **Průvodce návrháře jazyka specifického pro doménu**, nastavte následující možnosti:

    1.  Vyberte **MinimalLanguage** šablony.

    2.  Použít výchozí název jazyka specifického pro doménu `TrackingPropertyDSL`.

    3.  Nastavit rozšíření pro soubory modelu `trackingPropertyDsl`.

    4.  Ikona výchozí šablony lze použijte pro soubory modelu.

    5.  Nastavte název produktu, který má `Product Name`.

    6.  Nastavte název společnosti `Company Name`.

    7.  Použijte výchozí hodnotu pro kořenový obor názvů pro projekty v řešení, `CompanyName.ProductName.TrackingPropertyDSL`.

    8.  Povolte průvodce vytvořit soubor klíče se silným názvem pro vaše sestavení.

    9. Podrobnosti o řešení a potom klikněte na tlačítko **Dokončit** k vytvoření projektu definice DSL.

## <a name="customize-the-default-dsl-definition"></a>Přizpůsobení výchozí definice DSL
 V této části můžete přizpůsobit definici DSL tak, aby obsahovala následující položky:

-   Namespace, sledování vlastnost pro každý prvek modelu.

-   Logická IsNamespaceTracking vlastnost pro každý prvek modelu. Tato vlastnost indikuje, zda je vlastnost sledování stavu sledování nebo v aktualizovaném podle stavu uživatele.

-   Namespace výchozí vlastnost pro model. Tato vlastnost se použije k výpočtu Namespace vlastnost sledování na výchozí hodnotu.

-   CustomElements počítá vlastností modelu. Tato vlastnost bude tato informace uvedena podíl prvky, které mají vlastní obor názvů.

### <a name="to-add-the-domain-properties"></a>Chcete-li přidat vlastnosti domény

1.  V návrháře DSL, klikněte pravým tlačítkem na **ExampleModel** doménové třídy, přejděte na příkaz **přidat**a potom klikněte na tlačítko **vlastnost DomainProperty**.

    1.  Pojmenujte novou vlastnost `DefaultNamespace`.

    2.  V **vlastnosti** okna pro novou vlastnost, nastavte **výchozí hodnota** k `DefaultNamespace`a nastavte **typ** k **řetězec**.

2.  Chcete **ExampleModel** domény, do třídy doménovou vlastnost s názvem `CustomElements`.

     V **vlastnosti** okna pro novou vlastnost, nastavte **druh** k **vypočtené**.

3.  Chcete **ExampleElement** domény, do třídy doménovou vlastnost s názvem `Namespace`.

     V **vlastnosti** okna pro novou vlastnost, nastavte **je Prohlížitelná** k **False**a nastavte **druh** k **hodnotu CustomStorage** .

4.  Chcete **ExampleElement** domény, do třídy doménovou vlastnost s názvem `IsNamespaceTracking`.

     V **vlastnosti** okna pro novou vlastnost, nastavte **je Prohlížitelná** k **False**, nastavte **výchozí hodnota** k `true`a nastavení **Typ** k **logická**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Chcete-li aktualizovat elementy diagramu a podrobnosti DSL

1.  V návrháře DSL, klikněte pravým tlačítkem **ExampleShape** obrazec geometrie, přejděte na **přidat**a potom klikněte na tlačítko **Dekoratér Text**.

    1.  Pojmenujte nový text dekoratér `NamespaceDecorator`.

    2.  V **vlastnosti** okno pro dekoratér text nastaveno **pozice** k **InnerBottomLeft**.

2.  V návrháře DSL, vyberte řádek, který se připojí **ExampleElement** třídu **ExampleShape** obrazce.

    1.  V **podrobnosti DSL** okna, vyberte **mapování Dekoratéru** kartu.

    2.  V **Dekoratéry** seznamu vyberte **NamespaceDecorator**, zaškrtněte její políčko a potom na **zobrazit vlastnost** seznamu vyberte **Namespace**.

3.  V **Průzkumník DSL**, rozbalte **doménovými třídami** složky, klikněte pravým tlačítkem na **ExampleElement** uzlu a pak klikněte na tlačítko **přidat nový popisovač typu domény**.

    1.  Rozbalte **ExampleElement** uzel a vyberte **popisovači vlastního typu (popisovač typu domény)** uzlu.

    2.  V **vlastnosti** nastavit okno pro popisovač typu domény **programového vlastní** k **True**.

4.  V **Průzkumník DSL**, vyberte **chování serializace Xml** uzlu.

    1.  V **vlastnosti** okno, nastavte **načítání příspěvků vlastní** k **True**.

## <a name="transform-templates"></a>Transformace šablon

Teď, když jste definovali doménové třídy a vlastnosti pro vašeho DSL, můžete ověřit, že se znova vygenerovat kód pro váš projekt je správně transformovat definici DSL.

1.  Na **Průzkumníka řešení** nástrojů, klikněte na tlačítko **Transformovat všechny šablony**.

2.  Systém vygeneruje kód pro řešení a uloží DslDefinition.dsl. Informace o formátu XML souborů definic najdete v tématu [soubor DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Vytvoření souborů pro vlastní kód

Při transformaci všech šablon systém generuje zdrojový kód, který definuje jazyka specifického pro doménu v projektech Dsl a DslPackage. Tak, aby narušovaly vygenerovanému textu se můžete vyhnout, napište vlastní kód v souborech, které se liší od souboru generovaného kódu.

Pro zachování hodnotu a stav sledovaná vlastnost je nutné zadat kód. Vám usnadní orientaci ve vlastním kódu generovaného kódu a aby se zabránilo konfliktům pojmenování souboru, umístěte svoje soubory na vlastní kód v samostatné podsložce.

1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **DSL** projektu, přejděte na **přidat**a potom klikněte na **novou složku**. Název nové složky `CustomCode`.

2.  Klikněte pravým tlačítkem na nový **CustomCode** složku, přejděte na příkaz **přidat**a potom klikněte na tlačítko **nová položka**.

3.  Vyberte **souboru s kódem** šablony, nastavte **název** k `NamespaceTrackingProperty.cs`a potom klikněte na tlačítko **OK**.

     Soubor NamespaceTrackingProperty.cs je vytvořen a otevřen pro úpravy.

4.  Ve složce, vytvořte následující soubory kódu: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, a `TypeDescriptor.cs`.

5.  V **DslPackage** projektu, taky vytvořit `CustomCode` složky a přidejte do ní `Package.cs` soubor kódu.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Přidání tříd pomocných rutin pro podporu sledování vlastnosti

Chcete-li soubor HelperClasses.cs přidejte `TrackingHelper` a `CriticalException` třídy následujícím způsobem. Tyto třídy dále v tomto návodu budete odkazovat.

1.  Přidejte následující kód do souboru HelperClasses.cs.

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Přidání vlastního kódu pro vlastní typ popisovače

Implementace `GetCustomProperties` popisovače typu pro metodu `ExampleModel` doménovou třídu.

> [!NOTE]
> Kód, který nástroje DSL vygenerovat pro vlastního popisovače typu pro `ExampleModel` volání `GetCustomProperties`, nicméně nástroje DSL negenerují kód, který implementuje metodu.

Definování tato metoda vytvoří sledovací popisovač vlastnosti pro Namespace vlastnost sledování. Také umožňuje poskytuje atributy pro vlastnosti sledování **vlastnosti** okno k zobrazení vlastnost správně.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Chcete-li změnit popisovač typu pro doménovou třídu ExampleModel

1.  Přidejte následující kód do souboru TypeDescriptor.cs.

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>Přidání vlastního kódu pro balíček

Generovaný kód definuje poskytovatele popisů typů pro doménovou třídu ExampleElement; Nicméně je nutné přidat kód dáte pokyn, aby DSL k používání tohoto poskytovatele typu popis.

1.  Přidejte následující kód do souboru Package.cs.

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-model"></a>Přidání vlastního kódu pro Model

Implementace `GetCustomElementsValue` metodu `ExampleModel` doménovou třídu.

> [!NOTE]
> Kód, který nástroje DSL vygenerovat pro `ExampleModel` volání `GetCustomElementsValue`, nicméně nástroje DSL negenerují kód, který implementuje metodu.

Definování `GetCustomElementsValue` metoda obsahuje logiku pro vlastnost CustomElements počítá `ExampleModel`. Tato metoda vrátí počet `ExampleElement` doménovými třídami, které mají Namespace sledování vlastnost, která má uživatel aktualizovat hodnotu a vrátí řetězec, který představuje tento počet jako podíl celkové prvky v modelu.

Kromě toho přidejte `OnDefaultNamespaceChanged` metodu `ExampleModel`a přepsat `OnValueChanged` metodu `DefaultNamespacePropertyHandler` vnořené třídy `ExampleModel` volat `OnDefaultNamespaceChanged`.

Protože vlastností DefaultNamespace se používá k výpočtu Namespace vlastnost, sledování `ExampleModel` oznámí všechny `ExampleElement` doménovými třídami, které hodnota DefaultNamespace se změnila.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Chcete-li změnit obslužné rutiny vlastnosti sledované vlastnosti

1.  Přidejte následující kód do souboru ExampleModel.cs.

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-for-the-tracking-property"></a>Přidání vlastního kódu pro vlastnost sledování

Přidat `CalculateNamespace` metodu `ExampleElement` doménovou třídu.

Definování tato metoda poskytuje logiku pro vlastnost CustomElements počítá `ExampleModel`. Tato metoda vrátí počet `ExampleElement` doménovými třídami, které mají Namespace sledování vlastnost, která se v aktualizovaném podle stavu uživatele a vrátí řetězec, který představuje tento počet jako podíl celkové prvky v modelu.

Přidejte také úložiště pro a metody k získání a nastavení, vlastnost Namespace vlastního úložiště `ExampleElement` doménovou třídu.

> [!NOTE]
> Kód, který pro generování nástroje DSL `ExampleModel` volání get a set metod; však nástroje DSL negenerují kód, který implementuje metodu.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Chcete-li přidat metodu pro vlastní typ popisovače

1.  Přidejte následující kód do souboru NamespaceTrackingProperty.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-to-support-serialization"></a>Přidání vlastního kódu pro podporu serializace

Přidání kódu, který podporuje vlastní chování po načtení pro serializaci kódu XML.

> [!NOTE]
> Kód, nástroje DSL generovat volání `OnPostLoadModel` a `OnPostLoadModelAndDiagram` metody; však nástroje DSL negenerují kód, který implementuje tyto metody.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Přidání kódu, který podporuje vlastní chování po načtení

1.  Přidejte následující kód do souboru Serialization.cs.

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="test-the-language"></a>Testování jazyk

Dalším krokem je sestavte a spusťte návrháře DSL v nové instanci [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , aby mohli ověřit, že vlastnosti sledování pracuje správně.

1. Na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit řešení**.

2. Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.

    Experimentální sestavení [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] otevře **ladění** řešení, která obsahuje soubor prázdný test.

3. V **Průzkumníka řešení**, poklikejte na soubor Test.trackingPropertyDsl ho otevřete v návrháři a klikněte na návrhové ploše.

    Všimněte si, že v **vlastnosti** okně diagramu **výchozí Namespace** vlastnost **DefaultNamespace**a **vlastní elementy** vlastnost **0/0**.

4. Přetáhněte **ExampleElement** element z **nástrojů** na plochu diagramu.

5. V **vlastnosti** okna pro element, vyberte **Element Namespace** vlastnost a změňte hodnotu z **DefaultNamespace** k  **OtherNamespace**.

    Všimněte si, že hodnota **Element Namespace** se nyní zobrazí tučným písmem.

6. V **vlastnosti** okna, klikněte pravým tlačítkem na **Element Namespace**a potom klikněte na tlačítko **resetování**.

    Hodnota vlastnosti byla změněna na **DefaultNamespace**, a hodnota se zobrazí v pravidelných písma.

    Klikněte pravým tlačítkem na **Element Namespace** znovu. **Resetování** příkaz je teď zakázaná, protože vlastnost je aktuálně ve stavu sledování.

7. Přetáhněte další **ExampleElement** z **nástrojů** na plochu diagramu a změňte jeho **Element Namespace** k **OtherNamespace**.

8. Klikněte na návrhové ploše.

    V **vlastnosti** okno pro diagram hodnotu **vlastní elementy** je nyní **1/2**.

9. Změna **výchozí Namespace** diagramu z **DefaultNamespace** k **obor NewNamespace**.

     **Namespace** první prvek stop **výchozí Namespace** vlastnost, že **Namespace** druhého prvku uchovává svou hodnotu uživatelaktualizoval **OtherNamespace**.

10. Uložte řešení a pak zavřete experimentální sestavení.

## <a name="next-steps"></a>Další kroky

Pokud budete chtít použít více než jedna sledovací vlastnost nebo implementovat vlastnosti sledování do více než jednom DSL, můžete vytvořit textové šablony pro generování společný kód pro podporu každé vlastnosti sledování. Další informace o textových šablonách naleznete v tématu [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
- [Postupy: Vytváření řešení jazyka specifického pro doménu](../modeling/how-to-create-a-domain-specific-language-solution.md)
