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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 71eebd95db1a616d4f86866ef60fb32251634cc0
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967282"
---
# <a name="validate-code-with-dependency-diagrams"></a>Ověřování kódu pomocí diagramů závislostí

## <a name="why-use-dependency-diagrams"></a>Proč používat diagramů závislostí?

Pokud chcete mít jistotu, že kód není v konfliktu s návrhem, ověřování kódu pomocí diagramů závislostí v sadě Visual Studio. To může pomoci při:

- Vyhledání konfliktů mezi závislostmi v kódu a závislostmi na diagram závislostí.

- Vyhledání závislostí, které mohou být ovlivněny navrhovanými změnami.

   Například lze upravit diagram závislostí k zobrazení možných změn architektury a následně ověřit kód pro vyhledání ovlivněných závislostí.

- Refaktorujte nebo přeneste kód do jiného návrhu.

   Vyhledejte kód nebo závislosti, které vyžadují práci při přenesení kódu do jiné architektury.

**Požadavky**

- Visual Studio

- Řešení, které má projekt modelování s diagramem závislostí. Tento diagram závislostí musí být spojen s artefakty v projektech C# nebo Visual Basic, které chcete ověřit. Zobrazit [vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md).

> [!NOTE]
> Diagramy závislostí nejsou podporovány pro projekty .NET Core v sadě Visual Studio 2017.

