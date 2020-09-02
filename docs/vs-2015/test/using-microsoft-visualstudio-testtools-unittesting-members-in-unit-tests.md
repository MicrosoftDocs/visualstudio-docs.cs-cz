---
title: Použití členů Microsoft. VisualStudio. TestTools. UnitTesting v testování částí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e8b3ea10b96a63bd18098030dc884ac3f3383353
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657189"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Používání členů oboru názvů Microsoft.VisualStudio.TestTools.UnitTesting při testování částí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Rozhraní testování částí podporuje testování částí v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Při kódování testů jednotek použijte třídy a členy v <xref:Microsoft.VisualStudio.TestTools.UnitTesting> oboru názvů. Můžete je použít, když jste napsali test jednotky od začátku nebo pokud chcete remotivovat test jednotek, který byl vygenerován z testovaného kódu.

## <a name="groups-of-elements"></a>Skupiny prvků
 Abychom vám pomohli poskytnout jasný přehled rozhraní testování částí, Tato část uspořádá prvky oboru názvů UnitTesting do skupin souvisejících funkcí.

> [!NOTE]
> Prvky atributu, jejichž názvy se uzavírají s řetězcovým atributem, lze použít buď s řetězcovým atributem nebo bez něj. Například následující dvě příklady kódu mají stejnou funkci:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>Prvky používané pro testování řízené daty
 Pomocí následujících prvků nastavte testy jednotek řízené daty. Další informace najdete v tématu [Postupy: vytvoření testu a testování částí řízených daty](../test/how-to-create-a-data-driven-unit-test.md) [: použití konfiguračního souboru k definování zdroje dat](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atributy používané k vytvoření pořadí volání
 Prvek kódu upravený jedním z následujících atributů je volán v okamžiku, kdy zadáte. Další informace naleznete v tématu [anatomie testu jednotek](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Pro sestavení
 Atributem AssemblyInitialize a atributem AssemblyCleanup jsou volány hned po načtení sestavení a napravo před uvolněním sestavení.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>Pro třídy
 ClassInitialize a ClassCleanup jsou volány hned po načtení třídy a správné před uvolněním třídy.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>Pro testovací metody

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atributy používané k identifikaci testovacích tříd a metod
 Každá testovací třída musí mít atribut TestClass a každá testovací metoda musí mít atribut TestMethod. Další informace naleznete v tématu [anatomie testu jednotek](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Vyhodnocení tříd a souvisejících výjimek
 Testy jednotek mohou ověřit konkrétní chování aplikace podle jejich použití různými druhy příkazů, výjimek a atributů příkazu Assert. Další informace najdete v tématu [použití tříd Assert](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Třída TestContext
 Následující atributy a hodnoty, které jsou přiřazeny, se zobrazí v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno Vlastnosti pro konkrétní testovací metodu. Tyto atributy nejsou určeny pro použití v kódu testu jednotek. Místo toho mají vliv na způsob použití nebo spuštění testu jednotky, a to buď prostřednictvím integrovaného vývojového prostředí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (IDE), nebo pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] testovacího stroje. Například některé z těchto atributů se zobrazí jako sloupce v okně Test Manager a v Výsledky testů okně, což znamená, že je můžete použít k seskupení a seřazení testů a výsledků testů. Jeden z takových atributů je TestPropertyAttribute, který použijete k přidání libovolných metadat k jednotkovým testům. Můžete ji například použít k uložení názvu testu průchodu, který tento test pokrývá, označením testu jednotky pomocí `[TestProperty("TestPass", "Accessibility")]` . Nebo ho můžete použít k uložení indikátoru typu testu, který je: `[TestProperty("TestKind", "Localization")]` . Vlastnost, kterou vytvoříte pomocí tohoto atributu, a hodnota vlastnosti, kterou přiřadíte, se zobrazí v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno Vlastnosti pod položkou **test**pro daný nadpis.

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

## <a name="attributes-used-for-generating-reports"></a>Atributy používané pro generování sestav
 Atributy v této části se vztahují na testovací metodu, kterou upraví na entity v projektové hierarchii [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] týmového projektu.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Třídy používané s privátními přistupujícími objekty
 Jak je popsáno v tématu [použití Publicize k vytvoření privátního přístupového objektu](https://msdn.microsoft.com/2056c6a7-6672-42a7-8f53-fead33c56deb), můžete vygenerovat test jednotky pro soukromou metodu. Tato generace vytvoří třídu soukromého přístupového objektu, která vytvoří instanci objektu třídy PrivateObject. Třída PrivateObject je Obálková třída, která používá reflexi v rámci procesu privátního přístupového objektu. Třída PrivateType je podobná, ale používá se pro volání privátních statických metod namísto volání metod soukromé instance.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>