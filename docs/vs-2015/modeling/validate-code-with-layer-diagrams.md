---
title: Ověřování kódu pomocí diagramů vrstev | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4d010345c551572bb6458110d2de9ca33fc73155
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792161"
---
# <a name="validate-code-with-layer-diagrams"></a>Ověřování kódu pomocí diagramů vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete mít jistotu, že kód není v konfliktu s návrhem, ověřování kódu pomocí diagramů vrstev v sadě Visual Studio. To může pomoci při:  
  
- Vyhledání konfliktů mezi závislostmi v kódu a závislostmi v diagramu vrstev.  
  
- Vyhledání závislostí, které mohou být ovlivněny navrhovanými změnami.  
  
   Například lze upravit diagram vrstev pro zobrazení možných změn architektury a následně ověřit kód pro vyhledání ovlivněných závislostí.  
  
- Refaktorujte nebo přeneste kód do jiného návrhu.  
  
   Vyhledejte kód nebo závislosti, které vyžadují práci při přenesení kódu do jiné architektury.  
  
  **Požadavky**  
  
- Visual Studio  
  
- Visual Studio na vašem serveru Team Foundation Build pro automatické ověřování kódu pomocí Team Foundation Build  
  
- Řešení, které má projekt modelování s diagramem vrstev. Tento diagram vrstev musí být spojen s artefakty v projektech Visual C# .NET nebo Visual Basic .NET, které chcete ověřit. Zobrazit [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md).  
  
  Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
  Kód lze ověřit manuálně z otevřeného diagramu vrstev v systému Visual Studio nebo z příkazového řádku. Kód lze rovněž automaticky ověřit při spuštění místních sestavení nebo procesu Team Foundation Build. Zobrazit [Video pro kanál 9: návrh a ověření architektury pomocí diagramů vrstev](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
> [!IMPORTANT]
>  Pokud chcete spustit ověření vrstvy pomocí procesu Team Foundation Build, je rovněž nutné nainstalovat stejnou verzi sady Visual Studio na svém serveru sestavení.  
  
-   [Zobrazit, pokud položka podporuje validaci](#SupportsValidation)  
  
-   [Zahrnout další sestavení a projekty .NET pro ověření](#IncludeReferences)  
  
-   [Ověřování kódu ručně](#ValidateManually)  
  
-   [Ověřování kódu automaticky](#ValidateAuto)  
  
-   [Řešení potíží s problémy s ověřením vrstvy](#TroubleshootingValidation)  
  
-   [Pochopení a vyřešení chyb ověřování vrstev](#UnderstandingValidationErrors)  
  
##  <a name="SupportsValidation"></a> Zobrazit, pokud položka podporuje validaci  
 Vrstvy můžete propojit s weby, dokumenty Office, místo textových souborů a soubory v projektech, které jsou sdíleny napříč více aplikacemi, ale proces ověření nebude zahrnovat je. Chyby ověřování se neobjeví pro odkazy na projekty nebo sestavení, které jsou připojeny k samostatným vrstvám a v případě, že se mezi těmito vrstvami neobjeví závislosti. Tyto odkazy jsou považovány za závislosti jen tehdy, pokud kód tyto odkazy používá.  
  
1.  V diagramu vrstev vyberte jednu nebo více vrstev, klikněte pravým tlačítkem na svůj výběr a potom klikněte na tlačítko **zobrazit odkazy**.  
  
2.  V **Průzkumník vrstev**, podívejte se na **podporuje ověřování** sloupce. Pokud je hodnota false, položka ověřování nepodporuje.  
  
##  <a name="IncludeReferences"></a> Zahrnout další sestavení a projekty .NET pro ověření  
 Při přetažení položky do diagramu vrstev, odkazy odpovídající sestavení nebo projekty .NET přidány automaticky do **odkazy vrstvy** složky v projektu modelování. Tato složka obsahuje odkazy na sestavení a projekty, které jsou analyzovány během ověřování. Další sestavení a projekty .NET lze vložit do diagramu vrstev pro ověření bez nutnosti je ručně přetahovat.  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt modelování nebo **odkazy vrstvy** složku a pak klikněte na tlačítko **přidat odkaz**.  
  
2.  V **přidat odkaz** dialogovém okně vyberte projekty nebo sestavení a klikněte na **OK**.  
  
##  <a name="ValidateManually"></a> Ověřování kódu ručně  
 Pokud máte otevřeného diagramu vrstev, který je propojen s položkami řešení, můžete spustit **ověřit** příkaz z diagramu. Můžete také použít příkazový řádek ke spuštění **msbuild** příkazů **validatearchitecture** vlastní vlastnost nastavena na **True**. Například lze při provádění změn v kódu provádět pravidelně ověřování vrstvy, takže bude možné zachytit konflikty závislostí včas.  
  
#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Ověření kódu z otevřeného diagramu vrstev  
  
1.  Klikněte pravým tlačítkem na plochu diagramu a potom klikněte na tlačítko **ověřit architekturu**.  
  
    > [!NOTE]
    >  Ve výchozím nastavení **akce sestavení** vlastnost v souboru layer diagram (.layerdiagram) nastavena na **ověřit** tak, aby diagram je součástí procesu ověřování.  
  
     **Seznam chyb** okno hlásí chyby, ke kterým dochází. Další informace o chybách ověřování najdete v části [pochopení a vyřešení chyb ověřování vrstev](#UnderstandingValidationErrors).  
  
2.  Chcete-li zobrazit zdroje každé chyby, klikněte dvakrát na chybu v **seznam chyb** okna.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mapy kódu může namísto zdroje chyby zobrazit. K tomu dochází, pokud kód obsahuje závislost na sestavení, které není specifikováno diagramem vrstvy, nebo pokud kódu chybí závislost zadaná pomocí diagramu vrstev. Projděte si mapu kódu nebo kód určující, zda by měla závislost existovat. Další informace o mapách kódu najdete v tématu [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md).  
  
3.  Ke správě chyb, naleznete v tématu [spravovat chyby ověřování](#ManageErrors).  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>Ověřování kódu v příkazovém řádku  
  
1. Otevřít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku.  
  
2. Vyberte jednu z následujících možností:  
  
   - Pro ověření kódu proti konkrétnímu projektu modelování v řešení spusťte [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] s následující vlastní vlastností.  
  
     ```  
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
     ```  
  
     - nebo –  
  
       Přejděte do složky, která obsahuje modelování (.modelproj) souboru a diagram vrstev projektu a pak spusťte [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] s následující vlastní vlastností:  
  
     ```  
     msbuild /p:ValidateArchitecture=true   
     ```  
  
   - Pro ověření kódu proti všem projektům modelování v řešení spusťte [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] s následující vlastní vlastností:  
  
     ```  
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
     ```  
  
     - nebo –  
  
       Přejděte do složky řešení, které musí obsahovat projekt modelování obsahující diagram vrstev a pak spusťte [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] s následující vlastní vlastností:  
  
     ```  
     msbuild /p:ValidateArchitecture=true  
     ```  
  
     Zobrazí se všechny chyby, ke kterým dochází. Další informace o [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], naleznete v tématu [MSBuild](../msbuild/msbuild.md) a [úlohy nástroje MSBuild](../msbuild/msbuild-task.md).  
  
   Další informace o chybách ověřování najdete v části [pochopení a vyřešení chyb ověřování vrstev](#UnderstandingValidationErrors).  
  
###  <a name="ManageErrors"></a> Správa chyb ověřování  
 Během procesu vývoje můžete chtít potlačit některé vykázané konflikty během ověřování. Například můžete chtít potlačit chyby, které již řešíte nebo které nejsou relevantní k danému scénáři. Při potlačení chyby je praktikou zaznamenat pracovní položku [!INCLUDE[esprfound](../includes/esprfound-md.md)].  
  
> [!WARNING]
>  Musíte už být připojení k TFS zdrojového kódu ovládacího prvku (SCC) vytvořit nebo propojit s pracovní položkou. Pokud se pokusíte otevřít připojení k jiné SCC TFS, Visual Studio automaticky zavře aktuální řešení. Ujistěte se, že jste již připojeni k příslušné SCC než se pokusíte vytvořit nebo propojit s pracovní položkou. V pozdějších verzích sady Visual Studio příkazy nabídky nejsou k dispozici v případě, že nejste připojeni k SCC.  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>Vytvoření pracovní položky pro chybu ověřování  
  
- V **seznam chyb** okna, klikněte pravým tlačítkem na chyby, přejděte na **vytvořit pracovní položku**a potom klikněte na typ pracovní položky, kterou chcete vytvořit.  
  
  Tyto úlohy slouží ke správě chyb ověřování v **seznam chyb** okno:  
  
|**k**|**Postupujte podle těchto kroků**|  
|------------|----------------------------|  
|Potlačení vybraných chyb během ověřování|Klikněte pravým tlačítkem na jeden nebo více vybraných chyb, přejděte na **spravovat chyby ověřování**a potom klikněte na tlačítko **potlačit chyby**.<br /><br /> Potlačené chyby se zobrazují s přeškrtnutím. Při příštím spuštění ověřování se tyto chyby nezobrazí.<br /><br /> Potlačené chyby jsou sledovány v souboru .suppressions pro odpovídající soubor diagramu vrstev.|  
|Ukončení potlačování vybraných chyb|Klikněte pravým tlačítkem na Potlačené chyby nebo chyby, přejděte na **spravovat chyby ověřování**a potom klikněte na tlačítko **ukončit potlačování chyb**.<br /><br /> Vybrané potlačené chyby se při příštím spuštění ověřování zobrazí.|  
|Obnovení všech potlačených chyb v **seznam chyb** okna|Klikněte pravým tlačítkem kamkoli **seznam chyb** okno, přejděte na příkaz **spravovat chyby ověřování**a potom klikněte na tlačítko **zobrazit všechny Potlačené chyby**.|  
|Skrytí všech potlačených chyb v **seznam chyb** okna|Klikněte pravým tlačítkem kamkoli **seznam chyb** okno, přejděte na příkaz **spravovat chyby ověřování**a potom klikněte na tlačítko **skrýt všechny Potlačené chyby**.|  
  
##  <a name="ValidateAuto"></a> Ověřování kódu automaticky  
 Ověřování vrstev lze provádět při každém spuštění místního sestavení. Pokud váš tým používá proces Team Foundation Build, můžete provést ověření vrstev s ověřenými vráceními se změnami, které lze určit vytvořením vlastní úlohy MSBuild, a použít sestavy sestavení pro sběr chyb ověřování. Vytvoření sestavení hlídaného vrácení se změnami naleznete v tématu [použít proces sestavení hlídaného vrácení se změnami pro ověření změn](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>Automatické ověřování kódu během místního sestavení  
  
-   K otevření souboru projektu modelování (.modelproj) použijte textový editor a následně vložte následující vlastnost:  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- nebo –  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt modelování obsahující diagram vrstev a diagramů a pak klikněte na tlačítko **vlastnosti**.  
  
2. V **vlastnosti** okno, nastavte projekt modelování **ověřit architekturu** vlastnost **True**.  
  
    To zahrne projekt modelování do ověřovacího procesu.  
  
3. V **Průzkumníka řešení**, klikněte na soubor diagramu (.layerdiagram) vrstev, který chcete použít pro ověřování.  
  
4. V **vlastnosti** okno, ujistěte se, že v diagramu **akce sestavení** je nastavena na **ověřit**.  
  
    To zahrne diagram vrstev do ověřovacího procesu.  
  
   Ke správě chyb v okně Seznam chyb, naleznete v tématu [spravovat chyby ověřování](#ManageErrors).  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Ověření kódu automaticky během sestavení Team Foundation Build  
  
1. V **Team Exploreru**, klikněte dvakrát na definici sestavení a pak klikněte na tlačítko **procesu**.  
  
2. V části **parametry procesu sestavení**, rozbalte **kompilace**a zadejte následující příkaz v **argumenty nástroje MSBuild** parametr:  
  
    `/p:ValidateArchitecture=true`  
  
   Další informace o chybách ověřování najdete v části [pochopení a vyřešení chyb ověřování vrstev](#UnderstandingValidationErrors). Další informace o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], naleznete v tématu:  
  
-   [Sestavení aplikace](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [Použít výchozí šablonu pro proces sestavení](http://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [Upravit starší verze sestavení, které jsou založeny na UpgradeTemplate.xaml](http://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [Přizpůsobení šablony procesu sestavení](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [Průběh můžete monitorovat spuštění sestavení](http://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="TroubleshootingValidation"></a> Řešení potíží s problémy s ověřením vrstvy  
 Následující tabulka popisuje problémy s ověřením vrstvy a jejich řešení. Tyto problémy se liší od chyb, které vzniknou z konfliktů mezi kódem a návrhem. Další informace o těchto chybách naleznete v tématu [pochopení a vyřešení chyb ověřování vrstev](#UnderstandingValidationErrors).  
  
|**Problém**|**Možná příčina**|**Řešení**|  
|---------------|------------------------|--------------------|  
|Chyby ověřování se nezobrazí podle očekávání.|Ověřování nefunguje v diagramech vrstev, které jsou zkopírovány z jiných diagramů vrstev v Průzkumníku řešení a jsou ve stejném projektu modelování. Diagramy vrstev, které se tímto způsobem zkopírují, obsahují stejné odkazy jako původní diagram vrstev.|Přidejte do projektu modelování nový diagram vrstev.<br /><br /> Zkopírujte prvky ze zdrojového diagramu vrstev do nového diagramu.|  
  
##  <a name="UnderstandingValidationErrors"></a> Pochopení a vyřešení chyb ověřování vrstev  
 Při ověřování kódu proti diagramu vrstev se vyskytnou chyby, pokud bude kód v konfliktu s návrhem. Chyby ověřování mohou způsobit například následující podmínky:  
  
- Artefakt je přiřazen nesprávné vrstvě. V tomto případě přesuňte artefakt.  
  
- Artefakt, jako je například třída, používá jiné třídy způsobem, který je v konfliktu s architekturou. V tomto případě refaktorujte kód a odeberte závislost.  
  
  Chcete-li tyto chyby odstranit, aktualizujte kód, dokud se během ověřování neobjeví žádné chyby. Tuto úlohu lze provést iteračním způsobem.  
  
  Následující oddíl popisuje syntaxi, která se u těchto chyb používá, vysvětluje význam těchto chyb a navrhne, jak je vyřešit nebo spravovat.  
  
|**Syntaxe**|**Popis**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* je artefakt, který je spojen s vrstvou v diagramu vrstev.<br /><br /> *ArtifactTypeN* je typ *ArtifactN*, například **třídy** nebo **metoda**, například:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|  
|*NamespaceNameN*|Název oboru názvů.|  
|*LayerNameN*|Název vrstvy v diagramu vrstev.|  
|*DependencyType*|Typ vztahu závislosti mezi *Artifact1* a *Artifact2*. Například *Artifact1* má **volání** vztah s *Artifact2*.|  
  
|**Chyba syntaxe**|**Popis chyby**|  
|----------------------|---------------------------|  
|AV0001: Neplatná závislost: *Artifact1*(*ArtifactType1*)--> *Artifact2*(*ArtifactType2*)<br /><br /> Vrstvy: *LayerName1*, *LayerName2* &#124; závislosti: *DependencyType*|*Artifact1* v *LayerName1* by neměl být závislý na *Artifact2* v *LayerName2* protože *LayerName1* nemá přímou závislost na *LayerName2*.|  
|AV1001: Neplatný Namespace: *artefaktu*<br /><br /> Vrstva: *LayerName* &#124; vyžaduje Namespace: *NamespaceName1* &#124; aktuální Namespace: *NamespaceName2*|*LayerName* vyžaduje, aby přidružené artefakty patřily do *NamespaceName1*. *Artefakt* probíhá *NamespaceName2*, nikoli *NamespaceName1*.|  
|AV1002: Závisí na zakázaném Namespace: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Vrstva: *LayerName* &#124; zakázáno Namespace: *NamespaceName* &#124; závislosti: *DependencyType*|*LayerName* vyžaduje, aby přidružené artefakty nebyly závislé na *NamespaceName*. *Artifact1* nemůže záviset na *Artifact2* protože *Artifact2* probíhá *NamespaceName*.|  
|AV1003: V zakázaném Namespace: *artefaktů*(*ArtifactType*)<br /><br /> Vrstva: *LayerName* &#124; zakázáno Namespace: *NamespaceName*|*LayerName* vyžaduje, aby přidružené artefakty nepatřily do *NamespaceName*. *Artefakt* patří *NamespaceName*.|  
|AV3001: Chybějící vazba: vrstva "*LayerName*"odkazuje na"*artefaktů*" který nebyl nalezen. Nechybí odkaz na sestavení?|*LayerName* odkazuje na artefakt, který nebyl nalezen. Odkaz na třídu může chybět například proto, že projekt modelování nemá odkaz na sestavení obsahující třídu.|  
|AV9001: Strukturální analýza nalezla vnitřní chyby. Výsledky nemusí být úplné. Další informace lze nalézt v podrobném protokolu událostí sestavení nebo ve výstupním okně.|Více podrobností lze nalézt v protokolu událostí sestavení nebo ve výstupním okně.|  
  
## <a name="security"></a>Zabezpečení  
  
## <a name="see-also"></a>Viz také  
 [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)



