---
title: Upgrade projektů | Microsoft Docs
description: Přečtěte si o rozhraních, která sada Visual Studio SDK poskytuje k implementaci podpory upgradu v projektech.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1da17c4bca485bd32aa6604b350b8af80277670
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073349"
---
# <a name="upgrading-projects"></a>Upgrade projektů

Změny modelu projektu z jedné verze sady Visual Studio na další může vyžadovat upgrade projektů a řešení, aby mohli běžet v novější verzi. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Poskytuje rozhraní, které lze použít k implementaci podpory upgradu ve vašich vlastních projektech.

## <a name="upgrade-strategies"></a>Strategie upgradu

Pro podporu upgradu musí vaše implementace systému projektu definovat a implementovat strategii upgradu. Při určování vaší strategie můžete zvolit podporu souběžného zálohování (SxS), zálohování kopírování nebo obojího.

- Záloha SxS znamená, že projekt kopíruje pouze soubory, které vyžadují upgrade, a přidává vhodné přípony názvu souboru, například ". old".

- Příkaz Kopírovat zálohu znamená, že projekt kopíruje všechny položky projektu do umístění zálohy zadaného uživatelem. Příslušné soubory v původním umístění projektu jsou poté upgradovány.

## <a name="how-upgrade-works"></a>Jak funguje upgrade

Když je řešení vytvořené v dřívější verzi sady Visual Studio otevřeno v novější verzi, rozhraní IDE zkontroluje soubor řešení a určí, jestli je potřeba upgradovat. Pokud je nutné upgradovat, **Průvodce upgradem** se automaticky spustí a provede uživatele procesem upgradu.

Když řešení vyžaduje upgrade, dotazuje se na každý objekt pro vytváření projektů pro strategii upgradu. Strategie určuje, zda objekt pro vytváření projektů podporuje zálohování kopírováním nebo SxS. Informace se odesílají do **Průvodce upgradem**, který shromažďuje informace požadované pro zálohování a prezentuje příslušné možnosti uživateli.

### <a name="multi-project-solutions"></a>Řešení s více projekty

Pokud řešení obsahuje více projektů a strategie upgradu se liší, například pokud projekt C++, který podporuje pouze zálohu SxS a webový projekt, který podporuje pouze zálohu kopírování, musí projektové továrny vyjednávat strategii upgradu.

Řešení se dotazuje na jednotlivé továrny projektu pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Pak zavolá, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> zda globální soubory projektu vyžadují upgrade, a určí podporované strategie upgradu. Pak se vyvolá **Průvodce upgradem** .

Po dokončení průvodce <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se zavolá na každý objekt pro vytváření projektu, který provede vlastní upgrade. K usnadnění zálohování metody IVsProjectUpgradeViaFactory poskytují <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> službě protokolovat podrobnosti procesu upgradu. Tuto službu nelze uložit do mezipaměti.

Po aktualizaci všech relevantních globálních souborů může každý objekt pro vytváření projektu zvolit vytvoření instance projektu. Implementace projektu musí podporovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Metoda je pak volána pro upgrade všech relevantních položek projektu.

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>Metoda neposkytuje službu SVsUpgradeLogger. Tuto službu lze získat voláním <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .

## <a name="best-practices"></a>Osvědčené postupy

Službu můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> ke kontrole, jestli soubor před úpravou nemůžete upravit, a můžete ho před uložením Uložit. To pomůže vašim implementacím zálohování a upgradu zpracovat soubory projektu v rámci správy zdrojového kódu, souborů s nedostatečnými oprávněními a tak dále.

Službu můžete používat <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> během všech fází zálohování a upgradu a poskytnout tak informace o úspěchu nebo neúspěchu procesu upgradu.

Další informace o zálohování a upgradu projektů naleznete v tématu poznámky k IVsProjectUpgrade v vsshell2. idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a> Upgrade vlastních projektů