Chcete-li zjistit, jaké edice sady Visual Studio podporují tuto funkci, přečtěte si téma [podpora edice nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Můžete ověřit kód ručně z diagramu otevřete závislostí v sadě Visual Studio nebo z příkazového řádku. Rovněž je možné ověřit kód automaticky při spuštění místních sestavení nebo kanály Azure sestavení. Zobrazit [Video pro kanál 9: návrh a ověření architektury pomocí diagramů závislostí](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Pokud chcete spustit ověření vrstvy pomocí Team Foundation Server (TFS), je rovněž nutné nainstalovat stejnou verzi sady Visual Studio na svém serveru sestavení.

## <a name="live-dependency-validation"></a>Ověřování závislostí v reálném čase

Nastane, ověřování závislostí v reálném čase a zobrazují se chyby okamžitě v **seznam chyb**.

* Živé ověření je podporováno pro C# a Visual Basic.

* K povolení úplné analýzy řešení při použití ověřování závislostí v reálném čase, otevřete nastavení možností z zlatý pruh, který se zobrazí **seznam chyb**.

   - Zlatý pruh můžete trvale zavřít, pokud si nejste nepotřebujete vidět všechny architektury problémy ve vašem řešení.
   - Pokud nepovolíte úplné analýzy řešení, analýze se provádí pouze u souborů, který právě upravujete.

* Při upgradu projekty Povolit živé ověření, zobrazí dialogové okno průběhu převodu.

* Při aktualizaci projektu ověřování závislostí v reálném čase, verze balíčku NuGet se upgraduje na stejné pro všechny projekty a je nejvyšší verze používá.

* Přidání nových triggerů projektu ověřování závislostí projektu aktualizace.

## <a name="see-if-an-item-supports-validation"></a>Zjištění, zda položka podporuje validaci

Vrstvy můžete propojit s weby, dokumenty Office, místo textových souborů a soubory v projektech, které jsou sdíleny napříč více aplikacemi, ale proces ověření nebude zahrnovat je. Chyby ověřování se neobjeví pro odkazy na projekty nebo sestavení, které jsou připojeny k samostatným vrstvám a v případě, že se mezi těmito vrstvami neobjeví závislosti. Tyto odkazy jsou považovány za závislosti jen tehdy, pokud kód tyto odkazy používá.

1.  Na diagram závislostí, vyberte jednu nebo více vrstev, klikněte pravým tlačítkem na svůj výběr a potom klikněte na tlačítko **zobrazit odkazy**.

2.  V **Průzkumník vrstev**, podívejte se na **podporuje ověřování** sloupce. Pokud je hodnota false, položka ověřování nepodporuje.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Zahrnutí dalších projektů a sestavení .NET pro ověřování

Při přetažení položky do diagramu závislost, odkazy odpovídající sestavení nebo projekty .NET přidány automaticky do **odkazy vrstvy** složky v projektu modelování. Tato složka obsahuje odkazy na sestavení a projekty, které jsou analyzovány během ověřování. Můžete zahrnout další sestavení a projekty .NET pro ověření bez ručně přetahovat na diagram závislostí.

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt modelování nebo **odkazy vrstvy** složku a pak klikněte na tlačítko **přidat odkaz**.

2.  V **přidat odkaz** dialogovém okně vyberte projekty nebo sestavení a klikněte na **OK**.

## <a name="validate-code-manually"></a>Ověřování kódu ručně

Pokud máte diagramu otevřete závislostí, který je propojen s položkami řešení, můžete spustit **ověřit** příkaz z diagramu. Můžete také použít příkazový řádek ke spuštění **msbuild** příkazů **validatearchitecture** vlastní vlastnost nastavena na **True**. Například lze při provádění změn v kódu provádět pravidelně ověřování vrstvy, takže bude možné zachytit konflikty závislostí včas.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Ověření kódu z diagramu otevřete závislostí

1.  Klikněte pravým tlačítkem na plochu diagramu a potom klikněte na tlačítko **ověřit architekturu**.

    > [!NOTE]
    > Ve výchozím nastavení **akce sestavení** vlastnost na závislost soubor diagramu (.layerdiagram) nastavena na **ověřit** tak, aby diagram je součástí procesu ověřování.

     **Seznam chyb** okno hlásí chyby, ke kterým dochází. Další informace o chybách ověřování najdete v části [pochopení a vyřešení chyb ověřování vrstev](#UnderstandingValidationErrors).

2.  Chcete-li zobrazit zdroje každé chyby, klikněte dvakrát na chybu v **seznam chyb** okna.

    > [!NOTE]
    > Visual Studio může namísto zdroje chyby zobrazit mapu kódu. K tomu dojde, pokud kód obsahuje závislost na sestavení, které není specifikováno diagram závislostí nebo kód chybí závislost, která je zadána diagram závislostí. Projděte si mapu kódu nebo kód určující, zda by měla závislost existovat. Další informace o mapách kódu najdete v tématu [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md).

3.  Ke správě chyb, naleznete v tématu [spravovat chyby ověřování](#ManageErrors).

### <a name="validate-code-at-the-command-prompt"></a>Ověřování kódu v příkazovém řádku

1. Otevřete příkazový řádek sady Visual Studio.

2. Vyberte jednu z následujících možností:

   - Pro ověření kódu proti konkrétnímu projektu modelování v řešení spusťte nástroj MSBuild s následující vlastní vlastností.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - nebo –

       Přejděte do složky, která obsahuje projekt modelování (.modelproj) souboru a závislost diagramu a pak spusťte nástroj MSBuild s následující vlastní vlastností:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Pro ověření kódu proti všem projektům modelování v řešení spusťte nástroj MSBuild s následující vlastní vlastností:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - nebo –

       Přejděte do složky řešení, která musí obsahovat projekt modelování obsahující diagram závislostí a pak spusťte nástroj MSBuild s následující vlastní vlastností:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Zobrazí se všechny chyby, ke kterým dochází. Další informace o nástroji MSBuild naleznete v tématu [MSBuild](../msbuild/msbuild.md) a [úlohy nástroje MSBuild](../msbuild/msbuild-task.md).

   Další informace o chybách ověřování najdete v části [pochopení a vyřešení chyb ověřování vrstev](#UnderstandingValidationErrors).

### <a name="manage-validation-errors"></a>Správa chyb ověřování

Během procesu vývoje můžete chtít potlačit některé vykázané konflikty během ověřování. Například můžete chtít potlačit chyby, které již řešíte nebo které nejsou relevantní k danému scénáři. Při potlačení chyby je praktikou zaznamenat pracovní položku v Team Foundation.

> [!WARNING]
> Musíte už být připojení k TFS zdrojového kódu ovládacího prvku (SCC) vytvořit nebo propojit s pracovní položkou. Pokud se pokusíte otevřít připojení k jiné SCC TFS, Visual Studio automaticky zavře aktuální řešení. Ujistěte se, že jste již připojeni k příslušné SCC než se pokusíte vytvořit nebo propojit s pracovní položkou. V pozdějších verzích sady Visual Studio příkazy nabídky nejsou k dispozici v případě, že nejste připojeni k SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Vytvoření pracovní položky pro chybu ověřování

- V **seznam chyb** okna, klikněte pravým tlačítkem na chyby, přejděte na **vytvořit pracovní položku**a potom klikněte na typ pracovní položky, kterou chcete vytvořit.

Tyto úlohy slouží ke správě chyb ověřování v **seznam chyb** okno:

|**k**|**Postupujte podle těchto kroků**|
|-|-|
|Potlačení vybraných chyb během ověřování|Klikněte pravým tlačítkem na jeden nebo více vybraných chyb, přejděte na **spravovat chyby ověřování**a potom klikněte na tlačítko **potlačit chyby**.<br /><br /> Potlačené chyby se zobrazují s přeškrtnutím. Při příštím spuštění ověřování se tyto chyby nezobrazí.<br /><br /> Potlačené chyby jsou sledovány v souboru .suppressions pro odpovídající soubor diagramu závislostí.|
|Ukončení potlačování vybraných chyb|Klikněte pravým tlačítkem na Potlačené chyby nebo chyby, přejděte na **spravovat chyby ověřování**a potom klikněte na tlačítko **ukončit potlačování chyb**.<br /><br /> Vybrané potlačené chyby se při příštím spuštění ověřování zobrazí.|
|Obnovení všech potlačených chyb v **seznam chyb** okna|Klikněte pravým tlačítkem kamkoli **seznam chyb** okno, přejděte na příkaz **spravovat chyby ověřování**a potom klikněte na tlačítko **zobrazit všechny Potlačené chyby**.|
|Skrytí všech potlačených chyb v **seznam chyb** okna|Klikněte pravým tlačítkem kamkoli **seznam chyb** okno, přejděte na příkaz **spravovat chyby ověřování**a potom klikněte na tlačítko **skrýt všechny Potlačené chyby**.|

## <a name="validate-code-automatically"></a>Ověřování kódu automaticky

Ověřování vrstev lze provádět při každém spuštění místního sestavení. Pokud váš tým používá Azure DevOps, můžete provést ověření vrstev s ověřenými vráceními se změnami, které lze určit vytvořením vlastní úlohy MSBuild a použít sestavy sestavení pro sběr chyb ověřování. Vytvoření sestavení hlídaného vrácení se změnami naleznete v tématu [TFVC hlídané vrácení se změnami](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Automatické ověřování kódu během místního sestavení

K otevření souboru projektu modelování (.modelproj) použijte textový editor a následně vložte následující vlastnost:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- nebo –

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt modelování obsahující diagram závislostí nebo diagramy a pak klikněte na **vlastnosti**.

2.  V **vlastnosti** okno, nastavte projekt modelování **ověřit architekturu** vlastnost **True**.

    To zahrne projekt modelování do ověřovacího procesu.

3.  V **Průzkumníka řešení**, klikněte na soubor diagramu (.layerdiagram) závislost, kterou chcete použít pro ověřování.

4.  V **vlastnosti** okno, ujistěte se, že v diagramu **akce sestavení** je nastavena na **ověřit**.

    To zahrnuje diagram závislostí do ověřovacího procesu.

Ke správě chyb v okně Seznam chyb, naleznete v tématu [spravovat chyby ověřování](#ManageErrors).

## <a name="troubleshoot-layer-validation-issues"></a>Poradce při potížích s ověřením vrstvy

Následující tabulka popisuje problémy s ověřením vrstvy a jejich řešení. Tyto problémy se liší od chyb, které vzniknou z konfliktů mezi kódem a návrhem. Další informace o těchto chybách naleznete v tématu [pochopení a vyřešení chyb ověřování vrstev](#UnderstandingValidationErrors).

|**Problém**|**Možná příčina**|**Řešení**|
|-|-|-|
|Chyby ověřování se nezobrazí podle očekávání.|Ověřování nefunguje v diagramech závislosti, které jsou zkopírovány z jiných diagramů závislostí v Průzkumníku řešení a jsou ve stejném projektu modelování. diagramy závislostí, které jsou tímto způsobem zkopírují, obsahují stejné odkazy jako původní diagram závislostí.|Přidejte do projektu modelování nový diagram závislostí.<br /><br /> Zkopírujte prvky ze zdrojového diagramu závislostí do nového diagramu.|

## <a name="resolve-layer-validation-errors"></a>Řešení chyb při ověřování vrstvy

Při ověřování kódu proti diagramu závislost vyskytnou chyby, pokud kód je v konfliktu s návrhem. Chyby ověřování mohou způsobit například následující podmínky:

- Artefakt je přiřazen nesprávné vrstvě. V tomto případě přesuňte artefakt.

- Artefakt, jako je například třída, používá jiné třídy způsobem, který je v konfliktu s architekturou. V tomto případě refaktorujte kód a odeberte závislost.

Chcete-li tyto chyby odstranit, aktualizujte kód, dokud se během ověřování neobjeví žádné chyby. Tuto úlohu lze provést iteračním způsobem.

Následující oddíl popisuje syntaxi, která se u těchto chyb používá, vysvětluje význam těchto chyb a navrhne, jak je vyřešit nebo spravovat.

|**Syntaxe**|**Popis**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* je artefakt, který je spojen s vrstvou v diagramu závislostí.<br /><br /> *ArtifactTypeN* je typ *ArtifactN*, například **třídy** nebo **metoda**, například:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Název oboru názvů.|
|*LayerNameN*|Název vrstvy na diagram závislostí.|
|*DependencyType*|Typ vztahu závislosti mezi *Artifact1* a *Artifact2*. Například *Artifact1* má **volání** vztah s *Artifact2*.|

| **Chyba syntaxe** | **Popis chyby** |
|-|-|
| DV0001: **Neplatná závislost** | Tento problém je oznamují prvek kódu (obor názvů, typ, členství) mapovat na odkazy vrstvy prvek kódu, který je namapována na jinou vrstvu, ale neexistuje žádná šipky závislostí mezi tyto vrstvy v diagram ověřování závislostí obsahující této vrstvy. To je narušení omezení závislosti. |
| DV1001: **neplatný název oboru názvů** | Tento problém je uveden na prvek kódu spojené s vrstvou, která vlastnost "názvů Namespace povoleno" neobsahuje obor názvů, ve kterém je definována tento prvek kódu. To je narušení omezení vytváření názvů. Všimněte si, že syntaxe názvů Namespace"povoleno", které má být středníkem seznam oborů názvů v kódu jsou elementy související s vrstvou se smí být definované. |
| DV1002: **závislost na u oboru názvů** | Tento problém je uveden na prvek kódu spojené s vrstvou a odkazuje na jiný element kód definovaný v oboru názvů, který je definován v "U Namespace" Vlastnosti vrstvy. To je narušení omezení vytváření názvů. Všimněte si, že vlastnost "Odkazy názvů" je definován jako středníkem oddělený seznam oborů názvů, které nesmí elementy kódu přidružené k této vrstvě odkazovat. |
| DV1003: **název oboru názvů Nepovoleno** | Tento problém je uveden na prvek kódu spojené s vrstvou obsahující obor názvů, ve kterém je tento prvek kódu definována vlastnost "názvů Namespace zakázáno". To je narušení omezení vytváření názvů. Všimněte si, že vlastnost "Název oboru názvů Nepovoleno" je definován jako středníkem oddělený seznam oborů názvů, ve které kódu nesmí být definována prvky přidružené k této vrstvě. |
| DV3001: **chybějící spojení** | Vrstva "*LayerName*"odkazuje na"*artefaktů*" který nebyl nalezen. Nechybí odkaz na sestavení? |
| DV9001: **strukturální analýza nalezla vnitřní chyby** | Výsledky nemusí být úplné. Další informace lze nalézt v podrobném protokolu událostí sestavení nebo ve výstupním okně. |

## <a name="see-also"></a>Viz také:

- [Živé ověření závislosti v sadě Visual Studio 2017](https://blogs.msdn.microsoft.com/devops/2016/11/30/live-dependency-validation-in-visual-studio-2017/)
- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)
- [Video: Ověření závislostí architektury v reálném čase](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)