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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80759699"
---
# <a name="validate-code-with-dependency-diagrams"></a>Ověřování kódu pomocí diagramů závislostí

## <a name="why-use-dependency-diagrams"></a>Proč používat diagramy závislostí?

Chcete-li zajistit, aby kód nekoliduje s jeho návrhem, ověřte kód pomocí diagramů závislostí v aplikaci Visual Studio. To může pomoci při:

- Vyhledá konflikty mezi závislostmi v kódu a závislostmi na diagramu závislostí.

- Vyhledání závislostí, které mohou být ovlivněny navrhovanými změnami.

   Diagram závislosti můžete například upravit tak, aby zobrazoval možné změny architektury, a pak ověřit kód, aby se zobrazily ovlivněné závislosti.

- Refaktorujte nebo přeneste kód do jiného návrhu.

   Vyhledejte kód nebo závislosti, které vyžadují práci při přenesení kódu do jiné architektury.

**Požadavky**

- Visual Studio

  Chcete-li vytvořit diagram závislostí pro projekt .NET Core, musíte mít Visual Studio 2019 verze 16,2 nebo novější.

- Řešení, které má projekt modelování s diagramem závislostí. Tento diagram závislostí musí být spojen s artefakty v jazyce C# nebo Visual Basic projektů, které chcete ověřit. Viz [vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md).

