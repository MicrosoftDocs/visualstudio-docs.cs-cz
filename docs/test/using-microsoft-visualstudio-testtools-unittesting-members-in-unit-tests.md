---
title: Použití microsoft.VisualStudio.TestTools.UnitTesting v jednotkových testech
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e45df63f36947b5f6f0aad77bb8eebcab4aca731
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585558"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Použití architektury MSTest v jednotkových testech

Rozhraní [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) podporuje testování částí v sadě Visual Studio. Třídy a členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting> v oboru názvů při kódování testů částí. Můžete je také použít při zdokonalování testování částí, který byl vygenerován z kódu.

## <a name="framework-members"></a>Členové rámce

Chcete-li poskytnout jasnější přehled o rozhraní testování částí, tato <xref:Microsoft.VisualStudio.TestTools.UnitTesting> část uspořádá členy oboru názvů do skupin souvisejících funkcí.

> [!NOTE]
> Atribut ové prvky, jejichž názvy končí "Atribut", lze použít buď s nebo bez "Atribut" na konci. Například následující dva příklady kódu fungují stejně:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Členy používané pro testování založené na datech

Následující prvky slouží k nastavení testů částí řízených daty. Další informace naleznete [v tématu Vytvoření testu částí řízených daty](../test/how-to-create-a-data-driven-unit-test.md) a [Definování zdroje dat pomocí konfiguračního souboru](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atributy používané k vytvoření volací objednávky

Prvek kódu zdobený jedním z následujících atributů je volán v okamžiku, kdy zadáte. Další informace naleznete [v tématu Anatomie jednotkového testu](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="attributes-for-assemblies"></a>Atributy pro sestavení

SestavaInitialize a AssemblyCleanup jsou volána ihned po sestavení je načten a těsně před sestavení je uvolněna.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Atributy pro třídy

ClassInitialize a ClassCleanup jsou volány hned po načtení třídy a těsně před uvolněním třídy.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Atributy pro zkušební metody

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atributy používané k identifikaci testovacích tříd a metod

Každá testovací třída `TestClass` musí mít atribut a každá `TestMethod` zkušební metoda musí mít atribut. Další informace naleznete [v tématu Anatomie jednotkového testu](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Assert třídy a související výjimky

Testy částí můžete ověřit chování konkrétní aplikace jejich použití různých druhů kontrolnívýrazy, výjimky a atributy. Další informace naleznete [v tématu Using the assert classes](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>Třída TestContext

Následující atributy a hodnoty, které jim byly přiřazeny, se zobrazí v okně Vlastnosti sady Visual Studio pro konkrétní testovací metodu. Tyto atributy nejsou určeny pro přístup prostřednictvím kódu testování částí. Místo toho ovlivňují způsoby použití nebo spuštění testu částí, a to buď prostřednictvím ide sady Visual Studio, nebo testovacím strojem sady Visual Studio. Některé z těchto atributů se například zobrazí jako sloupce v okně **Správce testů** a v okně **Výsledky testů,** což znamená, že je můžete použít k seskupení a řazení testů a výsledků testů. Jeden takový <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>atribut je , který slouží k přidání libovolných metadat do testů částí. Můžete jej například použít k uložení názvu testovacího průchodu, který tento `[TestProperty("TestPass", "Accessibility")]`test pokrývá, označením testu částí pomocí . Nebo jej můžete použít k uložení indikátoru druhu testu, který je s `[TestProperty("TestKind", "Localization")]`. Vlastnost, kterou vytvoříte pomocí tohoto atributu, a hodnota vlastnosti, kterou přiřadíte, se zobrazí v okně **Vlastnosti** sady Visual Studio pod nadpisem **Test specific**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Testovat třídy konfigurace

- [Type objektu](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Atributy používané ke generování sestav

Atributy v této části se týkají testovací metody, které zdobí entity v hierarchii projektu týmového projektu Team Foundation Server.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Třídy používané s privátními přístupovými mikinami

Můžete vygenerovat testování částí pro soukromou metodu. Toto generování vytvoří třídu soukromého přistupujícího <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> objektu, která vytváří instance objektu třídy. Třída <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> je obálka třídy, která používá reflexe jako součást procesu soukromého přístupového procesu. Třída <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> je podobná, ale používá se pro volání privátních statických metod namísto volání metod privátní instance.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>referenční dokumentace