Pokud změníte trvale uložené informace v souboru projektu mezi různými verzemi sady Visual Studio, je třeba podporovat upgrade souboru projektu z původní na novou verzi. Pro podporu upgradu, která vám umožní zúčastnit se **Průvodce převodem sady Visual Studio**, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní. Toto rozhraní obsahuje jediný mechanismus, který je k dispozici pro upgrade kopírování. Upgrade projektu se stane součástí řešení. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>Rozhraní je implementováno pomocí objektu pro vytváření projektu, nebo by mělo být z objektu pro vytváření projektu získáno nejméně.

Starý mechanismus, který používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> rozhraní, je stále podporován, ale koncepčně upgraduje systém projektu jako součást projektu otevřeného. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>Rozhraní je proto voláno prostředím sady Visual Studio i v případě, že <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> je rozhraní voláno nebo implementováno. Tento přístup umožňuje použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> k implementaci kopírování a projektu pouze částí upgradu a delegovat zbývající práci, která bude provedena místně (případně v novém umístění) <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> rozhraním.

Ukázkovou implementaci nástroje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> naleznete v tématu [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

V případě upgradu projektu se vyskytnou následující scénáře:

- Pokud je soubor v novějším formátu, než může projekt podporovat, pak musí vrátit chybu informující o tom. Předpokládá se, že starší verze produktu obsahuje kód pro kontrolu verze.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> je příznak zadán v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodě, upgrade bude implementován jako místní upgrade před otevřením projektu.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> je v metodě zadaný příznak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> , upgrade se implementuje jako upgrade pro kopírování.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> je příznak zadán ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání, pak uživatel byl vyzván v prostředí pro upgrade souboru projektu jako místní upgrade po otevření projektu. Například prostředí vyzve uživatele k upgradu, když uživatel otevře starší verzi řešení.

- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> příznak není zadán v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání, je nutné, aby uživatel vyzvat uživatele k upgradu souboru projektu.

     Následuje příklad zprávy s výzvou k upgradu:

     "Projekt" %1 "byl vytvořen ve starší verzi sady Visual Studio. Pokud jej otevřete v této verzi aplikace Visual Studio, pravděpodobně jej nebudete moci otevřít ve starších verzích sady Visual Studio. Chcete pokračovat a otevřít tento projekt? "

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Implementace IVsProjectUpgradeViaFactory

1. Implementujte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní, konkrétně <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodu v implementaci vaší továrny projektu, nebo proveďte implementace z implementace výroby projektu.

2. Pokud chcete provést místní upgrade jako součást otevírání řešení, poskytněte příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> jako `VSPUVF_FLAGS` parametr v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementaci.

3. Pokud chcete provést místní upgrade jako součást otevírání řešení, poskytněte příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> jako `VSPUVF_FLAGS` parametr v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementaci.

4. V obou krocích 2 a 3 je možné implementovat vlastní postup upgradu souborů pomocí nástroje <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> , jak je popsáno v části "implementace `IVsProjectUpgade` " níže, nebo můžete delegovat vlastní upgrade souboru na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>K publikování zpráv souvisejících s upgradem pro uživatele pomocí Průvodce migrací sady Visual Studio použijte metody.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> rozhraní se používá k implementaci jakéhokoli typu upgradu souboru, který se musí nacházet jako součást upgradu projektu. Toto rozhraní není voláno z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , ale je zadáno jako mechanismus pro upgrade souborů, které jsou součástí systému projektu, ale hlavní systém projektu nemusí být přímo vědom. Tato situace může nastat například v případě, že soubory a vlastnosti související s kompilátorem nejsou zpracovávány stejným vývojovým týmem, který zpracovává zbytek projektového systému.

### <a name="ivsprojectupgrade-implementation"></a>Implementace IVsProjectUpgrade

Pokud systém projektu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> pouze, nemůže se zúčastnit **Průvodce převodem sady Visual Studio**. Nicméně i v případě, že rozhraní implementujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , můžete i nadále delegovat upgrade souboru na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementaci.

#### <a name="to-implement-ivsprojectupgrade"></a>Implementace IVsProjectUpgrade

1. Když se uživatel pokusí otevřít projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Metoda je volána prostředím po otevření projektu a před provedením jakékoli jiné akce uživatele v projektu. Pokud uživatel již byl vyzván k upgradu řešení, pak se <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> příznak předává v `grfUpgradeFlags` parametru. Pokud uživatel otevře projekt přímo, například pomocí příkazu **Přidat existující projekt** , <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> příznak není předán a projekt musí uživateli požádat o upgrade.

2. V reakci na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání musí projekt vyhodnotit, zda je soubor projektu upgradován. Pokud projekt není potřeba upgradovat typ projektu na novou verzi, pak může jednoduše vrátit <xref:Microsoft.VisualStudio.VSConstants.S_OK> příznak.

3. Pokud projekt potřebuje upgradovat typ projektu na novou verzi, pak musí určit, zda lze soubor projektu upravit voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody a předáním hodnoty <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametru. Projekt pak musí provést následující akce:

    - Pokud `VSQueryEditResult` hodnota vrácená `pfEditCanceled` parametrem je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> , může upgrade pokračovat, protože soubor projektu lze zapsat.

    - Pokud `VSQueryEditResult` je hodnota vrácená `pfEditCanceled` parametrem <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a `VSQueryEditResult` hodnota má <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bitovou sadu, pak se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musí vrátit chyba, protože uživatelé by měli vyřešit vlastní problém s oprávněním. Projekt by pak měl provádět následující akce:

         Nahlaste chybu uživateli tak, že zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> a vrátíte <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> kód chyby <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

    - Pokud `VSQueryEditResult` hodnota je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a `VSQueryEditResultFlags` hodnota má <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bitovou sadu, soubor projektu by měl být rezervován voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits> ,...).

4. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> volání na soubor projektu způsobí, že soubor bude rezervován a bude načtena nejnovější verze, projekt je uvolněn a znovu načten. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Metoda je volána znovu po vytvoření jiné instance projektu. Při tomto druhém volání se soubor projektu může zapsat na disk. doporučuje se, aby projekt uložil kopii souboru projektu v předchozím formátu pomocí. STARÉ rozšíření, proveďte potřebné změny upgradu a uložte soubor projektu v novém formátu. Pokud dojde k selhání jakékoli části procesu upgradu, metoda musí indikovat selhání vrácením <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> . To způsobí, že se projekt uvolní v Průzkumník řešení.

     Je důležité pochopit kompletní proces, který se vyskytuje v prostředí pro případ, kdy volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody (určení hodnoty ReportOnly) vrací <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> příznaky.

5. Uživatel se pokusí otevřít soubor projektu.

6. Prostředí volá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementaci.

7. Pokud se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> vrátí `true` , prostředí zavolá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementaci.

8. Prostředí volá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementaci k otevření souboru a inicializaci objektu projektu, například Project1.

9. Prostředí volá vaši `IVsProjectUpgrade::UpgradeProject` implementaci a určí, jestli se soubor projektu musí upgradovat.

10. Zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předáte hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> `rgfQueryEdit` parametru.

11. Prostředí vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> pro `VSQueryEditResult` a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit je nastaven v `VSQueryEditResultFlags` .

12. Vaše <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementace volání `IVsQueryEditQuerySave::QueryEditFiles` ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits> ).

Toto volání může způsobit rezervaci nové kopie souboru projektu a nejnovější načtenou verzi a také nutnost opětovného načtení souboru projektu. V tomto okamžiku nastane jedna ze dvou věcí:

- Pokud zpracováváte vlastní opětovné načtení projektu, prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementaci vaší (VSITEMID_ROOT). Po obdržení tohoto volání znovu načtěte první instanci projektu (Project1) a pokračujte v upgradu souboru projektu. Prostředí ví, že při návratu `true` pro () zpracováváte vlastní opětovné načtení <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> projektu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload> .

