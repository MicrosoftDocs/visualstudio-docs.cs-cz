---
title: Používání členů oboru názvů Microsoft.VisualStudio.TestTools.UnitTesting při testech jednotek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: gewarren
manager: douge
ms.openlocfilehash: 691b1e46f7657eb027fa48b31f31119cae0c7451
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216643"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Používání členů oboru názvů Microsoft.VisualStudio.TestTools.UnitTesting při testech jednotek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Rozhraní testování částí podporuje testování jednotek v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Používání tříd a členů v <xref:Microsoft.VisualStudio.TestTools.UnitTesting> obor názvů při psaní kódu testování částí. Je můžete použít, když jste napsali jednotky testování úplně od začátku nebo Jednotkový test, který byl vytvořen kód, který testujete dolaďování.

## <a name="groups-of-elements"></a>Skupiny prvků
 Jak zajistit lepší přehled o rozhraní testování částí, v této části slouží k uspořádání prvků obor názvů UnitTesting do skupiny související funkce.

> [!NOTE]
> Atribut elementy, jejichž názvy zakončen atribut řetězců, je možné s nebo bez atribut řetězců. Například následující dva příklady pracovat stejně jako:
>
>  `[TestClass()]`
>
>  `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>Prvků, které slouží pro testování řízené daty
 Nastavte testy jednotek řízené daty pomocí následující prvky. Další informace najdete v tématu [postupy: vytvoření testu jednotek data-Driven](../test/how-to-create-a-data-driven-unit-test.md) a [návod: použití konfiguračního souboru k definování zdroje dat](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Používá pro volací pořadí atributů
 Prvek kódu upraven pomocí jedné z následujících atributů je volána v okamžiku, kdy je zadat. Další informace najdete v tématu [anatomie testování částí](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Pro sestavení
 AssemblyInitialize a AssemblyCleanup se nazývají doprava po načtení sestavení a pravá před uvolněním vaše sestavení.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>Pro třídy
 ClassInitialize a ClassCleanup se nazývají doprava po načtení třídu a právo před uvolněním vaší třídy.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>Pro testovací metody

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atributy, které slouží k identifikaci testovací třídy a metody
 Každý testovací třídě musí mít atribut TestClass a každou zkušební metodu, musí mít atribut TestMethod. Další informace najdete v tématu [anatomie testování částí](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Assert – třídy a související výjimky.
 Testy jednotek můžete ověřit chování konkrétní aplikace podle jejich využívání různých druhů příkazů Assert, výjimky a atributů. Další informace najdete v tématu [používání tříd Assert](../test/using-the-assert-classes.md).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Třída TestContext
 Následující atributy a hodnoty přiřazené k jejich joinkind [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno vlastností pro konkrétní testovací metodu. Tyto atributy nejsou určeny k přístupné z kódu testování částí. Místo toho, které ovlivňují způsobem používá testování částí nebo spusťte skript, buď můžete prostřednictvím rozhraní IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nebo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] testovací stroj. Například některé z těchto atributů zobrazí jako sloupce v okně nástroje Test Manager a v okně Výsledky testu, což znamená, že můžete použít k seskupení a řazení testy a výsledky testů. Jeden atribut je TestPropertyAttribute, které můžete přidat libovolné metadata pro testování částí. Například může použít k uložení názvu průchodu testu, který se zabývá tento test s označením test jednotky s `[TestProperty("TestPass", "Accessibility")]`. Nebo ho může použít k ukládání indikátor druh testu je: `[TestProperty("TestKind", "Localization")]`. Obě vlastnosti vytvoříte pomocí tohoto atributu a hodnota vlastnosti přiřadíte, jsou zobrazeny v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna Vlastnosti pod záhlavím **konkrétní Test**.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Třídy pro konfiguraci testu

-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-for-generating-reports"></a>Atributy použité pro generování sestav
 Atributy v této části se týkají testovací metodu, jejich uspořádání entit v hierarchii projektu [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] týmový projekt.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Třídy používané s privátní přístupové objekty
 Jak je popsáno v [pomocí Publicize k vytvoření privátního přístupového objektu](http://msdn.microsoft.com/en-us/2056c6a7-6672-42a7-8f53-fead33c56deb), můžete vygenerovat testování částí pro soukromou metodu. Tato generace vytvoří třídy privátního přístupového objektu, který vytvoří instanci objektu třídy PrivateObject. Třída PrivateObject je třídou obálky, která používá reflexi jako součást procesu privátního přístupového objektu. Třída PrivateType se podobá, ale slouží pro volání privátní statické metody namísto volání metody privátní instance.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>