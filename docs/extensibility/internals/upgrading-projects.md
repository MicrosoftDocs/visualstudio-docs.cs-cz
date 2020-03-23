---
title: Modernizace projektů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9170532746dfc61cdec6636fb669676a94535de1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303230"
---
# <a name="upgrading-projects"></a>Upgrade projektů

Změny modelu projektu z jedné verze sady Visual Studio do další může vyžadovat, aby projekty a řešení být upgradovány tak, aby mohly běžet na novější verzi. Poskytuje [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] rozhraní, které lze použít k implementaci podpory upgradu ve vlastních projektech.

## <a name="upgrade-strategies"></a>Strategie upgradu

Pro podporu upgradu musí implementace systému projektu definovat a implementovat strategii upgradu. Při určování strategie můžete podporovat zálohování vedle sebe (SxS), zálohování zkopírování nebo obojí.

- Zálohování SxS znamená, že projekt zkopíruje pouze ty soubory, které je třeba upgradovat na místě, přidání vhodné přípony názvu souboru, například ".old".

- Kopírování zálohy znamená, že projekt zkopíruje všechny položky projektu do umístění zálohy poskytnuté uživatelem. Příslušné soubory v původním umístění projektu jsou pak inovovány.

## <a name="how-upgrade-works"></a>Jak funguje upgrade

Při otevření řešení vytvořeného v dřívější verzi sady Visual Studio v novější verzi ide zkontroluje soubor řešení k určení, zda je třeba inovovat. Pokud je vyžadována inovace, **průvodce upgradem** se automaticky spustí, aby uživatele provedl procesem upgradu.

Když řešení potřebuje upgrade, dotazuje se každé továrny projektu na strategii upgradu. Strategie určuje, zda továrna projektu podporuje zálohování kopií nebo zálohování SxS. Informace jsou odeslány **Průvodci upgradem**, který shromažďuje informace požadované pro zálohování a představuje uživateli příslušné možnosti.

### <a name="multi-project-solutions"></a>Řešení pro více projektů

Pokud řešení obsahuje více projektů a strategie upgradu se liší, například když projekt Jazyka C++, který podporuje pouze zálohování SxS a webový projekt, který podporuje pouze kopírování záloh, továrny projektu musí vyjednat strategii upgradu.

Řešení dotazuje každý <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>projekt factory pro . Potom volá, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> zda globální soubory projektu potřebují upgrade a určit podporované strategie upgradu. **Průvodce upgradem** je pak vyvolán.

Po dokončení průvodce uživatelem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> je volána na každé projektu továrny k provedení skutečné inovace. Pro usnadnění zálohování, IVsProjectUpgradeViaFactory <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> metody poskytují službu protokolovat podrobnosti o procesu upgradu. Tuto službu nelze uložit do mezipaměti.

Po aktualizaci všech relevantních globálních souborů může každá továrna projektu zvolit vytvoření instance projektu. Realizace projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>musí podporovat . Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> je pak volána k upgradu všech příslušných položek projektu.

> [!NOTE]
> Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> neposkytuje službu SVsUpgradeLogger. Tuto službu lze <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>získat na telefonním čísle .

## <a name="best-practices"></a>Osvědčené postupy

Pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> služby zkontrolujte, zda můžete soubor před úpravami upravit, a můžete jej před uložením uložit. To pomůže implementaci zálohování a upgradu zpracovávat soubory projektu pod správě zdrojového kódu, soubory s nedostatečnými oprávněními a tak dále.

Pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> služby ve všech fázích zálohování a upgradu poskytnout informace o úspěchu nebo neúspěchu procesu upgradu.

Další informace o zálohování a upgradu projektů naleznete v komentářích pro IVsProjectUpgrade v vsshell2.idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a>Inovace vlastních projektů

Pokud změníte informace trvalé v souboru projektu mezi různými verzemi sady Visual Studio produktu, budete muset podporovat upgrade souboru projektu ze staré na novou verzi. Chcete-li podporovat inovaci, která umožňuje účast v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> **Průvodci převodem sady Visual Studio**, implementujte rozhraní. Toto rozhraní obsahuje jediný mechanismus, který je k dispozici pro upgrade kopie. Upgrade projektu se stane jako součást řešení otevře. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> je implementováno factory projektu, nebo by měly být alespoň získat z továrny projektu.

Starý mechanismus, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> který používá rozhraní je stále podporována, ale koncepčně upgraduje systém projektu jako součást projektu otevřít. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> je proto volána prostředí sady <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Visual Studio i v případě, že rozhraní je volána nebo implementována. Tento přístup umožňuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> použít k implementaci kopie a projekt pouze části upgradu a delegovat zbytek práce, které mají <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> být provedeny na místě (případně v novém umístění) rozhraním.

