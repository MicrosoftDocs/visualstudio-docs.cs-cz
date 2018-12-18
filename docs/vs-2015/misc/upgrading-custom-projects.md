---
title: Upgrade projektů vlastní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 12b99770a7ab884e077ad6ba051a35d6e5316a49
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844676"
---
# <a name="upgrading-custom-projects"></a>Upgrade vlastních projektů
Pokud změníte informací uchovávaných v souboru projektu mezi různými verzemi sady Visual Studio, produktu, je nutné pro podporu upgradu váš soubor projektu ze staré na novou verzi. Pro podporu upgradu, která umožňuje vás k účasti **Průvodce převodu Visual Studio**, implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní. Toto rozhraní obsahuje pouze mechanismus k dispozici pro upgrade kopírování. Upgrade projektu se stane, jako součást řešení otevře. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Rozhraní je implementováno objekt pro vytváření projektu, nebo by měl být dosažitelný alespoň z objekt pro vytváření projektu.  
  
 Staré mechanismus, který používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> rozhraní je stále podporovány, ale koncepčně upgraduje systém projektu jako součást po otevření projektu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Rozhraní je tedy volána [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředí, i když <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> je volána nebo implementované rozhraní. Tento přístup umožňuje používat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> implementovat kopii projektu pouze části upgradu a delegujte zbývající práce, která musí provést na místě (případně na nové umístění) pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> rozhraní.  
  
 Pro ukázková implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, naleznete v tématu [VSSDK ukázky](../misc/vssdk-samples.md).  
  
 Následujících scénářích vznikají s upgradem projektu:  
  
-   Pokud je soubor formátu novější, než může zajistit projektu, se musí vrátit chybu s informacemi o tom to. Předpokladem je, že starší verzi produktu, například Visual Studio .NET 2003 – obsahuje kód pro kontrolu verze.  
  
-   Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> zadán příznak v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody upgradu bude možné implementovat jako upgrade v místě před počáteční projekt.  
  
-   Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> zadán příznak v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metoda, upgrade je implementovaný jako upgradu na kopii.  
  
-   Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> zadán příznak v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání, pak uživatel je vyzván prostředím upgrade souboru projektu jako místní upgrade, po otevření projektu. Například prostředí se zobrazí výzva k upgradu, když uživatel otevře starší verzi řešení.  
  
-   Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> příznak není zadán v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání, pak musí požádat uživatele upgrade souboru projektu.  
  
     Tady je ukázková zpráva upgradu příkazový řádek:  
  
     "Projekt '%1' byl vytvořen starší verzí sady Visual Studio. Když jej otevřete s touto verzí sady Visual Studio, nemusí být možné otevřít ve starších verzích sady Visual Studio. Opravdu chcete pokračovat a otevřít tento projekt?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>K implementaci IVsProjectUpgradeViaFactory  
  
1.  Implementovat metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní speciálně <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodu ve vaší implementaci objekt pro vytváření projektu, nebo učiňte implementace volat z vašeho projektu implementace objektu factory.  
  
2.  Pokud chcete provést místní upgrade jako součást řešení, otevření, zadat příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametr ve vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementace.  
  
3.  Pokud chcete provést místní upgrade jako součást řešení, otevření, zadat příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametr ve vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementace.  
  
4.  Pro oba kroky 2 a 3, skutečný soubor upgradovat kroky, pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, je možné implementovat, jak je popsáno v "implementace `IVsProjectUpgade`" níže v části, nebo můžete delegovat skutečný soubor inovace <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Použití metod pro posunutí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> účtovat inovace související zprávy pro uživatele pomocí Průvodce migrací sady Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> rozhraní se používá k implementaci jakýkoli druh upgradu souboru, který potřebuje provést jako součást upgradu projektu. Toto rozhraní není volána z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ale je poskytnut jako mechanismus pro upgradování souborů, které jsou součástí systém projektu, ale systém hlavní projekt nemusí být přímo vědět. Například této situaci může dojít, pokud nejsou stejné vývojovým týmem, který zpracovává rest systém projektu zpracovává soubory a vlastnosti související s kompilátor.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementace IVsProjectUpgrade  
 Pokud váš systém projektu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> pouze, se nemůže účastnit **Průvodce převodu Visual Studio**. Nicméně i v případě, že implementujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní, můžete stále delegovat upgrade souboru na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementace.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>K implementaci IVsProjectUpgrade  
  
1. Když se uživatel pokusí otevřít projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda je volána metodou prostředí po otevření projektu a před žádný jiný uživatel můžete provést akce na projektu. Pokud uživatel měl byl již výzva k upgradu řešení, pak bude <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> příznak je předáno `grfUpgradeFlags` parametru. Pokud uživatel otevře projekt přímo, takový tak, jak pomocí **přidat existující projekt** příkaz, pak bude <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> příznak nebude zadán, využije a projekt musí zobrazit výzvu uživateli pro upgrade.  
  
2. V reakci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání, projekt musí být vyhodnocen, zda soubor projektu se upgraduje. Pokud projekt není nutné upgradovat projekt na novou verzi, pak můžete jednoduše vrátit <xref:Microsoft.VisualStudio.VSConstants.S_OK> příznak.  
  
3. Pokud projekt je potřeba upgradovat projekt na novou verzi, pak musíte určit, zda soubor projektu je možné upravovat prostřednictvím volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metoda a předání hodnotou <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pro `rgfQueryEdit` parametru. Projekt se pak musí provést následující kroky:  
  
   -   Pokud `VSQueryEditResult` hodnotu vrácenou v `pfEditCanceled` parametr je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, pak upgradu můžete pokračovat, protože soubor projektu lze zapsat.  
  
   -   Pokud `VSQueryEditResult` hodnotu vrácenou v `pfEditCanceled` parametr je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a `VSQueryEditResult` má hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit sady, pak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musí, vrátí hodnotu neúspěch, protože uživatelé by se měly vyřešit oprávnění vydat sami. Projekt by potom postupujte takto:  
  
        Ohlaste chybu uživatele voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. a vraťte se <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> kód chyby <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
   -   Pokud `VSQueryEditResult` hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a `VSQueryEditResultFlags` má hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit sady, pak soubor projektu by měl být rezervován voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> volání v souboru projektu způsobí, že soubor, který má být rezervován a nejnovější verzi, která se má načíst a potom projekt a projekt znovu načíst. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Metoda je volána znovu, jakmile se vytvoří další instance projektu. V této druhé volání lze zapsat soubor projektu na disk. doporučuje se, že projekt uložení kopie souboru projektu ve starším formátu s. PŮVODNÍ rozšíření, proveďte jeho upgrade potřebné změny a uložte soubor projektu v novém formátu. Znovu, pokud libovolná součást procesu upgradu se nezdaří, metoda musíte uvést selhání tak, že vrací <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. To způsobí, že projekt tak, aby nenačte v Průzkumníkovi řešení.  
  
    Je důležité pochopit, dokončení procesu, který se nachází v prostředí pro případ, ve kterém volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> – metoda (zadáte třeba hodnotu jen) vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> příznaky.  
  
5. Uživatel se pokusí otevřít soubor projektu.  
  
6. Prostředí volá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementace.  
  
7. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> vrátí `true`, pak volání prostředí vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementace.  
  
8. Prostředí volá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementace otevřete soubor a inicializovat objekt projektu, například Project1.  
  
9. Prostředí volá vaši `IVsProjectUpgrade::UpgradeProject` implementace k určení, zda soubor projektu je potřeba upgradovat.  
  
10. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předejte hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pro `rgfQueryEdit` parametru.  
  
11. Vrátí prostředí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> pro `VSQueryEditResult` a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit nastaven `VSQueryEditResultFlags`.  
  
12. Vaše <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> volání implementace `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
    Toto volání může způsobit, že novou kopii souboru projektu jej rezervovat a načíst nejnovější verzi, a také potřeba znovu načíst soubor projektu. V tomto okamžiku jeden ze dvou kroků situace:  
  
- Pokud je zpracovat vlastní opakované načtení projektu, pak prostředí volá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementace (VSITEMID_ROOT). Když obdržíte toto volání, znovu načíst první instance vašeho projektu (Project1) a pokračovat v upgradu souboru projektu. Prostředí ví zpracování vlastní opakované načtení projektu, pokud se vrátíte `true` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
- Pokud nezpracovávají vlastní opakované načtení projektu, pak se vrátit `false` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). V takovém případě před <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) vrátí prostředí vytvoří další nové, instance projektu, například "project2" jako následující:  
  
  1.  Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> na váš první projekt objekt, Project1, tedy umístit tento objekt v neaktivním stavu.  
  
  2.  Prostředí volá vaši `IVsProjectFactory::CreateProject` implementace vytvořit druhou instanci projektu "project2".  
  
  3.  Prostředí volá vaši `IPersistFileFormat::Load` implementace otevřete soubor a inicializovat druhý objekt projektu "project2".  
  
  4.  Prostředí volá `IVsProjectUpgrade::UpgradeProject` podruhé k určení, zda objekt projektu by měl upgradovat. Ale tento přišla na nový, druhé instance projektu "project2". Jedná se o projekt, který je v řešení otevřen.  
  
      > [!NOTE]
      >  V instanci, která svůj první projekt Project1, se umístí do neaktivního stavu, pak musí vracet <xref:Microsoft.VisualStudio.VSConstants.S_OK> z prvního volání vaše <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementace. Zobrazit [základního projektu](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) implementace `IVsProjectUpgrade::UpgradeProject`.  
  
  5.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předejte hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pro `rgfQueryEdit` parametru.  
  
  6.  Vrátí prostředí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a upgradu můžete pokračovat, protože soubor projektu lze zapsat.  
  
  Pokud chcete upgradovat, vrátí <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> z `IVsProjectUpgrade::UpgradeProject`. Pokud žádný upgrade je nezbytné nebo jste vybrali možnost upgrade, zpracovávat `IVsProjectUpgrade::UpgradeProject` volat jako no-op. Pokud se vrátíte <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, zástupný uzel je přidán do řešení pro váš projekt.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce převodu Visual Studio](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Upgrade položky projektu](../misc/upgrading-project-items.md)   
 [Projekty](../extensibility/internals/projects.md)