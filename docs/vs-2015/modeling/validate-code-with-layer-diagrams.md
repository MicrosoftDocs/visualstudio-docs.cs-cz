---
title: Ověřování kódu pomocí diagramů vrstev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45b82ece15cfef4d313764027c0220453a6d4849
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845432"
---
# <a name="validate-code-with-layer-diagrams"></a>Ověřování kódu pomocí diagramů vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Abyste se ujistili, že kód není v konfliktu s jeho návrhem, ověřte kód pomocí diagramů vrstev v aplikaci Visual Studio. To může pomoci při:

- Vyhledání konfliktů mezi závislostmi v kódu a závislostmi v diagramu vrstev.

- Vyhledání závislostí, které mohou být ovlivněny navrhovanými změnami.

   Například lze upravit diagram vrstev pro zobrazení možných změn architektury a následně ověřit kód pro vyhledání ovlivněných závislostí.

- Refaktorujte nebo přeneste kód do jiného návrhu.

   Vyhledejte kód nebo závislosti, které vyžadují práci při přenesení kódu do jiné architektury.

  **Požadavky**

- Visual Studio

- Visual Studio na serveru Team Foundation Build pro automatické ověřování kódu pomocí Team Foundation Build

- Řešení, které má projekt modelování s diagramem vrstev. Tento diagram vrstev musí být spojen s artefakty v projektech Visual C# .NET nebo Visual Basic .NET, které chcete ověřit. Viz [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md).

  Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  Kód lze ověřit manuálně z otevřeného diagramu vrstev v systému Visual Studio nebo z příkazového řádku. Kód lze rovněž automaticky ověřit při spuštění místních sestavení nebo procesu Team Foundation Build. Viz [video o kanálu 9: návrh a ověření architektury pomocí diagramů vrstev](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Chcete-li spustit ověřování vrstvy pomocí sestavení Team Foundation Build, je nutné nainstalovat na server sestavení také stejnou verzi sady Visual Studio.

- [Zjištění, zda položka podporuje ověřování](#SupportsValidation)

- [Zahrnout další sestavení a projekty .NET k ověřování](#IncludeReferences)

- [Ruční ověření kódu](#ValidateManually)

- [Automaticky ověřit kód](#ValidateAuto)

- [Řešení potíží s ověřováním vrstev](#TroubleshootingValidation)

- [Pochopení a vyřešení chyb ověřování vrstvy](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a>Zjištění, zda položka podporuje ověřování
 V projektech, které jsou sdíleny napříč více aplikacemi, můžete propojit vrstvy na weby, dokumenty Office, textové soubory a soubory. proces ověřování je ale nebude zahrnovat. Chyby ověřování se neobjeví pro odkazy na projekty nebo sestavení, které jsou připojeny k samostatným vrstvám a v případě, že se mezi těmito vrstvami neobjeví závislosti. Tyto odkazy jsou považovány za závislosti jen tehdy, pokud kód tyto odkazy používá.

1. V diagramu vrstvy vyberte jednu nebo více vrstev, klikněte pravým tlačítkem myši na výběr a potom klikněte na možnost **Zobrazit odkazy**.

2. V **Průzkumníku vrstev**se podívejte do sloupce **podporuje ověřování** . Pokud je hodnota false, položka ověřování nepodporuje.

## <a name="IncludeReferences"></a>Zahrnout další sestavení a projekty .NET k ověřování
 Při přetahování položek do diagramu vrstev jsou odkazy na odpovídající sestavení nebo projekty .NET automaticky přidány do složky **odkazy na vrstvy** v projektu modelování. Tato složka obsahuje odkazy na sestavení a projekty, které jsou analyzovány během ověřování. Další sestavení a projekty .NET lze vložit do diagramu vrstev pro ověření bez nutnosti je ručně přetahovat.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt modelování nebo na složku **odkazy na vrstvu** a potom klikněte na tlačítko **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** vyberte sestavení nebo projekty a potom klikněte na tlačítko **OK**.

## <a name="ValidateManually"></a>Ruční ověření kódu
 Máte-li otevřený Diagram vrstev propojený s položkami řešení, můžete spustit příkaz **ověřit** zástupce z diagramu. Pomocí příkazového řádku můžete také spustit příkaz **MSBuild** s vlastní vlastností **/p: ValidateArchitecture** nastavenou na **hodnotu true**. Například lze při provádění změn v kódu provádět pravidelně ověřování vrstvy, takže bude možné zachytit konflikty závislostí včas.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Ověření kódu z otevřeného diagramu vrstev

1. Klikněte pravým tlačítkem na plochu diagramu a potom klikněte na **ověřit architekturu**.

    > [!NOTE]
    > Ve výchozím nastavení je vlastnost **Akce sestavení** v souboru diagramu vrstev (. layerdiagram) nastavena na hodnotu **ověřit** , aby byl diagram součástí procesu ověřování.

     Okno **Seznam chyb** nahlásí všechny chyby, ke kterým dojde. Další informace o chybách ověřování naleznete v tématu [pochopení a vyřešení chyb ověřování vrstvy](#UnderstandingValidationErrors).

2. Chcete-li zobrazit zdroj každé chyby, dvakrát klikněte na chybu v okně **Seznam chyb** .

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] může místo zdroje chyby zobrazit mapu kódu. K tomu dochází, pokud kód obsahuje závislost na sestavení, které není specifikováno diagramem vrstvy, nebo pokud kódu chybí závislost zadaná pomocí diagramu vrstev. Zkontrolujte mapu kódu nebo kód, abyste zjistili, zda by měla závislost existovat. Další informace o mapách kódu najdete v tématu [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md).

3. Chcete-li spravovat chyby, přečtěte si téma [Správa chyb ověřování](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>Ověřování kódu v příkazovém řádku

1. Otevřete příkazový řádek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Vyberte jednu z následujících možností:

   - Chcete-li ověřit kód proti konkrétnímu projektu modelování v řešení, spusťte [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] s následující vlastní vlastností.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - nebo –

       Přejděte do složky, která obsahuje soubor projektu modelování (. modelproj) a diagramu vrstev, a potom spusťte [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] s následující vlastní vlastností:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - Chcete-li ověřit kód pro všechny projekty modelování v řešení, spusťte [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] s následující vlastní vlastností:

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - nebo –

       Přejděte do složky řešení, která musí obsahovat projekt modelování, který obsahuje diagram vrstev, a potom spusťte [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] s následující vlastní vlastností:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     Zobrazí se všechny chyby, ke kterým dochází. Další informace o [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]najdete v tématu úloha [MSBuild](../msbuild/msbuild.md) a [MSBuild](../msbuild/msbuild-task.md).

   Další informace o chybách ověřování naleznete v tématu [pochopení a vyřešení chyb ověřování vrstvy](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a>Správa chyb ověřování
 Během procesu vývoje můžete chtít potlačit některé vykázané konflikty během ověřování. Například můžete chtít potlačit chyby, které již řešíte nebo které nejsou relevantní k danému scénáři. Pokud potlačíte chybu, je vhodné Protokolovat pracovní položku v [!INCLUDE[esprfound](../includes/esprfound-md.md)].

> [!WARNING]
> Aby bylo možné vytvořit nebo propojit pracovní položku, musíte být již připojeni ke správě zdrojového kódu TFS (SCC). Pokud se pokusíte otevřít připojení k jinému SCC TFS, Visual Studio automaticky zavře aktuální řešení. Před pokusem o vytvoření nebo propojení pracovní položky se ujistěte, že jste již připojeni k odpovídajícímu SCC. V novějších verzích sady Visual Studio nejsou příkazy nabídky k dispozici, pokud nejste připojeni k SCC.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Vytvoření pracovní položky pro chybu ověřování

- V okně **Seznam chyb** klikněte pravým tlačítkem myši na chybu, přejděte na příkaz **vytvořit pracovní položku**a poté klikněte na typ pracovní položky, kterou chcete vytvořit.

  Pomocí těchto úloh můžete spravovat chyby ověřování v okně **Seznam chyb** :

|**Komu**|**Postupujte podle těchto kroků**|
|------------|----------------------------|
|Potlačení vybraných chyb během ověřování|Klikněte pravým tlačítkem myši na jednu nebo více vybraných chyb, přejděte na položku **Spravovat chyby ověřování**a potom klikněte na **potlačit chyby**.<br /><br /> Potlačené chyby se zobrazují s přeškrtnutím. Při příštím spuštění ověřování se tyto chyby nezobrazí.<br /><br /> Potlačené chyby jsou sledovány v souboru .suppressions pro odpovídající soubor diagramu vrstev.|
|Ukončení potlačování vybraných chyb|Klikněte pravým tlačítkem myši na potlačit chybu nebo chyby, přejděte na položku **Spravovat chyby ověřování**a potom klikněte na možnost **ukončit potlačení chyb**.<br /><br /> Vybrané potlačené chyby se při příštím spuštění ověřování zobrazí.|
|Obnovit všechny Potlačené chyby v okně **Seznam chyb**|Klikněte pravým tlačítkem myši kdekoli v okně **Seznam chyb** , přejděte na položku **Spravovat chyby ověřování**a potom klikněte na možnost **Zobrazit všechny Potlačené chyby**.|
|Skrýt všechny Potlačené chyby z okna **Seznam chyb**|Klikněte pravým tlačítkem myši kdekoli v okně **Seznam chyb** , přejděte na možnost **Spravovat chyby ověřování**a potom klikněte na **Skrýt všechny Potlačené chyby**.|

## <a name="ValidateAuto"></a>Automaticky ověřit kód
 Ověřování vrstev lze provádět při každém spuštění místního sestavení. Pokud váš tým používá proces Team Foundation Build, můžete provést ověření vrstev s ověřenými vráceními se změnami, které lze určit vytvořením vlastní úlohy MSBuild, a použít sestavy sestavení pro sběr chyb ověřování. Chcete-li vytvořit ověřovaná sestavení pro vrácení se změnami, přečtěte si téma [použití procesu ověřovaného vrácení se změnami k ověření změn](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Automatické ověřování kódu během místního sestavení

- K otevření souboru projektu modelování (.modelproj) použijte textový editor a následně vložte následující vlastnost:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- nebo –

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt modelování, který obsahuje diagram vrstvy nebo diagramy, a poté klikněte na možnost **vlastnosti**.

2. V okně **vlastnosti** nastavte vlastnost **ověřit architekturu** projektu modelování na **hodnotu true**.

    To zahrne projekt modelování do ověřovacího procesu.

3. V **Průzkumník řešení**klikněte na soubor diagramu vrstev (. layerdiagram), který chcete použít k ověření.

4. V okně **vlastnosti** se ujistěte, že je vlastnost **Akce sestavení** diagramu nastavena na hodnotu **ověřit**.

    To zahrne diagram vrstev do ověřovacího procesu.

   Chcete-li spravovat chyby v okně Seznam chyb, přečtěte si téma [Správa chyb ověřování](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Ověření kódu automaticky během sestavení Team Foundation Build

1. V **Team Explorer**dvakrát klikněte na definici sestavení a pak klikněte na **proces**.

2. V části **Parametry procesu sestavení**rozbalte položku **kompilace**a do parametru **argumenty MSBuild** zadejte následující:

    `/p:ValidateArchitecture=true`

   Další informace o chybách ověřování naleznete v tématu [pochopení a vyřešení chyb ověřování vrstvy](#UnderstandingValidationErrors). Další informace o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]najdete v tématech:

- [Sestavení aplikace](/azure/devops/pipelines/index)

- [Použít výchozí šablonu pro proces sestavení](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Úprava starší verze sestavení, která je založena na UpgradeTemplate. XAML](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Přizpůsobení šablony procesu sestavení](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Sledování průběhu spuštěného buildu](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a>Řešení potíží s ověřováním vrstev
 Následující tabulka popisuje problémy s ověřením vrstvy a jejich řešení. Tyto problémy se liší od chyb, které vzniknou z konfliktů mezi kódem a návrhem. Další informace o těchto chybách naleznete v tématu [pochopení a vyřešení chyb ověřování vrstvy](#UnderstandingValidationErrors).

|**Problém**|**Možná příčina**|**Řešení**|
|---------------|------------------------|--------------------|
|Chyby ověřování se nezobrazí podle očekávání.|Ověřování nefunguje v diagramech vrstev, které jsou zkopírovány z jiných diagramů vrstev v Průzkumníku řešení a jsou ve stejném projektu modelování. Diagramy vrstev, které se tímto způsobem zkopírují, obsahují stejné odkazy jako původní diagram vrstev.|Přidejte do projektu modelování nový diagram vrstev.<br /><br /> Zkopírujte prvky ze zdrojového diagramu vrstev do nového diagramu.|

## <a name="UnderstandingValidationErrors"></a>Porozumění a řešení chyb při ověřování vrstvy
 Při ověřování kódu proti diagramu vrstev se vyskytnou chyby, pokud bude kód v konfliktu s návrhem. Chyby ověřování mohou způsobit například následující podmínky:

- Artefakt je přiřazen nesprávné vrstvě. V tomto případě přesuňte artefakt.

- Artefakt, jako je například třída, používá jiné třídy způsobem, který je v konfliktu s architekturou. V tomto případě refaktorujte kód a odeberte závislost.

  Chcete-li tyto chyby odstranit, aktualizujte kód, dokud se během ověřování neobjeví žádné chyby. Tuto úlohu lze provést iteračním způsobem.

  Následující oddíl popisuje syntaxi, která se u těchto chyb používá, vysvětluje význam těchto chyb a navrhne, jak je vyřešit nebo spravovat.

|**Syntaxe**|**Popis**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* je artefakt, který je spojen s vrstvou v diagramu vrstev.<br /><br /> *ArtifactTypeN* je typ *ArtifactN*, například **Třída** nebo **Metoda**, například:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Název oboru názvů.|
|*LayerNameN*|Název vrstvy v diagramu vrstev.|
|*DependencyType*|Typ vztahu závislostí mezi *artefakt Artifact1* a *Artifact2*. Například *artefakt Artifact1* má relaci **volání** s *Artifact2*.|

|**Chyba syntaxe**|**Popis chyby**|
|----------------------|---------------------------|
|AV0001: Neplatná závislost: *artefakt Artifact1*(*ArtifactType1*)--> *Artifact2*(*ArtifactType2*)<br /><br /> Vrstvy: *LayerName1*, *LayerName2* &#124; závislosti: *dependencyType*|*Artefakt Artifact1* v *LayerName1* by neměl mít závislost na *Artifact2* v *LayerName2* , protože *LayerName1* nemá přímou závislost na *LayerName2*.|
|AV1001: neplatný obor názvů: *artefakt*<br /><br /> Vrstva: *vrstva* &#124; vyžaduje obor názvů: *oboru názvů NamespaceName1* &#124; aktuální obor názvů: *NamespaceName2*|*Úroveň* ' oboru názvů NamespaceName1 ' vyžaduje, aby přidružené artefakty patřily do. *Artefakt* je v *NamespaceName2*, ne *oboru názvů NamespaceName1*.|
|AV1002: závisí na zakázaném oboru názvů: *artefakt Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*).<br /><br /> Vrstva: *vrstva* &#124; zakázaný obor názvů: &#124; závislosti *oboru názvů* : *dependencyType*|*Úroveň názvu vrstvy* vyžaduje, aby její přidružené artefakty nebyly závislé na *oboru názvů*. *Artefakt Artifact1* nemůže záviset na *Artifact2* , protože *Artifact2* je v *oboru názvů*.|
|AV1003: v zakázaném oboru názvů: *artefakt*(*ArtifactType*)<br /><br /> Vrstva: *vrstva* &#124; zakázaný obor názvů: *Namespace*|*Úroveň názvu vrstvy* vyžaduje, aby přidružené artefakty nepatřily do *oboru názvů*. *Artefakt* patří do *oboru názvů*.|
|AV3001: chybí propojení:*vrstva '* propojuje ' odkazuje na*artefakt*, který nebyl nalezen. Nechybí odkaz na sestavení?|*Propojování odkazuje na* artefakt, který nebyl nalezen. Odkaz na třídu může chybět například proto, že projekt modelování nemá odkaz na sestavení obsahující třídu.|
|AV9001: Strukturální analýza nalezla vnitřní chyby. Výsledky nemusí být úplné. Další informace lze nalézt v podrobném protokolu událostí sestavení nebo ve výstupním okně.|Více podrobností lze nalézt v protokolu událostí sestavení nebo ve výstupním okně.|

## <a name="security"></a>Zabezpečení –

## <a name="see-also"></a>Viz také
 [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)
