---
title: Upgrade projektů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea5c29819d0035e45f97122fd108ea1f51d60806
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057527"
---
# <a name="upgrading-projects"></a>Upgrade projektů

Změny do projektu modelu z jedné verze sady Visual Studio na další můžou vyžadovat, aby projekty a řešení upgradovat tak, aby mohly běžet na novější verzi. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Poskytuje rozhraní, které lze použít k implementaci upgradu podporu ve vašich vlastních projektů.

## <a name="upgrade-strategies"></a>Strategie upgradu

Implementace systému projektu pro podporu upgradu, musíte definovat a implementovat upgradu strategie. Při určování strategie, můžete podporovat-souběžného (SxS) zálohování, zálohování kopírováním nebo obojí.

-   Zálohování SxS znamená, že projektu zkopíruje pouze soubory, které je třeba upgradovat na místě, přidávání vhodný název příponu souboru, například "old".

-   Zálohování kopírováním znamená, že projektu zkopíruje všechny položky projektu do umístění zálohy zadaný uživatelem. Příslušné soubory do původního umístění projektu jsou potom upgradovat.

## <a name="how-upgrade-works"></a>Jak upgradovat funguje

Po otevření řešení vytvořena ve starší verzi sady Visual Studio v novější verzi rozhraní IDE kontroluje soubor řešení k určení, jestli je třeba upgradovat. Je-li upgrade vyžadováno, **Průvodce upgradem** spuštěna automaticky provede uživatele prostřednictvím procesu upgradu.

Když řešení potřebuje upgrade, vyžádá si každý projektu pro vytváření pro jeho upgradu strategie. Strategie určí, zda objekt pro vytváření projektu podporuje zálohování kopírováním nebo SxS zálohování. Posílá informace **Průvodce upgradem**, který shromažďuje informace požadované pro zálohování a zobrazí příslušné možnosti s uživatele.

### <a name="multi-project-solutions"></a>Řešení vícenásobného projektu

Pokud řešení obsahuje více projektů a upgradu strategie liší, například když C++ projekt, který podporuje pouze SxS zálohování a webový projekt, který podporuje jenom zálohování kopírováním objekty pro vytváření projektů musí si vyjednat strategie upgradu.

Každý projekt objekt factory pro dotazy řešení <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Potom zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> vědět, pokud je nutné soubory globální projektu upgradu a určení podporovaných upgradu strategie. **Průvodce upgradem** potom je volána.

Po dokončení průvodce, uživatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se volá na každý vytváření projektu k provedení skutečném upgradu. Pro usnadnění zálohování, IVsProjectUpgradeViaFactory metody poskytují <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> služby do protokolu podrobnosti o procesu upgradu. Tuto službu nelze uložit do mezipaměti.

Po aktualizaci všechny relevantní soubory globální, můžete zvolit každý objekt pro vytváření projektu vytvořit instanci projektu. Implementace projektu musí podporovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Metoda je volána poté upgradovat všechny relevantní projektu položky.

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Metoda neposkytuje službu SVsUpgradeLogger. Tato služba je možné získat volání <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Doporučené postupy

Použití <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> služby zkontrolujte, zda můžete upravit soubor před úpravou ho a můžete ho uložit před uložením. To vám pomůže zálohování a upgradu implementace zpracování souborů projektu ve správě zdrojového kódu, soubory s nedostatečná oprávnění a tak dále.

Použití <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> služby během fáze všechny zálohy a upgradujte poskytnout informace o úspěch nebo selhání procesu upgradu.

Další informace o zálohování a upgrade projektů naleznete v tématu komentáře IVsProjectUpgrade v vsshell2.idl.

## <a name="upgrading-custom-projects"></a> Upgrade vlastních projektů

