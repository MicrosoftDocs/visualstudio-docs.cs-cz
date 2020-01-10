---
title: Upgrade projektů | Microsoft Docs
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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848772"
---
# <a name="upgrading-projects"></a>Upgrade projektů

Změny modelu projektu z jedné verze sady Visual Studio na další může vyžadovat upgrade projektů a řešení, aby mohli běžet v novější verzi. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] poskytuje rozhraní, která lze použít k implementaci podpory upgradu ve vašich vlastních projektech.

## <a name="upgrade-strategies"></a>Strategie upgradu

Pro podporu upgradu musí vaše implementace systému projektu definovat a implementovat strategii upgradu. Při určování vaší strategie můžete zvolit podporu souběžného zálohování (SxS), zálohování kopírování nebo obojího.

- Záloha SxS znamená, že projekt kopíruje pouze soubory, které vyžadují upgrade, a přidává vhodné přípony názvu souboru, například ". old".

- Příkaz Kopírovat zálohu znamená, že projekt kopíruje všechny položky projektu do umístění zálohy zadaného uživatelem. Příslušné soubory v původním umístění projektu jsou poté upgradovány.

## <a name="how-upgrade-works"></a>Jak funguje upgrade

Když je řešení vytvořené v dřívější verzi sady Visual Studio otevřeno v novější verzi, rozhraní IDE zkontroluje soubor řešení a určí, jestli je potřeba upgradovat. Pokud je nutné upgradovat, **Průvodce upgradem** se automaticky spustí a provede uživatele procesem upgradu.

Když řešení vyžaduje upgrade, dotazuje se na každý objekt pro vytváření projektů pro strategii upgradu. Strategie určuje, zda objekt pro vytváření projektů podporuje zálohování kopírováním nebo SxS. Informace se odesílají do **Průvodce upgradem**, který shromažďuje informace požadované pro zálohování a prezentuje příslušné možnosti uživateli.

### <a name="multi-project-solutions"></a>Řešení s více projekty

Pokud řešení obsahuje více projektů a strategie upgradu se liší, například když C++ projekt, který podporuje pouze zálohu SxS, a webový projekt, který podporuje pouze zálohu kopírování, musí továrny projektu vyjednávat strategii upgradu.

Řešení se dotazuje na jednotlivé továrny projektu pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Pak zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> a zjistí, zda globální soubory projektu vyžadují upgrade, a určí podporované strategie upgradu. Pak se vyvolá **Průvodce upgradem** .

Až uživatel dokončí průvodce, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se zavolá v každé továrně projektu, aby se provedl skutečný upgrade. Pro usnadnění zálohování metody IVsProjectUpgradeViaFactory poskytují službě <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> k protokolování podrobností o procesu upgradu. Tuto službu nelze uložit do mezipaměti.

Po aktualizaci všech relevantních globálních souborů může každý objekt pro vytváření projektu zvolit vytvoření instance projektu. Implementace projektu musí podporovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> je pak volána pro upgrade všech relevantních položek projektu.

> [!NOTE]
> Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> neposkytuje službu SVsUpgradeLogger. Tuto službu lze získat voláním <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Doporučené postupy

Službu <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> použijte ke kontrole, jestli soubor před úpravou nemůžete upravit, a můžete ho před uložením Uložit. To pomůže vašim implementacím zálohování a upgradu zpracovat soubory projektu v rámci správy zdrojového kódu, souborů s nedostatečnými oprávněními a tak dále.

Služba <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> se používá během všech fází zálohování a upgradu, aby poskytovala informace o úspěchu nebo neúspěchu procesu upgradu.

Další informace o zálohování a upgradu projektů naleznete v tématu poznámky k IVsProjectUpgrade v vsshell2. idl.

## <a name="upgrading-custom-projects"></a>Upgrade vlastních projektů

Pokud změníte trvale uložené informace v souboru projektu mezi různými verzemi sady Visual Studio, je třeba podporovat upgrade souboru projektu z původní na novou verzi. Pro podporu upgradu, která vám umožní zúčastnit se **Průvodce převodem sady Visual Studio**, implementujte rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Toto rozhraní obsahuje jediný mechanismus, který je k dispozici pro upgrade kopírování. Upgrade projektu se stane součástí řešení. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> je implementováno pomocí objektu pro vytváření projektu, nebo by mělo být z objektu pro vytváření projektu získáno nejméně.

Starý mechanismus, který používá rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, je stále podporován, ale koncepčně upgraduje systém projektu jako součást projektu otevřeného. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> je proto voláno prostředím sady Visual Studio i v případě, že je rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> voláno nebo implementováno. Tento přístup umožňuje použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> k implementaci pouze částí upgradu, které jsou součástí upgradu, a delegovat zbývající část práce, která bude provedena místně (případně v novém umístění) pomocí rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

