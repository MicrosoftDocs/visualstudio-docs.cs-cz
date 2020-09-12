---
title: Použití Microsoft. VisualStudio. TestTools. UnitTesting v testování částí
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 9d68e26e8503fb450d6b163ecec31c0cb6485f6c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038618"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Použití rozhraní MSTest v testování částí

Rozhraní [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) podporuje testování částí v aplikaci Visual Studio. Při kódování testů jednotek použijte třídy a členy v <xref:Microsoft.VisualStudio.TestTools.UnitTesting> oboru názvů. Můžete je také použít při rerafinaci testu jednotek, který byl vygenerován z kódu.

## <a name="framework-members"></a>Členové architektury

Abychom vám pomohli poskytnout jasný přehled rozhraní testování částí, Tato část uspořádá členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting> oboru názvů do skupin souvisejících funkcí.

> [!NOTE]
> Prvky atributu, jejichž názvy končí na "Attribute", lze použít buď s atributem "nebo bez" atributu "na konci. Například následující dvě příklady kódu mají stejnou funkci:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Členy používané pro testování řízené daty

Pomocí následujících prvků nastavte testy jednotek řízené daty. Další informace najdete v tématu [Vytvoření testu jednotek řízeného daty](../test/how-to-create-a-data-driven-unit-test.md) a [použití konfiguračního souboru k definování zdroje dat](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atributy používané k vytvoření pořadí volání

Prvek kódu upravený jedním z následujících atributů je volán v okamžiku, kdy zadáte. Další informace naleznete v tématu [anatomie testu jednotek](/previous-versions/ms182517(v=vs.110)).

### <a name="attributes-for-assemblies"></a>Atributy pro sestavení

Atributem AssemblyInitialize a atributem AssemblyCleanup jsou volány hned po načtení sestavení a napravo před uvolněním sestavení.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Atributy pro třídy

ClassInitialize a ClassCleanup jsou volány hned po načtení třídy a správné před uvolněním třídy.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Atributy testovacích metod

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atributy používané k identifikaci testovacích tříd a metod

Každá testovací třída musí mít `TestClass` atribut a každá testovací metoda musí mít `TestMethod` atribut. Další informace naleznete v tématu [anatomie testu jednotek](/previous-versions/ms182517(v=vs.110)).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Vyhodnocení tříd a souvisejících výjimek

Testy jednotek mohou ověřit konkrétní chování aplikace podle jejich použití různými druhy kontrolních výrazů, výjimek a atributů. Další informace najdete v tématu [použití tříd Assert](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>Třída TestContext

Následující atributy a hodnoty, které jsou přiřazeny, se zobrazí v okno Vlastnosti sady Visual Studio pro konkrétní testovací metodu. Tyto atributy nejsou určeny pro použití v kódu testu jednotek. Místo toho ovlivňují způsoby použití nebo spuštění testu jednotky, a to buď prostřednictvím integrovaného vývojového prostředí (IDE) sady Visual Studio, nebo pomocí testovacího modulu sady Visual Studio. Například některé z těchto atributů se zobrazí jako sloupce v okně **Test Manager** a v **výsledky testů** okně, což znamená, že je můžete použít k seskupení a seřazení testů a výsledků testů. Jeden z těchto atributů je <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> , který použijete k přidání libovolných metadat k jednotkovým testům. Můžete ji například použít k uložení názvu testu průchodu, který tento test pokrývá, označením testu jednotky pomocí `[TestProperty("TestPass", "Accessibility")]` . Nebo můžete použít k uložení indikátoru typu testu, u kterého se jedná `[TestProperty("TestKind", "Localization")]` . Vlastnost, kterou vytvoříte pomocí tohoto atributu a hodnotu vlastnosti, kterou přiřadíte, se zobrazí v okně **vlastnosti** sady Visual Studio pod položkou **test**pro daný nadpis.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Třídy konfigurace testu

- [ObjectType](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Atributy používané ke generování sestav

Atributy v této části se vztahují na testovací metodu, kterou upraví na entity v hierarchii projektu Team Foundation Server týmového projektu.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Třídy používané s privátními přistupujícími objekty

Můžete vygenerovat test jednotky pro soukromou metodu. Tato generace vytvoří třídu soukromého přístupového objektu, která vytvoří instanci objektu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> třídy. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>Třída je Obálková třída, která používá reflexi v rámci procesu privátního přístupového objektu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>Třída je podobná, ale používá se pro volání privátních statických metod namísto volání metod soukromé instance.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Referenční dokumentace