Pokud chcete zjistit, které edice sady Visual Studio podporují tuto funkci, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Kód lze ověřit ručně z otevřeného diagramu závislostí v aplikaci Visual Studio nebo z příkazového řádku. Kód lze také automaticky ověřit při spuštění místních sestavení nebo sestavení Azure Pipelines. Podívejte [se na video pro kanál 9: návrh a ověření architektury pomocí diagramů závislostí](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Pokud chcete spustit ověřování vrstvy pomocí Team Foundation Server (TFS), musíte na server sestavení také nainstalovat stejnou verzi sady Visual Studio.

## <a name="live-dependency-validation"></a>Ověřování závislostí v reálném čase

Ověřování závislostí probíhá v reálném čase a chyby jsou zobrazeny ihned v **Seznam chyb**.

* Pro C# a Visual Basic se podporuje živé ověřování.

* Pokud chcete při ověřování závislosti v reálném čase povolit úplnou analýzu řešení, otevřete nastavení možností z zlatého panelu, který se zobrazí v **Seznam chyb**.

  - Zlatý panel můžete trvale zavřít, pokud vás zajímá všechny problémy architektury vašeho řešení.
  - Pokud nepovolíte úplnou analýzu řešení, provede se analýza pouze u upravovaných souborů.

* Při upgradu projektů pro povolení živého ověřování se v dialogu zobrazuje průběh převodu.

* Při aktualizaci projektu pro ověření závislosti na živé závislosti je verze balíčku NuGet upgradována tak, aby byla stejná pro všechny projekty, a je nejvyšší použitá verze.

* Přidáním nového projektu ověření závislosti se aktivuje aktualizace projektu.

## <a name="see-if-an-item-supports-validation"></a>Zjištění, zda položka podporuje validaci

Vrstvy můžete v projektech, které jsou sdíleny napříč více aplikacemi, propojit s weby, dokumenty Office, soubory ve formátu prostého textu a soubory, ale proces ověření je nebude zahrnovat. Chyby ověřování se neobjeví pro odkazy na projekty nebo sestavení, které jsou připojeny k samostatným vrstvám a v případě, že se mezi těmito vrstvami neobjeví závislosti. Tyto odkazy jsou považovány za závislosti jen tehdy, pokud kód tyto odkazy používá.

1. V diagramu závislosti vyberte jednu nebo více vrstev, klikněte pravým tlačítkem myši na výběr a potom klikněte na možnost **Zobrazit odkazy**.

2. V **Průzkumníku vrstev**se podívejte do sloupce **podporuje ověřování** . Pokud je hodnota false, položka ověřování nepodporuje.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Zahrnutí dalších projektů a sestavení .NET pro ověřování

Při přetahování položek do diagramu závislostí se automaticky přidají odkazy na odpovídající sestavení nebo projekty .NET do složky **odkazy na vrstvy** v projektu modelování. Tato složka obsahuje odkazy na sestavení a projekty, které jsou analyzovány během ověřování. Můžete zahrnout další sestavení a projekty .NET pro ověřování, aniž byste je museli ručně přetahovat do diagramu závislostí.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt modelování nebo na složku **odkazy na vrstvu** a potom klikněte na tlačítko **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** vyberte sestavení nebo projekty a potom klikněte na tlačítko **OK**.

## <a name="validate-code-manually"></a>Ověřování kódu ručně

Pokud máte otevřený Diagram závislostí, který je propojen s položkami řešení, můžete spustit příkaz **ověřit** zástupce z diagramu. Pomocí příkazového řádku můžete také spustit příkaz **MSBuild** s vlastní vlastností **/p: ValidateArchitecture** nastavenou na **hodnotu true**. Například lze při provádění změn v kódu provádět pravidelně ověřování vrstvy, takže bude možné zachytit konflikty závislostí včas.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Ověření kódu z otevřeného diagramu závislostí

1. Klikněte pravým tlačítkem na plochu diagramu a potom klikněte na **ověřit architekturu**.

    > [!NOTE]
    > Ve výchozím nastavení je vlastnost **Akce sestavení** v souboru diagramu závislosti (. layerdiagram) nastavena na hodnotu **ověřit** , aby byl diagram součástí procesu ověřování.

     Okno **Seznam chyb** nahlásí všechny chyby, ke kterým dojde. Další informace o chybách ověřování najdete v tématu [řešení potíží s ověřováním vrstev](#troubleshoot-layer-validation-issues).

2. Chcete-li zobrazit zdroj každé chyby, dvakrát klikněte na chybu v okně **Seznam chyb** .

    > [!NOTE]
    > Visual Studio může namísto zdroje chyby zobrazit mapu kódu. K tomu dochází, když má kód závislost na sestavení, které není zadáno v diagramu závislosti, nebo v kódu chybí závislost, která je určena diagramem závislostí. Zkontrolujte mapu kódu nebo kód, abyste zjistili, zda by měla závislost existovat. Další informace o mapách kódu najdete v tématu [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md).

3. Chcete-li spravovat chyby, přečtěte si téma [řešení chyb ověřování vrstvy](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Ověřit kód na příkazovém řádku

1. Otevřete příkazový řádek sady Visual Studio.

2. Vyberte jednu z následujících možností:

   - Pro ověření kódu proti konkrétnímu projektu modelování v řešení spusťte nástroj MSBuild s následující vlastní vlastností.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - ani

       Přejděte do složky, která obsahuje soubor projektu modelování (. modelproj) a diagram závislosti, a poté spusťte nástroj MSBuild s následující vlastní vlastností:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Chcete-li ověřit kód pro všechny projekty modelování v řešení, spusťte MSBuild s následující vlastní vlastností:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - ani

       Přejděte do složky řešení, která musí obsahovat projekt modelování, který obsahuje diagram závislosti, a poté spusťte nástroj MSBuild s následující vlastní vlastností:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Zobrazí se všechny chyby, ke kterým dochází. Další informace o nástroji MSBuild naleznete v tématu úloha [MSBuild](../msbuild/msbuild.md) a [MSBuild](../msbuild/msbuild-task.md).

   Další informace o chybách ověřování najdete v tématu [řešení potíží s ověřováním vrstev](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Správa chyb ověřování

Během procesu vývoje můžete chtít potlačit některé vykázané konflikty během ověřování. Například můžete chtít potlačit chyby, které již řešíte nebo které nejsou relevantní k danému scénáři. Pokud potlačíte chybu, je vhodné Protokolovat pracovní položku v Team Foundation.

> [!WARNING]
> Aby bylo možné vytvořit nebo propojit pracovní položku, musíte být již připojeni ke správě zdrojového kódu TFS (SCC). Pokud se pokusíte otevřít připojení k jinému SCC TFS, Visual Studio automaticky zavře aktuální řešení. Před pokusem o vytvoření nebo propojení pracovní položky se ujistěte, že jste již připojeni k odpovídajícímu SCC. V novějších verzích sady Visual Studio nejsou příkazy nabídky k dispozici, pokud nejste připojeni k SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Vytvoření pracovní položky pro chybu ověření

- V okně **Seznam chyb** klikněte pravým tlačítkem myši na chybu, přejděte na příkaz **vytvořit pracovní položku**a poté klikněte na typ pracovní položky, kterou chcete vytvořit.

Pomocí těchto úloh můžete spravovat chyby ověřování v okně **Seznam chyb** :

|**Záměr**|**Postupujte podle těchto kroků**|
|-|-|
|Potlačení vybraných chyb během ověřování|Klikněte pravým tlačítkem myši na jednu nebo více vybraných chyb, přejděte na položku **Spravovat chyby ověřování**a potom klikněte na **potlačit chyby**.<br /><br /> Potlačené chyby se zobrazují s přeškrtnutím. Při příštím spuštění ověřování se tyto chyby nezobrazí.<br /><br /> Potlačené chyby jsou sledovány v souboru. potlačení pro odpovídající soubor diagramu závislosti.|
|Ukončení potlačování vybraných chyb|Klikněte pravým tlačítkem myši na potlačit chybu nebo chyby, přejděte na položku **Spravovat chyby ověřování**a potom klikněte na možnost **ukončit potlačení chyb**.<br /><br /> Vybrané potlačené chyby se při příštím spuštění ověřování zobrazí.|
|Obnovit všechny Potlačené chyby v okně **Seznam chyb**|Klikněte pravým tlačítkem myši kdekoli v okně **Seznam chyb** , přejděte na položku **Spravovat chyby ověřování**a potom klikněte na možnost **Zobrazit všechny Potlačené chyby**.|
|Skrýt všechny Potlačené chyby z okna **Seznam chyb**|Klikněte pravým tlačítkem myši kdekoli v okně **Seznam chyb** , přejděte na možnost **Spravovat chyby ověřování**a potom klikněte na **Skrýt všechny Potlačené chyby**.|

## <a name="validate-code-automatically"></a>Ověřování kódu automaticky

Ověřování vrstev lze provádět při každém spuštění místního sestavení. Pokud váš tým používá Azure DevOps, můžete provést ověřování vrstvy pomocí ověřovaných vrácení se změnami, které lze zadat vytvořením vlastní úlohy MSBuild, a pomocí sestav sestavení shromažďovat chyby ověřování. Chcete-li vytvořit ověřovaná sestavení pro vrácení se změnami, přečtěte si téma [TFVC gated check-in](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Automatické ověřování kódu během místního sestavení

K otevření souboru projektu modelování (.modelproj) použijte textový editor a následně vložte následující vlastnost:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- ani

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt modelování, který obsahuje diagram nebo diagramy závislosti, a poté klikněte na možnost **vlastnosti**.

2. V okně **vlastnosti** nastavte vlastnost **ověřit architekturu** projektu modelování na **hodnotu true**.

    To zahrne projekt modelování do ověřovacího procesu.

3. V **Průzkumník řešení**klikněte na soubor diagramu závislosti (. layerdiagram), který chcete použít k ověření.

4. V okně **vlastnosti** se ujistěte, že je vlastnost **Akce sestavení** diagramu nastavena na hodnotu **ověřit**.

    To zahrnuje diagram závislosti v procesu ověřování.

Chcete-li spravovat chyby v okně Seznam chyb, přečtěte si téma [řešení chyb ověřování vrstvy](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Poradce při potížích s ověřením vrstvy

Následující tabulka popisuje problémy s ověřením vrstvy a jejich řešení. Tyto problémy se liší od chyb, které vzniknou z konfliktů mezi kódem a návrhem. Další informace o těchto chybách najdete v tématu [řešení potíží s ověřováním vrstev](#troubleshoot-layer-validation-issues).

|**Problém**|**Možná příčina**|**Řešení**|
|-|-|-|
|Chyby ověřování se nezobrazí podle očekávání.|Ověřování nefunguje na diagramech závislostí, které se zkopírují z jiných diagramů závislostí v Průzkumník řešení a které jsou ve stejném projektu modelování. diagramy závislostí, které jsou tímto způsobem zkopírovány, obsahují stejné odkazy jako původní Diagram závislostí.|Přidejte do projektu modelování nový diagram závislosti.<br /><br /> Zkopírujte prvky z diagramu závislosti zdrojového kódu do nového diagramu.|

## <a name="resolve-layer-validation-errors"></a>Vyřešit chyby ověřování vrstvy

Při ověřování kódu proti diagramu závislostí dojde k chybám ověřování, když je kód v konfliktu s návrhem. Chyby ověřování mohou způsobit například následující podmínky:

- Artefakt je přiřazen nesprávné vrstvě. V tomto případě přesuňte artefakt.

- Artefakt, jako je například třída, používá jiné třídy způsobem, který je v konfliktu s architekturou. V tomto případě refaktorujte kód a odeberte závislost.

Chcete-li tyto chyby odstranit, aktualizujte kód, dokud se během ověřování neobjeví žádné chyby. Tuto úlohu lze provést iteračním způsobem.

Následující oddíl popisuje syntaxi, která se u těchto chyb používá, vysvětluje význam těchto chyb a navrhne, jak je vyřešit nebo spravovat.

|**Syntax**|**Popis**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* je artefakt, který je spojen s vrstvou v diagramu závislostí.<br /><br /> *ArtifactTypeN* je typ *ArtifactN*, například **Třída** nebo **Metoda**, například:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Název oboru názvů.|
|*LayerNameN*|Název vrstvy v diagramu závislostí.|
|*DependencyType*|Typ vztahu závislostí mezi *artefakt Artifact1* a *Artifact2*. Například *artefakt Artifact1* má relaci **volání** s *Artifact2*.|

| **Chyba syntaxe** | **Popis chyby** |
|-|-|
| DV0001: **neplatná závislost** | K tomuto problému dochází, pokud prvek kódu (obor názvů, typ, člen) mapovaný na vrstvu odkazuje na prvek kódu mapovaný na jinou vrstvu, ale mezi těmito vrstvami není žádná šipka závislosti v diagramu ověřování závislostí obsahující tuto vrstvu. Toto je narušení omezení závislosti. |
| DV1001: **neplatný název oboru názvů** | Tento problém je hlášen u elementu kódu přidruženého k vrstvě, která "povolené názvy oborů názvů" neobsahuje obor názvů, ve kterém je tento prvek kódu definován. Toto je porušení omezení pojmenování. Všimněte si, že syntaxe "povolených názvů oborů názvů" je středníkem seznam oborů názvů, ve kterých je povoleno definovat prvky kódu přidružené ke vrstvě. |
| DV1002: **závislost na neodkazovaném oboru názvů** | Tento problém je hlášen u prvku kódu přidruženého k vrstvě a odkazování na jiný prvek kódu definovaný v oboru názvů, který je definován v vlastnosti "neodkazovaná" názvový prostor vrstvy. Toto je porušení omezení pojmenování. Všimněte si, že vlastnost "neodkazované obory názvů" je definována jako středníkem oddělený seznam oborů názvů, na které by neměly být odkazovány v prvcích kódu přidružených k této vrstvě. |
| DV1003: **nepovolený název oboru názvů** | Tento problém je hlášen u elementu kódu přidruženého ke vrstvě, která "nepovolené názvy oborů názvů" obsahuje obor názvů, ve kterém je tento prvek kódu definován. Toto je porušení omezení pojmenování. Všimněte si, že vlastnost "nepovolený název oboru názvů" je definována jako středníkem oddělený seznam oborů názvů, ve kterých by neměly být definovány elementy kódu přidružené k této vrstvě. |
| DV2001: **přítomnost diagramu vrstvy** | Tento problém se oznamuje v projektu, který neobsahuje soubor s diagramem závislostí, ale odkazuje na analyzátory ověřování závislostí. Pokud nebylo použito ověřování závislostí, můžete odebrat "Microsoft. DependencyValidation. Analyzers" přímo z Průzkumník řešení nebo potlačit toto upozornění. Chcete-li přidat Diagram závislostí, přečtěte si téma [vytvoření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002: **nemapované typy Base** | Tento problém je hlášen, když prvek kódu není namapován na žádnou vrstvu. |
| DV3001: **chybějící odkaz** | Vrstva "*propojuje" odkazuje*na*artefakt*, který nebyl nalezen. Nechybí odkaz na sestavení? |
| DV9001: **Analýza architektury zjistila vnitřní chyby** . | Výsledky nemusí být úplné. Další informace lze nalézt v podrobném protokolu událostí sestavení nebo ve výstupním okně. |

## <a name="see-also"></a>Viz také

- [Ověřování aktivní závislosti v aplikaci Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)
- [Video: ověření závislostí architektury v reálném čase](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
