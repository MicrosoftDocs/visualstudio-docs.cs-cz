---
title: Ověřování kódu pomocí diagramů závislostí
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759699"
---
# <a name="validate-code-with-dependency-diagrams"></a>Ověřování kódu pomocí diagramů závislostí

## <a name="why-use-dependency-diagrams"></a>Proč používat diagramy závislostí?

Chcete-li se ujistit, že kód není v konfliktu s jeho návrhem, ověřte kód pomocí diagramů závislostí v sadě Visual Studio. To může pomoci při:

- Najít konflikty mezi závislostmi v kódu a závislosti na diagramu závislostí.

- Vyhledání závislostí, které mohou být ovlivněny navrhovanými změnami.

   Můžete například upravit diagram závislostí a zobrazit potenciální změny architektury a potom ověřit kód, abyste viděli ovlivněné závislosti.

- Refaktorujte nebo přeneste kód do jiného návrhu.

   Vyhledejte kód nebo závislosti, které vyžadují práci při přenesení kódu do jiné architektury.

**Požadavky**

- Visual Studio

  Chcete-li vytvořit diagram závislostí pro projekt .NET Core, musíte mít Visual Studio 2019 verze 16.2 nebo novější.

- Řešení, které má projekt modelování s diagramzávislostí. Tento diagram závislostí musí být propojen s artefakty v jazyce C# nebo v projektech jazyka Visual Basic, které chcete ověřit. Viz [Vytvoření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md).