Ukázková implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>aplikace naleznete [v tématu VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Následující scénáře vznikají s upgrady projektu:

- Pokud je soubor novějšího formátu, než může projekt podporovat, musí vrátit chybu s uvedením tohoto. To předpokládá, že starší verze produktu obsahuje kód pro kontrolu verze.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> je příznak zadán <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> v metodě, upgrade bude implementován jako inovace na místě před otevřením projektu.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> je příznak zadán <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> v metodě, upgrade je implementován jako upgrade kopie.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> je příznak zadán <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> ve volání, pak byl uživatel vyzván prostředím k upgradu souboru projektu jako inovace na místě po otevření projektu. Prostředí například vyzve uživatele k upgradu, když uživatel otevře starší verzi řešení.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> příznak není zadán <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> ve volání, musíte vyzvat uživatele k upgradu souboru projektu.

     Následuje ukázková zpráva s výzvou k upgradu:

     "Projekt '%1' byl vytvořen se starší verzí sady Visual Studio. Pokud jej otevřete pomocí této verze sady Visual Studio, pravděpodobně ji nebudete moci otevřít se staršími verzemi sady Visual Studio. Chcete pokračovat a otevřít tento projekt?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Implementace IVsProjectUpgradeViaFactory

1. Implementujte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> konkrétně metodu v implementaci projektu z výroby nebo proveďte implementace volatelné z implementace továrny projektu.

2. Pokud chcete provést upgrade na místě jako součást otevření řešení, <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> zadejte `VSPUVF_FLAGS` příznak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jako parametr v implementaci.

3. Pokud chcete provést upgrade na místě jako součást otevření řešení, <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> zadejte `VSPUVF_FLAGS` příznak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jako parametr v implementaci.

4. Pro kroky 2 a 3 lze implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>skutečné kroky upgradu souboru pomocí `IVsProjectUpgade`aplikace , jak je popsáno v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>části Implementace , nebo můžete delegovat skutečný upgrade souboru na .

5. Metody odeslání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> souvisejících zpráv o upgradu pro uživatele pomocí Průvodce migrací sady Visual Studio.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>rozhraní se používá k implementaci jakéhokoli druhu upgradu souboru, který se musí stát v rámci upgradu projektu. Toto rozhraní není <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>volána z aplikace , ale je dodávánjako mechanismus pro upgrade souborů, které jsou součástí systému projektu, ale hlavní systém projektu nemusí být přímo vědomi. Například tato situace může nastat, pokud soubory a vlastnosti související s kompilátorem nejsou zpracovány stejným vývojovým týmem, který zpracovává zbytek systému projektu.

### <a name="ivsprojectupgrade-implementation"></a>Implementace upgradu projektu IVsProject

Pokud systém projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementuje pouze, nemůže se účastnit **Průvodce převodem sady Visual Studio**. Však i v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> případě, že implementovat rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> můžete stále delegovat upgrade souboru na implementaci.

#### <a name="to-implement-ivsprojectupgrade"></a>Implementace iVsProjectUpgrade

1. Když se uživatel pokusí otevřít projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda je volána prostředí po otevření projektu a před jakoukoli jinou akci uživatele může být provedena v projektu. Pokud uživatel již byla vyzvána k upgradu <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> řešení, pak `grfUpgradeFlags` příznak je předán v parametru. Pokud uživatel otevře projekt přímo, například pomocí příkazu Přidat <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> existující **projekt,** příznak není předán a projekt musí vyzvat uživatele k upgradu.

2. V reakci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> na volání musí projekt vyhodnotit, zda je soubor projektu upgradován. Pokud projekt není nutné upgradovat typ projektu na novou verzi, <xref:Microsoft.VisualStudio.VSConstants.S_OK> pak může jednoduše vrátit příznak.

3. Pokud projekt potřebuje upgradovat typ projektu na novou verzi, musí určit, zda soubor <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> projektu lze změnit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> voláním `rgfQueryEdit` metody a předáním hodnoty parametru. Projekt pak musí provést následující kroky:

    - Pokud `VSQueryEditResult` je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>hodnota `pfEditCanceled` vrácená v parametru , může inovace pokračovat, protože soubor projektu může být zapsán.

    - Pokud `VSQueryEditResult` `pfEditCanceled` je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> hodnota vrácená v `VSQueryEditResult` parametru <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> a hodnota <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> má nastavený bit, musí vrátit selhání, protože uživatelé by měli vyřešit problém oprávnění sami. Projekt by pak měl provést následující kroky:

         Oznamte chybu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> uživateli <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>a vraťte kód chyby společnosti .

    - Pokud `VSQueryEditResult` je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> hodnota `VSQueryEditResultFlags` a hodnota <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> má nastavený bit, pak soubor projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>by <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>měl být rezervován voláním ( , ,...).

4. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> volání souboru projektu způsobí, že soubor má být rezervován a nejnovější verze, které mají být načteny, pak je projekt uvolněn a znovu načten. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> je volána znovu, jakmile je vytvořena jiná instance projektu. Při tomto druhém volání lze soubor projektu zapsat na disk; doporučujeme, aby projekt uložil kopii souboru projektu v předchozím formátu s . OLD příponu, proveďte potřebné změny upgradu a uložte soubor projektu v novém formátu. Opět platí, že pokud se nezdaří některá část <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>procesu upgradu, musí metoda indikovat selhání vrácením . To způsobí, že projekt má být uvolněnv Průzkumníka řešení.

     Je důležité pochopit celý proces, ke kterému dochází v prostředí pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> případ, ve kterém volání metody (zadání hodnoty ReportOnly) vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> příznaky.

5. Uživatel se pokusí otevřít soubor projektu.

6. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementaci.

7. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true`vrátí , pak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> prostředí volá implementaci.

8. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementaci k otevření souboru a inicializaci objektu projektu, například Project1.

9. Prostředí volá `IVsProjectUpgrade::UpgradeProject` implementaci k určení, zda je třeba upgradovat soubor projektu.

10. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předání hodnoty <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> parametru. `rgfQueryEdit`

11. Prostředí se <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> `VSQueryEditResult` vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> a bit `VSQueryEditResultFlags`je nastaven v .

12. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementace `IVsQueryEditQuerySave::QueryEditFiles` <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>, ).

Toto volání může způsobit novou kopii souboru projektu, které mají být rezervovány a nejnovější verze načtena, stejně jako potřeba znovu načíst soubor projektu. V tomto okamžiku se stane jedna ze dvou věcí:

- Pokud zpracovat vlastní projekt znovu načíst, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> pak prostředí volá (VSITEMID_ROOT) implementace. Po přijetí tohoto volání znovu načtěte první instanci projektu (Project1) a pokračujte v inovaci souboru projektu. Prostředí ví, že zpracovat vlastní projekt `true` znovu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>načíst, pokud se vrátíte pro ( ).

- Pokud nezvládáte vlastní projekt znovu `false` načíst, pak se vrátíte pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). V tomto případě <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>před (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) vrátí, prostředí vytvoří další novou instanci projektu, například Project2, takto:

    1. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> na první objekt projektu Project1, a tím umístit tento objekt do neaktivního stavu.

    2. Prostředí volá `IVsProjectFactory::CreateProject` implementaci k vytvoření druhé instance projektu Project2.

    3. Prostředí volá `IPersistFileFormat::Load` implementaci k otevření souboru a inicializaci druhého objektu projektu Project2.

    4. Prostředí volá `IVsProjectUpgrade::UpgradeProject` podruhé k určení, zda má být upgradován objekt projektu. Toto volání je však na nové, second, instance projektu Project2. Toto je projekt, který je otevřen v řešení.

        > [!NOTE]
        > V případě, že váš první projekt, Project1, je umístěn v <xref:Microsoft.VisualStudio.VSConstants.S_OK> neaktivním stavu, pak se musíte vrátit z první volání do implementace. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>

    5. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předání hodnoty <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> parametru. `rgfQueryEdit`

    6. Prostředí se <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> vrátí a upgrade může pokračovat, protože soubor projektu lze zapsat.

Pokud se vám nepodaří inovovat, vraťte se <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> z . `IVsProjectUpgrade::UpgradeProject` Pokud není nutný žádný upgrade nebo se `IVsProjectUpgrade::UpgradeProject` rozhodnete neupgradovat, považovat volání za no-op. Pokud vrátíte <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, zástupný uzel je přidán do řešení pro váš projekt.

## <a name="upgrading-project-items"></a>Inovace položek projektu

Pokud přidáte nebo spravujete položky v projektových systémech, které neimplementujete, bude pravděpodobně nutné se účastnit procesu upgradu projektu. Crystal Reports je příkladem položky, kterou lze přidat do systému projektu.

Implementátoři položek projektu obvykle chtějí využít již plně instancied a upgradovaný projekt, protože potřebují vědět, jaké jsou odkazy na projekt a jaké další vlastnosti projektu jsou k dispozici pro rozhodnutí o upgradu.

### <a name="to-get-the-project-upgrade-notification"></a>Získání oznámení o upgradu projektu

1. Nastavte <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> příznak (definovaný v vsshell80.idl) v implementaci položky projektu. To způsobí, že položka projektu VSPackage automaticky načíst, když prostředí Sady Visual Studio určuje, že systém projektu je v procesu inovace.

2. Poradit <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> pomocí metody.

3. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> je aktivována po implementaci systému projektu dokončil a je vytvořen nový upgradovaný projekt. V závislosti na <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> scénáři je <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>aktivována <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> po , , nebo metody.

### <a name="to-upgrade-the-project-item-files"></a>Upgrade souborů položek projektu

1. Je nutné pečlivě spravovat proces zálohování souborů v implementaci položky projektu. To platí zejména pro zálohování vedle sebe, kde `fUpgradeFlag` je <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> parametr metody <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>nastaven na , kde jsou soubory, které byly zálohovány, umístěny vedle souborů, které jsou označeny jako ".old". Zálohované soubory starší než systémový čas při upgradu projektu lze označit jako zastaralé. Kromě toho mohou být přepsány, pokud nepodniknete konkrétní kroky, abyste tomu zabránili.

2. V době, kdy položka projektu získá oznámení o upgradu projektu, **průvodce převodem sady Visual Studio** se stále zobrazí. Proto byste měli použít metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> rozhraní k poskytování zpráv o upgradu do uživatelského rozhraní průvodce.

## <a name="see-also"></a>Viz také

- [Projekty](../../extensibility/internals/projects.md)
