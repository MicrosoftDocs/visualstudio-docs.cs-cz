---
title: Používání členů oboru názvů Microsoft.VisualStudio.TestTools.UnitTesting při testech jednotek
ms.date: 03/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bad6f01a49856e44120c0dc121ee262d9d26506c
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295602"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Použití rozhraní MSTest při testech jednotek

[MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) framework podporuje testování jednotek v sadě Visual Studio. Používání tříd a členů v <xref:Microsoft.VisualStudio.TestTools.UnitTesting> obor názvů při psaní kódu testování částí. Můžete také je při dolaďování Jednotkový test, který byl vytvořen kód.

## <a name="framework-members"></a>Členy rozhraní Framework

Jak zajistit lepší přehled o rozhraní testování části, v této části slouží k uspořádání členů <xref:Microsoft.VisualStudio.TestTools.UnitTesting> oboru názvů do skupin související funkce.

> [!NOTE]
> Atribut elementy, jejichž názvy končí "Atribut", je možné s nebo bez "Atribut" na konci. Například následující dva příklady pracovat stejně jako:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Členové, používá se pro testování řízené daty

Nastavte testy jednotek řízené daty pomocí následující prvky. Další informace najdete v tématu [vytvoření testu jednotek řízené daty](../test/how-to-create-a-data-driven-unit-test.md) a [pomocí konfiguračního souboru k definování zdroje dat](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atributy použité k vytvoření pořadí volání

Prvek kódu upraven pomocí jedné z následujících atributů je volána v okamžiku, kdy je zadat. Další informace najdete v tématu [anatomie testování částí](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="attributes-for-assemblies"></a>Atributy pro sestavení

AssemblyInitialize a AssemblyCleanup se nazývají doprava po načtení sestavení a pravá před uvolněním vaše sestavení.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Atributy třídy

ClassInitialize a ClassCleanup se nazývají doprava po načtení třídu a právo před uvolněním vaší třídy.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Atributy pro testovací metody

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atributy, které slouží k identifikaci testovací třídy a metody

Každý testovací třídě musí mít `TestClass` atribut a každou zkušební metodu, musí být `TestMethod` atribut. Další informace najdete v tématu [anatomie testování částí](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Assert – třídy a související výjimky.

Testy jednotek můžete ověřit chování konkrétní aplikace podle jejich využívání různých druhů atributy, výjimky a kontrolní výrazy. Další informace najdete v tématu [používání tříd assert](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Třída TestContext

Následující atributy a hodnoty přiřazené k nim se zobrazí v okně vlastností Visual Studio pro konkrétní testovací metodu. Tyto atributy nejsou určeny k přístupné z kódu testování částí. Místo toho mají vliv způsoby testování částí se používá nebo spustit, můžete pomocí integrovaného vývojového prostředí sady Visual Studio, nebo testovacím modulem Visual Studio. Například některé z těchto atributů se zobrazí jako sloupce v **Test Manager** okno a **výsledky testu** okna, což znamená, že můžete použít k seskupení a řazení testy a výsledky testů. Je jeden atribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>, které můžete přidat libovolné metadata pro testování částí. Například může použít k uložení názvu průchodu testu, který se zabývá tento test s označením test jednotky s `[TestProperty("TestPass", "Accessibility")]`. Nebo ho může použít k ukládání indikátor druh testu je s `[TestProperty("TestKind", "Localization")]`. Obě vlastnosti, které vytvoříte pomocí tohoto atributu a hodnota vlastnosti přiřadíte, se zobrazí v sadě Visual Studio **vlastnosti** okno pod záhlavím **konkrétní Test**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Třídy pro konfiguraci testu

- <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Atributy použité ke generování sestav

Atributy v této části se týkají testovací metodu, jejich uspořádání entit v hierarchii projektu týmového projektu serveru Team Foundation Server.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Třídy používané s privátní přístupové objekty

Můžete generovat testování částí pro soukromou metodu. Tato generace vytvoří třídy privátního přístupového objektu, který vytvoří instanci objektu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> třídy. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> Třída je třídou obálky, která používá reflexi jako součást procesu privátního přístupového objektu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> Třídy je podobné, ale slouží pro volání privátní statické metody namísto volání metody privátní instance.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Referenční dokumentace