Pokud změníte informace jako trvalý v souboru projektu mezi různými verzemi sady Visual Studio produktu a potom budete potřebovat k podpoře upgrade souboru projektu ze starého na nové verze. Pro podporu upgradu, který umožňuje účastnit **Průvodce převodu Visual Studio**, implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní. Toto rozhraní obsahuje pouze mechanismus k dispozici pro upgrade kopírování. Upgrade projektu se stane, jako součást řešení otevře. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Rozhraní je implementováno modulem objektu pro vytváření projektu nebo by měla být dosažitelný alespoň z objektu pro vytváření projektu.

Původní mechanismus, který používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> rozhraní se pořád podporuje, ale koncepčně upgraduje projektu systém jako součást otevřít projekt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Proto volá rozhraní prostředí sady Visual Studio, i když <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní je volána nebo implementovat. Tento přístup umožňuje používat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> k implementaci kopie a pouze části upgrade projektu a delegovat zbývající práce provést na místě (případně na nové umístění) pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> rozhraní.

Pro příklad implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, najdete v části [VSSDK ukázky](http://aka.ms/vs2015sdksamples).

Následující scénáře jsou vyvolány s upgradem projektu:

-   Pokud je soubor novější formátu, než může podporovat projekt, pak musí vracet chyba oznamující to. Předpokladem je, že starší verzi produktu, obsahuje kód ke kontrole pro verzi.

-   Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> příznak je uveden v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody upgradu přechází k implementaci jako místní upgrade před otevření projektu.

-   Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> příznak je uveden v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metoda, upgrade je implementovaný jako kopírování upgradu.

-   Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> příznak je uveden v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volat, pak uživatel má prostředí vyzván k upgradu souboru projektu jako místní upgrade, po otevření projektu. Například prostředí vyzývá uživatele k upgradu, když uživatel otevře starší verzi řešení.

-   Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> příznak není zadané v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volat, pak musí vyzvat uživatele k upgradu souboru projektu.

     Příklad upgradu výzva zpráva je následující:

     "'%1: vytvoření projektu ze starší verze sady Visual Studio. Pokud otevřete s touto verzí sady Visual Studio, nemusí být schopni otevřít se staršími verzemi sady Visual Studio. Opravdu chcete pokračovat a otevřít tento projekt?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>K implementaci IVsProjectUpgradeViaFactory

1.  Implementovat metodu, jakou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní, konkrétně <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metoda v implementaci objekt pro vytváření projektu nebo zkontrolujte implementace, kterou lze volat z vaší implementace objektu pro vytváření projektu.

2.  Pokud chcete provést upgrade na místě jako součást řešení, otevření, zadejte příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> jako `VSPUVF_FLAGS` parametr ve vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementace.

3.  Pokud chcete provést upgrade na místě jako součást řešení, otevření, zadejte příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> jako `VSPUVF_FLAGS` parametr ve vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementace.

4.  Oba kroky 2 a 3, skutečný soubor upgrade kroky, pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, můžete implementovat, jak je popsáno v "implementace `IVsProjectUpgade`" části níže, nebo můžete delegovat upgrade skutečný soubor <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5.  Použít metody třídy <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> odeslat upgrade související zprávy pro uživatele pomocí Průvodce migrací Visual Studio.

6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> rozhraní se používá k implementaci jakýkoli druh upgrade souboru, který je potřeba v rámci upgradu projektu. Toto rozhraní není volat z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ale je zadaná jako mechanismus pro upgrade soubory, které jsou součástí systému projektu, ale hlavní projekt systému nemusí být přímo vědět. Například této situaci může dojít, pokud kompilátor související soubory a vlastnosti nejsou zpracovány pomocí stejné vývojový tým, který zpracovává zbytek systému projektu.

### <a name="ivsprojectupgrade-implementation"></a>Implementace IVsProjectUpgrade

Pokud váš systém projektu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> pouze se nemůže účastnit **Průvodce převodu Visual Studio**. Ale i v případě, že budete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní, můžete stále delegovat upgrade souboru na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementace.

#### <a name="to-implement-ivsprojectupgrade"></a>K implementaci IVsProjectUpgrade

1.  Když se uživatel pokusí otevřít projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda je volána prostředí po otevření projektu a před jiný uživatel může být provedena akce na projekt. Pokud uživatel měl byl již výzva k upgradu řešení, pak se <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> příznak, je předaná `grfUpgradeFlags` parametr. Pokud uživatel otevře projektu přímo, takové jako pomocí **přidat existující projekt** příkazu, pak se <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> příznak není předán a projekt musí vyzvat uživatele k upgradu.

2.  V reakci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání projektu musí vyhodnocení, zda je upgrade souboru projektu. Pokud projekt není nutné upgradovat typ projektu na novou verzi, pak můžete jednoduše vrátit <xref:Microsoft.VisualStudio.VSConstants.S_OK> příznak.

3.  Pokud projekt je potřeba upgradovat typ projektu na novou verzi, pak musíte určit, zda soubor projektu lze upravovat voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metoda a předávání hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pro `rgfQueryEdit` parametr. Projekt, je třeba provést následující:

    -   Pokud `VSQueryEditResult` hodnota vrácená v `pfEditCanceled` parametr <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, pak upgradu můžete pokračovat, protože soubor projektu lze zapisovat.

    -   Pokud `VSQueryEditResult` hodnota vrácená v `pfEditCanceled` parametr je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a `VSQueryEditResult` má hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> nastaven, pak bit <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musí vracet selhání, protože uživatelé měli vyřešit oprávnění vydat sami. Projekt by měl potom postupujte takto:

         Ohlaste chybu uživatele voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> a vrátíte se <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> kódu chyby <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    -   Pokud `VSQueryEditResult` hodnota je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a `VSQueryEditResultFlags` má hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> nastaven, pak by měl být rezervována souboru projektu voláním bit <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4.  Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> volání v souboru projektu způsobí, že soubor rezervaci a mají být načteny na nejnovější verzi a potom je odpojeno a znovu načíst projekt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Metoda je volána znovu po vytvoření jiná instance projektu. V této druhé volání, je možné soubor projektu zapsat na disk; Doporučujeme, aby projekt uložení kopie souboru projektu v předchozí formátu s. PŮVODNÍ rozšíření, proveďte její upgrade změny a uložte soubor projektu v novém formátu. Znovu, pokud libovolná součást procesu upgradu selže, metodu musí označovat selhání vrácením <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. To způsobí, že projekt, který má být uvolněn v Průzkumníku řešení.

     Je důležité si uvědomit, k níž dojde v prostředí pro případ, ve kterém proces dokončení volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (zadáte třeba hodnotu ReportOnly) metoda vrátí hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> příznaky.

5.  Uživatel se pokusí otevřít soubor projektu.

6.  Volání prostředí vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementace.

7.  Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> vrátí `true`, pak volání prostředí vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementace.

8.  Volání prostředí vaší <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementace otevřete soubor a inicializovat objekt projektu, například Project1.

9. Volání prostředí vaší `IVsProjectUpgrade::UpgradeProject` implementace k určení, zda soubor projektu musí být upgradován.

10. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předejte hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> pro `rgfQueryEdit` parametr.

11. Vrátí prostředí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> pro `VSQueryEditResult` a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> je v nastaven bit `VSQueryEditResultFlags`.

12. Vaše <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementace volá `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Toto volání může způsobit, že o novou kopii tohoto souboru projektu rezervaci a načíst nejnovější verzi, a také potřeba znovu načíst soubor projektu. V tomto okamžiku dvě situace:

-   Pokud zpracováváte vlastní znovu načíst projekt, pak prostředí zavolá váš <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementace (VSITEMID_ROOT). Jakmile se zobrazí toto volání, načtěte první instance projektu (Project1) a pokračovat v upgradu souboru projektu. Prostředí zná zpracování vlastní opětovného načtení projektu, pokud se vrátíte `true` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

-   Pokud nezpracuje vlastní znovu načíst projekt, pak se vraťte `false` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). V takovém případě před <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) vrátí prostředí vytvoří novou instanci jiného projektu, například projektu2 následujícím způsobem:

    1.  Volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> na vaše první objekt projektu Project1, proto umístění tohoto objektu v neaktivním stavu.

    2.  Volání prostředí vaší `IVsProjectFactory::CreateProject` implementace vytvořit druhou instanci projektu projektu2.

    3.  Volání prostředí vaší `IPersistFileFormat::Load` implementace otevřete soubor a druhý objekt projektu projektu2 inicializovat.

    4.  Volání prostředí `IVsProjectUpgrade::UpgradeProject` pro podruhé k určení, zda je potřeba upgradovat objekt projektu. Však tento přišla na nové, druhé instanci projektu, projektu2. Toto je projekt, který je otevřen v řešení.

        > [!NOTE]
        > V instanci, která svůj první projekt Project1, je umístěn v neaktivním stavu, pak musí vracet <xref:Microsoft.VisualStudio.VSConstants.S_OK> z první volání vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementace.

    5.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předejte hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> pro `rgfQueryEdit` parametr.

    6.  Vrátí prostředí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> a upgradu můžete pokračovat, protože soubor projektu lze zapisovat.

Pokud jste upgrade se nezdařil, vrátí <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> z `IVsProjectUpgrade::UpgradeProject`. Pokud žádné upgradu je nutné nebo rozhodnete-li upgradovat, považovat `IVsProjectUpgrade::UpgradeProject` volání jako no-op. Pokud vrátíte <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, zástupný symbol uzlu je přidán do řešení pro váš projekt.

## <a name="upgrading-project-items"></a>Upgrade položky projektu

Pokud přidáte nebo spravovat položky v rámci projektu systémů, které jste neimplementují, musíte k účasti v procesu upgradu projektu. Crystal Reports je příkladem položku, která mohou být přidány do systému projektu.

Obvykle implementátory položky projektu chtějí využít projekt již plně instancí a upgradovali, protože musí vědět, jaké jsou odkazy na projekt a co další vlastnosti projektu existují provést upgrade rozhodnutí.

### <a name="to-get-the-project-upgrade-notification"></a>Chcete-li získat oznámení upgrade projektu

1.  Nastavte <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> příznak (definovanou v vsshell80.idl) ve vaší implementace položky projektu. To způsobí, že vaše položka projektu VSPackage pro automatické zatížení při prostředí sady Visual Studio Určuje, že probíhá upgrade systému projektu.

2.  Poradit <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> rozhraní prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metoda.

3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Rozhraní je aktivováno po dokončení upgradu operací implementace systému projektu a je vytvořen nový projekt upgradovaný. V závislosti na scénáři <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> rozhraní je aktivováno po <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metody.

### <a name="to-upgrade-the-project-item-files"></a>Upgrade souborů položek projektu

1.  Proces zálohování souboru musí spravovat pečlivě v implementaci položky projektu. To platí především pro vytvoření zálohy vedle sebe, kde `fUpgradeFlag` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> je nastavena metoda <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, kde jsou umístěny soubory, které se měl zálohovat podél straně soubory, které jsou označeny jako "old". Zálohované soubory starší než systémový čas, kdy byl upgradován projektu, může být označeno jako zastaralé. Kromě toho se může být přepsána není-li provést určité kroky k tomu zabránit.

2.  V době položky projektu získá oznámení o upgrade projektu **Průvodce převodu Visual Studio** zobrazena i. Proto měli používat metody třídy <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> rozhraní zajistit upgradu zprávy do průvodce uživatelské rozhraní.

## <a name="see-also"></a>Viz také:

- [Projekty](../../extensibility/internals/projects.md)