Ukázkovou implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>najdete v tématu [Ukázky VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

V případě upgradu projektu se vyskytnou následující scénáře:

- Pokud je soubor v novějším formátu, než může projekt podporovat, pak musí vrátit chybu informující o tom. Předpokládá se, že starší verze produktu obsahuje kód pro kontrolu verze.

- Pokud je v metodě <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> zadán příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, upgrade bude implementován jako místní upgrade před otevřením projektu.

- Pokud je v metodě <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> zadaný příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP>, upgrade se implementuje jako upgrade pro kopírování.

- Pokud je ve volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> zadán příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>, uživatel byl po otevření projektu vyzván v prostředí, aby provedl upgrade souboru projektu jako místní upgrade. Například prostředí vyzve uživatele k upgradu, když uživatel otevře starší verzi řešení.

- Pokud není příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> ve volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> zadán, je nutné, aby uživatel vyzvat, aby provedl upgrade souboru projektu.

     Následuje příklad zprávy s výzvou k upgradu:

     "Projekt" %1 "byl vytvořen ve starší verzi sady Visual Studio. Pokud jej otevřete v této verzi aplikace Visual Studio, pravděpodobně jej nebudete moci otevřít ve starších verzích sady Visual Studio. Chcete pokračovat a otevřít tento projekt? "

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Implementace IVsProjectUpgradeViaFactory

1. Implementujte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní, konkrétně metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> v implementaci továrny projektu, nebo proveďte implementace z implementace výroby projektu.

2. Pokud chcete provést místní upgrade jako součást otevírání řešení, zadejte příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> jako `VSPUVF_FLAGS` parametr v implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

3. Pokud chcete provést místní upgrade jako součást otevírání řešení, zadejte příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> jako `VSPUVF_FLAGS` parametr v implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

4. V případě kroků 2 a 3 je možné implementovat vlastní postup upgradu souborů pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, jak je popsáno v níže uvedené části "implementace `IVsProjectUpgade`" nebo můžete delegovat vlastní upgrade souboru na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5. Pomocí metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> vystavte zprávy související s upgradem pro uživatele pomocí Průvodce migrací sady Visual Studio.

6. rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> slouží k implementaci jakéhokoli typu upgradu souboru, který se musí nacházet jako součást upgradu projektu. Toto rozhraní není voláno z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ale je zadáno jako mechanismus pro upgrade souborů, které jsou součástí systému projektu, ale hlavní systém projektu nemusí být přímo vědom. Tato situace může nastat například v případě, že soubory a vlastnosti související s kompilátorem nejsou zpracovávány stejným vývojovým týmem, který zpracovává zbytek projektového systému.

### <a name="ivsprojectupgrade-implementation"></a>Implementace IVsProjectUpgrade

Pokud systém projektu implementuje pouze <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, nemůžete se zúčastnit **Průvodce převodem sady Visual Studio**. Nicméně i v případě, že implementujete rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, můžete i nadále delegovat upgrade souboru na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementaci.

#### <a name="to-implement-ivsprojectupgrade"></a>Implementace IVsProjectUpgrade

1. Když se uživatel pokusí otevřít projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda je volána prostředím po otevření projektu a před tím, než bude možné provést jakoukoli akci uživatele v projektu. Pokud uživatel již byl vyzván k upgradu řešení, bude příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> předán do parametru `grfUpgradeFlags`. Pokud uživatel otevře projekt přímo, například pomocí příkazu **Přidat existující projekt** , příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> není předán a projekt musí uživateli požádat o upgrade.

2. V reakci na volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musí projekt vyhodnotit, zda je soubor projektu upgradován. Pokud projekt nepotřebuje upgrade typu projektu na novou verzi, pak může jednoduše vrátit příznak <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Pokud projekt potřebuje upgradovat typ projektu na novou verzi, pak musí určit, zda lze soubor projektu upravit voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předáním hodnoty <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> parametru `rgfQueryEdit`. Projekt pak musí provést následující akce:

    - Pokud je hodnota `VSQueryEditResult` vrácená v parametru `pfEditCanceled` <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, může upgrade pokračovat, protože soubor projektu lze zapsat.

    - Pokud hodnota `VSQueryEditResult` vrácená parametrem `pfEditCanceled` je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a hodnota `VSQueryEditResult` má <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bitovou sadu, pak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musí vrátit chybu, protože uživatelé by měli vyřešit problém s oprávněními sami. Projekt by pak měl provádět následující akce:

         Nahlaste chybu uživateli tak, že zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> a vrátíte kód chyby <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    - Pokud je hodnota `VSQueryEditResult` <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a hodnota `VSQueryEditResultFlags` má <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bitovou sadu, soubor projektu by měl být rezervován voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting><xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> volání na soubor projektu způsobí, že soubor bude rezervován a bude načtena nejnovější verze, projekt je uvolněn a znovu načten. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> je volána znovu po vytvoření jiné instance projektu. Při tomto druhém volání se soubor projektu může zapsat na disk. doporučuje se, aby projekt uložil kopii souboru projektu v předchozím formátu pomocí. STARÉ rozšíření, proveďte potřebné změny upgradu a uložte soubor projektu v novém formátu. Pokud dojde k selhání jakékoli části procesu upgradu, musí metoda indikovat selhání vrácením <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. To způsobí, že se projekt uvolní v Průzkumník řešení.

     Je důležité pochopit kompletní proces, který se nachází v prostředí pro případ, kdy volání metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (určující hodnotu ReportOnly) vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a příznaky <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>.

5. Uživatel se pokusí otevřít soubor projektu.

6. Prostředí volá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementaci.

7. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> vrátí `true`, prostředí zavolá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementaci.

8. Prostředí volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> k otevření souboru a inicializaci objektu projektu, například Project1.

9. Prostředí volá vaši implementaci `IVsProjectUpgrade::UpgradeProject` k určení, zda je třeba upgradovat soubor projektu.

10. Zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předá hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> parametru `rgfQueryEdit`.

11. Prostředí vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> pro `VSQueryEditResult` a bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> je nastaven v `VSQueryEditResultFlags`.

12. Vaše implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> volá `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Toto volání může způsobit rezervaci nové kopie souboru projektu a nejnovější načtenou verzi a také nutnost opětovného načtení souboru projektu. V tomto okamžiku nastane jedna ze dvou věcí:

- Pokud zpracujete vlastní projekt znovu načtete, prostředí zavolá implementaci vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Po obdržení tohoto volání znovu načtěte první instanci projektu (Project1) a pokračujte v upgradu souboru projektu. Prostředí ví, že budete zpracovávat vlastní projekt znovu načíst, pokud vrátíte `true` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

- Pokud nezpracováváte svůj vlastní projekt opětovného načtení, vrátíte `false` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). V tomto případě, před vrácením <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits), prostředí vytvoří další novou instanci projektu, například "Project2", následovně:

    1. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> vašeho prvního objektu projektu Project1, takže tento objekt umísťuje do neaktivního stavu.

    2. Prostředí volá vaši implementaci `IVsProjectFactory::CreateProject` pro vytvoření druhé instance projektu, "Project2".

    3. Prostředí volá vaši implementaci `IPersistFileFormat::Load` k otevření souboru a inicializaci druhého objektu projektu "Project2".

    4. Prostředí volá `IVsProjectUpgrade::UpgradeProject` pro určení, zda by měl být upgradován objekt projektu. Toto volání je však provedeno na nové, druhé instanci projektu "Project2". Toto je projekt, který je otevřen v řešení.

        > [!NOTE]
        > V instanci, která je v prvním projektu Project1, je umístěn v neaktivním stavu, je nutné vrátit <xref:Microsoft.VisualStudio.VSConstants.S_OK> z prvního volání implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>.

    5. Zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předá hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> parametru `rgfQueryEdit`.

    6. Prostředí vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> a upgrade může pokračovat, protože soubor projektu lze zapsat.

Pokud se upgrade nezdaří, vraťte <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> z `IVsProjectUpgrade::UpgradeProject`. Pokud upgrade není nutný nebo pokud se rozhodnete neupgradovat, považovat `IVsProjectUpgrade::UpgradeProject` volání jako No-op. Pokud vrátíte <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, je do řešení pro váš projekt přidán zástupný uzel.

## <a name="upgrading-project-items"></a>Upgrade položek projektu

Pokud přidáte nebo spravujete položky v rámci projektové systémy, které neimplementujete, může být nutné se zapojit do procesu upgradu projektu. Crystal Reports je příkladem položky, kterou lze přidat do systému projektu.

Implementací položek projektu obvykle chtějí využít již plně sestavený a upgradovaný projekt, protože potřebují znát, co jsou odkazy na projekt a jaké další vlastnosti projektu jsou k dispozici pro rozhodnutí o upgradu.

### <a name="to-get-the-project-upgrade-notification"></a>Získání oznámení o upgradu projektu

1. Nastavte příznak <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> (definovaný v souboru vsshell80. idl) v implementaci položky projektu. To způsobí, že se položka projektu VSPackage automaticky načte, když prostředí Visual Studio zjistí, že systém projektu je v procesu upgradu.

2. Pomocí metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> poraďte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> rozhraní.

3. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> se aktivuje poté, co implementace systému projektu dokončí operace upgradu a vytvoří se nový upgradovaný projekt. V závislosti na scénáři je rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> vyvolána za <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metody.

### <a name="to-upgrade-the-project-item-files"></a>Upgrade souborů položek projektu

1. Je nutné pečlivě spravovat proces zálohování souborů v implementaci položky projektu. To platí zejména pro souběžné zálohování, kde parametr `fUpgradeFlag` metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> je nastaven na <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, kde jsou umístěné soubory, které byly zálohovány, umístěné společně se soubory, které jsou označeny jako ". old". Zálohované soubory starší než systémový čas, kdy byl projekt upgradován, mohou být označeny jako zastaralé. Kromě toho mohou být přepsány, Pokud neprovedete konkrétní kroky k tomu, aby se zabránilo.

2. V okamžiku, kdy položka projektu získá oznámení o upgradu projektu, je stále zobrazen **Průvodce převodem sady Visual Studio** . Proto byste měli použít metody rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> k poskytnutí zpráv upgradu do uživatelského rozhraní průvodce.

## <a name="see-also"></a>Viz také:

- [Projekty](../../extensibility/internals/projects.md)
