---
title: Přidání vlastnosti sledování do definice DSL
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccac40e2ff11b4da67c95fba307de97e4f72a101
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238241"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Přidání vlastnosti sledování do definice jazyka specifického pro doménu

Tento návod ukazuje, jak přidat vlastnost sledování do doménového modelu.

Vlastnost *prostrkání Domain* je vlastnost, kterou může aktualizovat uživatel, ale má výchozí hodnotu, která je vypočítána pomocí hodnot jiných vlastností nebo prvků domény.

Například v Nástroje DSL (nástroje DSL) má vlastnost zobrazovaný název třídy domény výchozí hodnotu, která je vypočítána pomocí názvu doménové třídy, ale uživatel může změnit hodnotu v době návrhu nebo ji obnovit na počítanou hodnotu.

V tomto návodu vytvoříte jazyk specifický pro doménu (DSL), který má vlastnost sledování oboru názvů, která má výchozí hodnotu založenou na vlastnosti výchozího oboru názvů modelu. Další informace o vlastnostech sledování najdete v tématu [Definování vlastností sledování](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- Nástroje DSL podporují popisovače vlastností sledování. Návrhář DSL však nelze použít k přidání vlastnosti sledování do jazyka. Proto je nutné přidat vlastní kód pro definování a implementaci sledovací vlastnosti.

  Vlastnost sledování má dva stavy: sledování a aktualizováno uživatelem. Vlastnosti sledování mají následující funkce:

- Když je ve stavu sledování vypočtena hodnota vlastnosti sledování a hodnota je aktualizována jako ostatní vlastnosti v rámci změny modelu.

- Když se v aktualizovaném stavu uživatele aktualizuje hodnota vlastnosti sledování, zachová se hodnota, na kterou uživatel naposledy nastavil vlastnost.

- V okně **vlastnosti** je příkaz **resetování** pro vlastnost Tracking povolen pouze v případě, že je vlastnost aktualizována stavem uživatele. Příkaz **reset** nastaví stav vlastnosti sledování na sledování.

- V okně **vlastnosti** , když je vlastnost sledování ve stavu sledování, je její hodnota zobrazena v běžném písmu.

- V okně **vlastnosti** , když je vlastnost sledování v aktualizovaném stavu uživatele, je tato hodnota zobrazena tučným písmem.

## <a name="prerequisites"></a>Předpoklady

Než budete moct spustit tento návod, musíte nejdřív nainstalovat tyto komponenty:

| Komponenta | Odkaz |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](https://code.msdn.microsoft.com/site/search?query=%22Modeling%20SDK%22&f%5B0%5D.Value=%22Modeling%20SDK%22&f%5B0%5D.Type=SearchText&ac=5) |

## <a name="create-the-project"></a>Vytvoření projektu

1. Vytvořte projekt návrháře jazyka specifického pro doménu. Pojmenujte ji `TrackingPropertyDSL`.

2. V **Průvodci návrháře jazyka specifického pro doménu**nastavte následující možnosti:

    1. Vyberte šablonu **MinimalLanguage** .

    2. Pro jazyk specifický pro doménu použijte výchozí název `TrackingPropertyDSL` .

    3. Nastavte rozšíření pro soubory modelů na `trackingPropertyDsl` .

    4. Pro soubory modelu použijte výchozí ikonu šablony.

    5. Nastavte název produktu na `Product Name` .

    6. Nastavte název společnosti na `Company Name` .

    7. Použijte výchozí hodnotu pro kořenový obor názvů pro projekty v řešení, `CompanyName.ProductName.TrackingPropertyDSL` .

    8. Umožňuje průvodci vytvořit soubor klíče se silným názvem pro vaše sestavení.

    9. Zkontrolujte podrobnosti řešení a potom kliknutím na tlačítko **Dokončit** vytvořte projekt definice DSL.

## <a name="customize-the-default-dsl-definition"></a>Přizpůsobení výchozí definice DSL
 V této části si přizpůsobíte definici DSL tak, aby obsahovala následující položky:

- Vlastnost sledování oboru názvů pro každý prvek modelu.

- Logická vlastnost IsNamespaceTracking pro každý prvek modelu. Tato vlastnost určuje, zda je vlastnost sledování ve stavu sledování nebo aktualizována stavem uživatele.

- Výchozí vlastnost oboru názvů pro model Tato vlastnost se použije k výpočtu výchozí hodnoty vlastnosti sledování oboru názvů.

- Vypočítaná vlastnost CustomElements pro model. Tato vlastnost bude označovat poměr prvků, které mají vlastní obor názvů.

### <a name="to-add-the-domain-properties"></a>Přidání vlastností domény

1. V Návrháři DSL klikněte pravým tlačítkem na doménovou třídu **ExampleModel** , přejděte na **Přidat**a pak klikněte na **doménová vlastnost**.

    1. Pojmenujte novou vlastnost `DefaultNamespace` .

    2. V okně **vlastnosti** nové vlastnosti nastavte **Výchozí hodnota** na `DefaultNamespace` a nastavte **typ** na **řetězec**.

2. Do třídy domény **ExampleModel** přidejte doménovou vlastnost s názvem `CustomElements` .

     V okně **vlastnosti** nové vlastnosti nastavte **druh** na **počítané**.

3. Do třídy domény **ExampleElement** přidejte doménovou vlastnost s názvem `Namespace` .

     V okně **vlastnosti** pro novou vlastnost **je** nastaveno procházení na **false**a nastavte **druh** na **nemá CustomStorage**.

4. Do třídy domény **ExampleElement** přidejte doménovou vlastnost s názvem `IsNamespaceTracking` .

     V okně **vlastnosti** pro novou vlastnost je nastavena hodnota **Procházet** na **false**, nastavit **výchozí hodnotu** na `true` a nastavit **typ** na **Boolean**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Aktualizace elementů diagramu a podrobností DSL

1. V Návrháři DSL klikněte pravým tlačítkem myši na obrazec geometrie **ExampleShape** , přejděte na **Přidat**a pak klikněte na **text dekoratér**.

    1. Pojmenujte nový text dekoratér `NamespaceDecorator` .

    2. V okně **vlastnosti** pro text dekoratér nastavte vlastnost **pozice** na **InnerBottomLeft**.

2. V Návrháři DSL vyberte čáru, která spojuje třídu **ExampleElement** s obrazcem **ExampleShape** .

    1. V okně **Podrobnosti DSL** vyberte kartu **mapy dekoratér** .

    2. V seznamu **dekoratéry** vyberte možnost **NamespaceDecorator**, zaškrtněte příslušné políčko a potom v seznamu **vlastností zobrazení** vyberte možnost **obor názvů**.

3. V **Průzkumníku DSL**rozbalte složku **třídy domény** , klikněte pravým tlačítkem na uzel **ExampleElement** a pak klikněte na **Přidat nový popisovač typu domény**.

    1. Rozbalte uzel **ExampleElement** a vyberte uzel **popisovač vlastního typu (popisovač typu domény)** .

    2. V okně **vlastnosti** pro popisovač typu domény nastavte **vlastní kód** na **hodnotu true**.

4. V **Průzkumníku DSL**vyberte uzel **chování serializace XML** .

    1. V okně **vlastnosti** nastavte **vlastní post Load** na true ( **pravda**).

## <a name="transform-templates"></a>Transformace šablon

Teď, když jste definovali doménové třídy a vlastnosti pro DSL, můžete ověřit, že definice DSL se dá transformovat správně, aby se znovu vygeneroval kód pro váš projekt.

1. Na panelu nástrojů **Průzkumník řešení** klikněte na možnost **transformovat všechny šablony**.

2. Systém znovu vygeneruje kód pro řešení a uloží DslDefinition. DSL. Informace o formátu XML definičních souborů najdete v [souboru DslDefinition. DSL](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Vytváření souborů pro vlastní kód

Při transformaci všech šablon systém generuje zdrojový kód definující jazyk specifický pro doménu v projektech DSL a DslPackage. Takže se můžete vyhnout kolizi s generovaným textem, napsat vlastní kód v souborech, které jsou odlišné od generovaných souborů kódu.

Je nutné zadat kód pro zachování hodnoty a stavu vlastnosti sledování. Abychom vám pomohli odlišit svůj vlastní kód od generovaného kódu a vyhnout se konfliktům při pojmenovávání souborů, umístěte vlastní soubory kódu do samostatné podsložky.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **DSL** , přejděte na **Přidat**a pak klikněte na **Nová složka**. Pojmenujte novou složku `CustomCode` .

2. Klikněte pravým tlačítkem na novou složku **CustomCode** , přejděte na **Přidat**a klikněte na **Nová položka**.

3. Vyberte šablonu **soubor kódu** , nastavte **název** na `NamespaceTrackingProperty.cs` a pak klikněte na **OK**.

     Soubor NamespaceTrackingProperty.cs se vytvoří a otevře pro úpravy.

4. Ve složce vytvořte následující soubory kódu: `ExampleModel.cs,``HelperClasses.cs` , `Serialization.cs` , a `TypeDescriptor.cs` .

5. V projektu **DslPackage** také vytvořte `CustomCode` složku a přidejte do ní `Package.cs` soubor kódu.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Přidat pomocné třídy pro podporu vlastností sledování

Do souboru HelperClasses.cs přidejte `TrackingHelper` `CriticalException` třídy a následujícím způsobem. Na tyto třídy se odkazuje později v tomto návodu.

1. Do souboru HelperClasses.cs přidejte následující kód.

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

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Přidat vlastní kód pro popisovač vlastního typu

Implementujte `GetCustomProperties` metodu pro popisovač typu pro `ExampleModel` doménovou třídu.

> [!NOTE]
> Kód, který vygeneruje nástroje DSL pro vlastní deskriptor typu pro `ExampleModel` volání `GetCustomProperties` . nástroje DSL však negenerují kód, který implementuje metodu.

Definování této metody vytvoří popisovač sledovacích vlastností pro vlastnost sledování oboru názvů. Poskytnutí atributů pro vlastnost sledování také umožňuje, aby okno **vlastností** zobrazilo vlastnost správně.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Úprava popisovače typu pro doménovou třídu ExampleModel

1. Do souboru TypeDescriptor.cs přidejte následující kód.

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

Generovaný kód definuje poskytovatele popisu typu pro doménovou třídu ExampleElement; je však nutné přidat kód, který instruuje DSL na použití tohoto poskytovatele popisu typu.

1. Do souboru Package.cs přidejte následující kód.

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

## <a name="add-custom-code-for-the-model"></a>Přidání vlastního kódu pro model

Implementujte `GetCustomElementsValue` metodu pro `ExampleModel` doménovou třídu.

> [!NOTE]
> Kód, který nástroje DSL generují pro `ExampleModel` volání. `GetCustomElementsValue` nástroje DSL však negenerují kód, který implementuje metodu.

Definování `GetCustomElementsValue` metody poskytuje logiku pro vypočítanou vlastnost CustomElements `ExampleModel` . Tato metoda spočítá počet `ExampleElement` tříd domény, které mají vlastnost sledování oboru názvů s uživatelem aktualizovanou hodnotou, a vrátí řetězec, který představuje tento počet jako podíl celkových prvků v modelu.

Kromě toho přidejte `OnDefaultNamespaceChanged` metodu do `ExampleModel` a přepište `OnValueChanged` metodu `DefaultNamespacePropertyHandler` vnořené třídy `ExampleModel` pro volání `OnDefaultNamespaceChanged` .

Vzhledem k tomu, že vlastnost DefaultNamespace se používá k výpočtu vlastnosti sledování oboru názvů, `ExampleModel` musí upozorňovat na všechny `ExampleElement` třídy domény, že hodnota DefaultNamespace se změnila.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Úprava obslužné rutiny vlastnosti pro sledovanou vlastnost

1. Do souboru ExampleModel.cs přidejte následující kód.

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

## <a name="add-custom-code-for-the-tracking-property"></a>Přidat vlastní kód pro vlastnost sledování

Přidejte `CalculateNamespace` metodu do `ExampleElement` doménové třídy.

Definování této metody poskytuje logiku pro vypočítanou vlastnost CustomElements `ExampleModel` . Tato metoda spočítá počet `ExampleElement` tříd domény, které mají vlastnost sledování oboru názvů, která je aktualizována stavem uživatele, a vrátí řetězec, který představuje tento počet jako podíl celkového prvku v modelu.

Přidejte také úložiště pro a metody pro Get a set, vlastnost vlastního úložiště oboru názvů `ExampleElement` třídy Domain.

> [!NOTE]
> Kód, který nástroje DSL generuje pro `ExampleModel` volání metod get a set, ale nástroje DSL negenerují kód, který implementuje metody.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Přidání metody pro vlastní popisovač typu

1. Do souboru NamespaceTrackingProperty.cs přidejte následující kód.

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

## <a name="add-custom-code-to-support-serialization"></a>Přidat vlastní kód pro podporu serializace

Přidejte kód pro podporu vlastního chování po načtení pro serializaci XML.

> [!NOTE]
> Kód, který generují nástroje DSL, volá `OnPostLoadModel` metody a, `OnPostLoadModelAndDiagram` ale nástroje DSL negenerují kód, který tyto metody implementuje.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Přidání kódu pro podporu vlastního chování po načtení

1. Do souboru Serialization.cs přidejte následující kód.

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

## <a name="test-the-language"></a>Testování jazyka

Dalším krokem je sestavení a spuštění návrháře DSL v nové instanci nástroje [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , abyste mohli ověřit, že vlastnost sledování pracuje správně.

1. V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**.

2. V nabídce **Ladit** klikněte na **Spustit ladění**.

    Experimentální sestavení [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] otevře **ladicí** řešení, které obsahuje prázdný testovací soubor.

3. V **Průzkumník řešení**dvakrát klikněte na soubor test. trackingPropertyDsl, aby se otevřel v návrháři, a pak klikněte na návrhovou plochu.

    Všimněte si, že v okně **vlastnosti** diagramu je výchozí vlastnost **Namespace** **DefaultNamespace**a vlastnost **Custom Elements** je **0/0**.

4. Přetáhněte element **ExampleElement** z **panelu nástrojů** na plochu diagramu.

5. V okně **vlastnosti** prvku vyberte vlastnost **Namespace elementu** a změňte hodnotu z **DefaultNamespace** na **OtherNamespace**.

    Všimněte si, že hodnota **oboru názvů element** je nyní zobrazena tučně.

6. V okně **vlastnosti** klikněte pravým tlačítkem myši na **obor názvů element**a potom klikněte na **resetovat**.

    Hodnota vlastnosti se změní na **DefaultNamespace**a hodnota se zobrazí v běžném písmu.

    Znovu klikněte pravým tlačítkem na **obor názvů elementu** . Příkaz pro **obnovení** je teď zakázaný, protože tato vlastnost je aktuálně ve stavu sledování.

7. Přetáhněte další **ExampleElement** z **panelu nástrojů** na plochu diagramu a změňte jeho **obor názvů element** na **OtherNamespace**.

8. Klikněte na plochu návrhu.

    V okně **vlastnosti** diagramu je hodnota **vlastních prvků** nyní **1/2**.

9. Změňte **výchozí obor názvů** pro diagram z **DefaultNamespace** na **NewNamespace**.

     **Obor názvů** prvního prvku sleduje **výchozí vlastnost oboru názvů** , zatímco **obor názvů** druhého prvku uchovává jeho hodnotu **OtherNamespace**.

10. Uložte řešení a pak zavřete experimentální sestavení.

## <a name="next-steps"></a>Další kroky

Pokud plánujete použít více než jednu vlastnost sledování nebo implementovat vlastnosti sledování ve více než jedné DSL, můžete vytvořit textovou šablonu, která generuje společný kód pro podporu jednotlivých vlastností sledování. Další informace o textových šablonách naleznete v tématu [Code Generation and T4 text Templates](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
- [Postupy: Vytváření řešení jazyka specifického pro doménu](../modeling/how-to-create-a-domain-specific-language-solution.md)