Informace o tom, které edice sady Visual Studio tuto funkci podporují, naleznete [v tématu Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Kód můžete ověřit ručně z otevřeného diagramu závislostí v sadě Visual Studio nebo z příkazového řádku. Můžete také ověřit kód automaticky při spuštění místní sestavení nebo sestavení Azure Pipelines. Viz [Channel 9 Video: Návrh a ověření architektury pomocí diagramů závislostí](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Pokud chcete spustit ověření vrstvy pomocí Team Foundation Server (TFS), musíte také nainstalovat stejnou verzi sady Visual Studio na serveru sestavení.

## <a name="live-dependency-validation"></a>Ověření živé závislosti

K ověření závislostí dochází v reálném čase a chyby jsou okamžitě zobrazeny v **seznamu chyb**.

* Živé ověření je podporováno pro c# a visual basic.

* Chcete-li povolit úplnou analýzu řešení při použití ověřování závislostí za provozu, otevřete nastavení možností ze zlatého pruhu, který se zobrazí v **seznamu chyb**.

  - Můžete trvale zavřít zlatou lištu, pokud nemáte zájem vidět všechny architektonické problémy ve vašem řešení.
  - Pokud nepovolíte úplnou analýzu řešení, analýza se provádí pouze pro upravované soubory.

* Při inovaci projektů za účelem povolení živého ověření se v dialogovém okně zobrazí průběh převodu.

* Při aktualizaci projektu pro ověření živé závislosti je verze balíčku NuGet upgradována tak, aby byla stejná pro všechny projekty a je nejvyšší verzí, která se používá.

* Přidání nového projektu ověření závislostí spustí aktualizaci projektu.

## <a name="see-if-an-item-supports-validation"></a>Zjištění, zda položka podporuje validaci

Vrstvy můžete propojit s weby, dokumenty Office, soubory ve formátu prostého textu a soubory v projektech, které jsou sdíleny ve více aplikacích, ale proces ověřování je nezahrnuje. Chyby ověřování se neobjeví pro odkazy na projekty nebo sestavení, které jsou připojeny k samostatným vrstvám a v případě, že se mezi těmito vrstvami neobjeví závislosti. Tyto odkazy jsou považovány za závislosti jen tehdy, pokud kód tyto odkazy používá.

1. V diagramu závislostí vyberte jednu nebo více vrstev, klikněte pravým tlačítkem myši na výběr a potom klikněte na **Zobrazit odkazy**.

2. V **Průzkumníku vrstev**se podívejte na sloupec **Podporuje ověřování.** Pokud je hodnota false, položka ověřování nepodporuje.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Zahrnutí dalších projektů a sestavení .NET pro ověřování

Při přetahování položek do diagramu závislostí jsou odkazy na odpovídající sestavení nebo projekty rozhraní .NET automaticky přidány do složky **Odkazy na vrstvy** v projektu modelování. Tato složka obsahuje odkazy na sestavení a projekty, které jsou analyzovány během ověřování. Můžete zahrnout další sestavení .NET a projekty pro ověření bez ručního přetažení do diagramu závislostí.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt modelování nebo na složku **Odkazy na vrstvy** a potom klepněte na příkaz **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** vyberte sestavení nebo projekty a klepněte na tlačítko **OK**.

## <a name="validate-code-manually"></a>Ověřování kódu ručně

Pokud máte otevřený diagram závislostí, který je propojen s položkami řešení, můžete spustit příkaz **Ověřit** zástupce z diagramu. Příkazový řádek můžete také použít ke spuštění příkazu **msbuild** s vlastní vlastností **/p:ValidateArchitecture** nastavenou na **hodnotu True**. Například lze při provádění změn v kódu provádět pravidelně ověřování vrstvy, takže bude možné zachytit konflikty závislostí včas.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Ověření kódu z otevřeného diagramu závislostí

1. Klepněte pravým tlačítkem myši na povrch diagramu a potom klepněte na příkaz **Ověřit architekturu**.

    > [!NOTE]
    > Ve výchozím nastavení je vlastnost **Akce sestavení** v souboru diagramu závislostí (.layerdiagram) nastavena na **ověřit** tak, aby byl diagram zahrnut do procesu ověřování.

     Okno **Seznam chyb** hlásí všechny chyby, ke kterým dojde. Další informace o chybách ověření naleznete [v tématu Poradce při potížích s ověřením vrstvy](#troubleshoot-layer-validation-issues).

2. Chcete-li zobrazit zdroj každé chyby, poklepejte na chybu v okně **Seznam chyb.**

    > [!NOTE]
    > Visual Studio může zobrazit mapu kódu namísto zdroje chyby. K tomu dochází, pokud má kód závislost na sestavení, které není určeno diagramem závislostí, nebo kód chybí závislost, která je určena diagramem závislostí. Zkontrolujte mapování kódu nebo kód k určení, zda by měla existovat závislost. Další informace o mapách kódu naleznete v tématu [Mapové závislosti napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md).

3. Informace o správě chyb naleznete [v tématu Řešení chyb ověření vrstvy](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Ověření kódu na příkazovém řádku

1. Otevřete příkazový řádek sady Visual Studio.

2. Vyberte jednu z následujících možností:

   - Chcete-li ověřit kód proti konkrétní modelovací projekt v řešení, spusťte MSBuild s následující vlastní vlastnost.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - nebo -

       Přejděte do složky, která obsahuje soubor projektu modelování (.modelproj) a diagramzávislosta a spusťte MSBuild s následující vlastní vlastností:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Chcete-li ověřit kód proti všem projektům modelování v řešení, spusťte MSBuild s následující vlastní vlastností:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - nebo -

       Přejděte do složky řešení, která musí obsahovat projekt modelování, který obsahuje diagram závislostí, a spusťte msbuild s následující vlastní vlastností:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Zobrazí se všechny chyby, ke kterým dochází. Další informace o msbuildu naleznete v tématu [MSBuild](../msbuild/msbuild.md) a [MSBuild Task](../msbuild/msbuild-task.md).

   Další informace o chybách ověření naleznete [v tématu Poradce při potížích s ověřením vrstvy](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Správa chyb ověřování

Během procesu vývoje můžete chtít potlačit některé vykázané konflikty během ověřování. Například můžete chtít potlačit chyby, které již řešíte nebo které nejsou relevantní k danému scénáři. Při potlačení chyby, je vhodné protokolovat pracovní položku v Team Foundation.

> [!WARNING]
> Chcete-li vytvořit nebo propojit pracovní položku, musíte již být připojeni ke složce zdrojového kódu TFS (SCC). Pokud se pokusíte otevřít připojení k jinému TFS SCC, Visual Studio zavře aktuální řešení automaticky. Ujistěte se, že jste již připojeni k příslušné SCC před pokusem o vytvoření nebo propojení s pracovní položkou. V novějších verzích sady Visual Studio nejsou příkazy nabídky k dispozici, pokud nejste připojeni k SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Vytvoření pracovní položky pro chybu ověření

- V okně **Seznam chyb** klepněte pravým tlačítkem myši na chybu, přejděte na příkaz Vytvořit **pracovní položku**a potom klepněte na typ pracovní položky, kterou chcete vytvořit.

Tyto úkoly slouží ke správě chyb ověření v okně **Seznam chyb:**

|**Akce**|**Postupujte**|
|-|-|
|Potlačení vybraných chyb během ověřování|Klepněte pravým tlačítkem myši na jednu nebo více vybraných chyb, přejděte na **položku Správa chyb ověření**a potom klepněte na příkaz **Potlačit chyby**.<br /><br /> Potlačené chyby se zobrazují s přeškrtnutím. Při příštím spuštění ověřování se tyto chyby nezobrazí.<br /><br /> Potlačené chyby jsou sledovány v souboru .suppressions pro odpovídající soubor diagramu závislostí.|
|Ukončení potlačování vybraných chyb|Klepněte pravým tlačítkem myši na vybranou potlačenou chybu nebo chyby, přejděte na **položku Správa chyb ověření**a potom klepněte na příkaz **Zastavit potlačení chyb**.<br /><br /> Vybrané potlačené chyby se při příštím spuštění ověřování zobrazí.|
|Obnovit všechny potlačené chyby v okně **Seznam chyb**|Klepněte pravým tlačítkem myši na libovolné místo v okně **Seznam chyb,** přejděte na **položku Správa chyb ověření**a potom klepněte na příkaz Zobrazit všechny **potlačené chyby**.|
|Skrýt všechny potlačené chyby z okna **Seznam chyb**|Klepněte pravým tlačítkem myši na libovolné místo v okně **Seznam chyb,** přejděte na **položku Správa chyb ověření**a potom klepněte na příkaz Skrýt všechny **potlačené chyby**.|

## <a name="validate-code-automatically"></a>Ověřování kódu automaticky

Ověřování vrstev lze provádět při každém spuštění místního sestavení. Pokud váš tým používá Azure DevOps, můžete provést ověření vrstvy s gated vrácení se změnami, které můžete zadat vytvořením vlastní úlohy MSBuild a použít sestavy sestavení ke shromažďování chyb ověření. Chcete-li vytvořit sestavení s bránou vrácení se změnami, přečtěte si informace o [vrácení se změnami tfvc](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Automatické ověřování kódu během místního sestavení

K otevření souboru projektu modelování (.modelproj) použijte textový editor a následně vložte následující vlastnost:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\-nebo -

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt modelování, který obsahuje diagram závislostí nebo diagramy, a potom klepněte na příkaz **Vlastnosti**.

2. V okně **Vlastnosti** nastavte vlastnost **Ověřit architekturu** projektu modelování na **hodnotu True**.

    To zahrne projekt modelování do ověřovacího procesu.

3. V **Průzkumníku řešení**klepněte na soubor diagramu závislostí (.layerdiagram), který chcete použít pro ověření.

4. V okně **Vlastnosti** se ujistěte, že vlastnost **Akce sestavení** diagramu je nastavena na **ověřit**.

    To zahrnuje diagram závislostí v procesu ověřování.

Informace o správě chyb v okně Seznam chyb naleznete v [tématu Řešení chyb ověření vrstvy](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Poradce při potížích s ověřením vrstvy

Následující tabulka popisuje problémy s ověřením vrstvy a jejich řešení. Tyto problémy se liší od chyb, které vzniknou z konfliktů mezi kódem a návrhem. Další informace o těchto chybách naleznete [v tématu Poradce při potížích s ověřením vrstvy](#troubleshoot-layer-validation-issues).

|**Problém**|**Možná příčina**|**Rozlišení**|
|-|-|-|
|Chyby ověřování se nezobrazí podle očekávání.|Ověření nefunguje na diagramy závislostí, které jsou zkopírovány z jiných diagramů závislostí v Průzkumníku řešení a které jsou ve stejném projektu modelování. Diagramy závislostí, které jsou kopírovány tímto způsobem, obsahují stejné odkazy jako původní diagram závislostí.|Přidejte nový diagram závislostí do projektu modelování.<br /><br /> Zkopírujte prvky z diagramu zdrojové závislosti do nového diagramu.|

## <a name="resolve-layer-validation-errors"></a>Řešení chyb ověření vrstvy

Při ověření kódu proti diagramu závislostí dojde k chybám ověření, když je kód v konfliktu s návrhem. Chyby ověřování mohou způsobit například následující podmínky:

- Artefakt je přiřazen nesprávné vrstvě. V tomto případě přesuňte artefakt.

- Artefakt, jako je například třída, používá jiné třídy způsobem, který je v konfliktu s architekturou. V tomto případě refaktorujte kód a odeberte závislost.

Chcete-li tyto chyby odstranit, aktualizujte kód, dokud se během ověřování neobjeví žádné chyby. Tuto úlohu lze provést iteračním způsobem.

Následující oddíl popisuje syntaxi, která se u těchto chyb používá, vysvětluje význam těchto chyb a navrhne, jak je vyřešit nebo spravovat.

|**Syntaxe**|**Popis**|
|-|-|
|*ArtefaktN**(ArtifactTypeN*)|*ArtifactN* je artefakt, který je spojen s vrstvou v diagramu závislostí.<br /><br /> *ArtifactTypeN* je typ *ArtifactN*, například **Class** nebo **Method**, například:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*Název_oboru namen*|Název oboru názvů.|
|*Název_vrstvyN*|Název vrstvy v diagramu závislostí.|
|*Typ závislosti*|Typ vztahu závislosti mezi *Artifact1* a *Artifact2*. Například *Artifact1* má **vztah volání** s *Artifact2*.|

| **Syntaxe chyby** | **Popis chyby** |
|-|-|
| DV0001: **Neplatná závislost** | Tento problém je hlášena, když prvek kódu (obor názvů, typ, člen) mapována vrstva odkazuje na prvek kódu mapované na jinou vrstvu, ale neexistuje žádná šipka závislostmezi těmito vrstvami v diagramu ověřování závislostí obsahující tyto vrstvy. Toto je porušení omezení závislosti. |
| DV1001: **Neplatný název oboru názvů** | Tento problém je hlášen na prvek kódu přidružené k vrstvě, která "Povolené názvy jmen" vlastnost neobsahuje obor názvů, ve kterém je definován tento prvek kódu. Toto je porušení omezení pojmenování. Všimněte si, že syntaxe "Povolené názvy jmenných oborů" má být středník seznam jmenné prostory, ve kterých jsou definovány prvky kódu spojené s vrstvy. |
| DV1002: **Závislost na neodkazovatelném oboru názvů** | Tento problém je hlášen na prvek kódu přidružené k vrstvě a odkazování na jiný prvek kódu definované v oboru názvů, který je definován v "Neodkazovatelný obor názvů" vlastnost vrstvy. Toto je porušení omezení pojmenování. Všimněte si, že vlastnost "Neodkazovatelné obory názvů" je definována jako seznam jmenovcích oddělený chodnících, na který by se nemělo odkazovat v prvcích kódu přidružených k této vrstvě. |
| DV1003: **Nepovolený název oboru názvů** | Tento problém je hlášen na prvek kódu přidružené k vrstvě, která "Nepovolené názvy jmen" vlastnost obsahuje obor názvů, ve kterém je definován tento prvek kódu. Toto je porušení omezení pojmenování. Všimněte si, že vlastnost "Název oboru názvů zakázáno" je definována jako seznam jmenovky oddělenými středníkem, ve kterém by neměly být definovány prvky kódu přidružené k této vrstvě. |
| DV2001: **Přítomnost diagramu vrstvy** | Tento problém je hlášena na projektu, který neobsahuje soubor diagramu závislostí, ale odkazuje na analyzátory ověření závislostí. Pokud ověření závislostí nebyl použit, můžete odebrat "Microsoft.DependencyValidation.Analyzers" přímo z Průzkumníka řešení nebo potlačit toto upozornění. Informace o přidání diagramu závislostí naleznete v tématu [Vytvoření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002: **Nenamapované typy Base** | Tento problém je hlášena při prvek kódu není mapována na žádnou vrstvu. |
| DV3001: **Chybějící článek** | Vrstva _*Název_vrstvy*' odkazuje na '*Artefakt*', který nebyl nalezen. Nechybí odkaz na sestavení? |
| DV9001: **Architektonická analýza zjistila interní chyby** | Výsledky nemusí být úplné. Další informace lze nalézt v podrobném protokolu událostí sestavení nebo ve výstupním okně. |

## <a name="see-also"></a>Viz také

- [Ověření živé závislosti ve Visual Studiu](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)
- [Video: Ověření závislostí architektury v reálném čase](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