- Pokud nezpracováváte svůj vlastní projekt opětovného načtení, vrátíte se `false` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload> ). V tomto případě, před <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> vrácením (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits), prostředí vytvoří další novou instanci projektu, například "Project2", následovně:

    1. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> svůj první objekt projektu Project1, takže tento objekt umísťuje do neaktivního stavu.

    2. Prostředí volá vaši `IVsProjectFactory::CreateProject` implementaci a vytvoří druhou instanci projektu, "Project2".

    3. Prostředí volá vaši `IPersistFileFormat::Load` implementaci k otevření souboru a inicializaci druhého objektu projektu, "Project2".

    4. Prostředí volá `IVsProjectUpgrade::UpgradeProject` určitou dobu, aby bylo možné určit, zda má být objekt projektu upgradován. Toto volání je však provedeno na nové, druhé instanci projektu "Project2". Toto je projekt, který je otevřen v řešení.

        > [!NOTE]
        > V instanci, která je v prvním projektu Project1, je umístěn v neaktivním stavu, je nutné se vrátit <xref:Microsoft.VisualStudio.VSConstants.S_OK> z prvního volání do vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementace.

    5. Zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předáte hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> `rgfQueryEdit` parametru.

    6. Prostředí se vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> a upgrade může pokračovat, protože soubor projektu lze zapsat.

Pokud se upgrade nezdaří, vraťte se <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> z `IVsProjectUpgrade::UpgradeProject` . Pokud upgrade není nutný nebo pokud se rozhodnete neupgradovat, považovat `IVsProjectUpgrade::UpgradeProject` volání za No-op. Pokud se vrátíte <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> , je do řešení pro váš projekt přidán zástupný uzel.

## <a name="upgrading-project-items"></a>Upgrade položek projektu

Pokud přidáte nebo spravujete položky v rámci projektové systémy, které neimplementujete, může být nutné se zapojit do procesu upgradu projektu. Crystal Reports je příkladem položky, kterou lze přidat do systému projektu.

Implementací položek projektu obvykle chtějí využít již plně sestavený a upgradovaný projekt, protože potřebují znát, co jsou odkazy na projekt a jaké další vlastnosti projektu jsou k dispozici pro rozhodnutí o upgradu.

### <a name="to-get-the-project-upgrade-notification"></a>Získání oznámení o upgradu projektu

1. Nastavte <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> příznak (definovaný v vsshell80. idl) v implementaci položky projektu. To způsobí, že se položka projektu VSPackage automaticky načte, když prostředí Visual Studio zjistí, že systém projektu je v procesu upgradu.

2. Poraďte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> rozhraní prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metody.

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>Rozhraní se aktivuje poté, co implementace systému projektu dokončí operace upgradu a vytvoří se nový upgradovaný projekt. V závislosti na scénáři <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> je rozhraní vyvolána za <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metodami, nebo.

### <a name="to-upgrade-the-project-item-files"></a>Upgrade souborů položek projektu

1. Je nutné pečlivě spravovat proces zálohování souborů v implementaci položky projektu. To platí zejména pro souběžné zálohování, kde `fUpgradeFlag` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody je nastaven na <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> , kde jsou umístěny soubory, které byly zálohovány společně umístěné soubory, které jsou označeny jako ". old". Zálohované soubory starší než systémový čas, kdy byl projekt upgradován, mohou být označeny jako zastaralé. Kromě toho mohou být přepsány, Pokud neprovedete konkrétní kroky k tomu, aby se zabránilo.

2. V okamžiku, kdy položka projektu získá oznámení o upgradu projektu, je stále zobrazen **Průvodce převodem sady Visual Studio** . Proto byste měli použít metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> rozhraní k poskytnutí zpráv upgradu do uživatelského rozhraní průvodce.

## <a name="see-also"></a>Viz také

- [Projekty](../../extensibility/internals/projects.md)
