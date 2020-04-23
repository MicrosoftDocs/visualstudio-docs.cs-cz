---
title: Inovace vlastních projektů | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: c91013e7d5650e82fd9e5f6e39e28c4609e4fbfe
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037204"
---
# <a name="upgrading-custom-projects"></a>Inovace vlastních projektů
Pokud změníte informace trvalé v souboru projektu mezi různými verzemi sady Visual Studio produktu, budete muset podporovat upgrade souboru projektu ze staré na novou verzi. Chcete-li podporovat inovaci, která umožňuje účast v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> **Průvodci převodem sady Visual Studio**, implementujte rozhraní. Toto rozhraní obsahuje jediný mechanismus, který je k dispozici pro upgrade kopie. Upgrade projektu se stane jako součást řešení otevře. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> je implementováno factory projektu, nebo by měly být alespoň získat z továrny projektu.  
  
 Starý mechanismus, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> který používá rozhraní je stále podporována, ale koncepčně upgraduje systém projektu jako součást projektu otevřít. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> je proto volána prostředí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> i v případě, že rozhraní je volána nebo implementována. Tento přístup umožňuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> použít k implementaci kopie a projekt pouze části upgradu a delegovat zbytek práce, které mají <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> být provedeny na místě (případně v novém umístění) rozhraním.  
  
 Ukázková implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>aplikace naleznete [v tématu VSSDK Samples](../misc/vssdk-samples.md).  
  
 Následující scénáře vznikají s upgrady projektu:  
  
- Pokud je soubor novějšího formátu, než může projekt podporovat, musí vrátit chybu s uvedením tohoto. To předpokládá, že starší verze produktu , například Visual Studio .NET 2003 , obsahuje kód pro kontrolu verze.  
  
- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> je příznak zadán <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> v metodě, upgrade bude implementován jako inovace na místě před otevřením projektu.  
  
- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> je příznak zadán <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> v metodě, upgrade je implementován jako upgrade kopie.  
  
- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> je příznak zadán <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> ve volání, pak byl uživatel vyzván prostředím k upgradu souboru projektu jako inovace na místě po otevření projektu. Prostředí například vyzve uživatele k upgradu, když uživatel otevře starší verzi řešení.  
  
- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> příznak není zadán <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> ve volání, musíte vyzvat uživatele k upgradu souboru projektu.  
  
     Následuje ukázková zpráva s výzvou k upgradu:  
  
     "Projekt '%1' byl vytvořen se starší verzí sady Visual Studio. Pokud jej otevřete pomocí této verze sady Visual Studio, pravděpodobně ji nebudete moci otevřít se staršími verzemi sady Visual Studio. Chcete pokračovat a otevřít tento projekt?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Implementace IVsProjectUpgradeViaFactory  
  
1. Implementujte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> konkrétně metodu v implementaci projektu z výroby nebo proveďte implementace volatelné z implementace továrny projektu.  
  
2. Pokud chcete provést upgrade na místě jako součást otevření řešení, <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> zadejte `VSPUVF_FLAGS` příznak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jako parametr v implementaci.  
  
3. Pokud chcete provést upgrade na místě jako součást otevření řešení, <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> zadejte `VSPUVF_FLAGS` příznak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jako parametr v implementaci.  
  
4. Pro kroky 2 a 3 lze implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>skutečné kroky upgradu souboru pomocí `IVsProjectUpgade`aplikace , jak je popsáno v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>části Implementace , nebo můžete delegovat skutečný upgrade souboru na .  
  
5. Metody odeslání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> souvisejících zpráv o upgradu pro uživatele pomocí Průvodce migrací sady Visual Studio.  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>rozhraní se používá k implementaci jakéhokoli druhu upgradu souboru, který se musí stát v rámci upgradu projektu. Toto rozhraní není <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>volána z aplikace , ale je dodávánjako mechanismus pro upgrade souborů, které jsou součástí systému projektu, ale hlavní systém projektu nemusí být přímo vědomi. Například tato situace může nastat, pokud soubory a vlastnosti související s kompilátorem nejsou zpracovány stejným vývojovým týmem, který zpracovává zbytek systému projektu.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementace upgradu projektu IVsProject  
 Pokud systém projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementuje pouze, nemůže se účastnit **Průvodce převodem sady Visual Studio**. Však i v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> případě, že implementovat rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> můžete stále delegovat upgrade souboru na implementaci.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Implementace iVsProjectUpgrade  
  
1. Když se uživatel pokusí otevřít projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda je volána prostředí po otevření projektu a před jakoukoli jinou akci uživatele může být provedena v projektu. Pokud uživatel již byla vyzvána k upgradu <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> řešení, pak `grfUpgradeFlags` příznak je předán v parametru. Pokud uživatel otevře projekt přímo, například pomocí příkazu Přidat <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> existující **projekt,** příznak není předán a projekt musí vyzvat uživatele k upgradu.  
  
2. V reakci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> na volání musí projekt vyhodnotit, zda je soubor projektu upgradován. Pokud projekt není nutné upgradovat typ projektu na novou verzi, <xref:Microsoft.VisualStudio.VSConstants.S_OK> pak může jednoduše vrátit příznak.  
  
3. Pokud projekt potřebuje upgradovat typ projektu na novou verzi, musí určit, zda soubor <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> projektu lze změnit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> voláním `rgfQueryEdit` metody a předáním hodnoty parametru. Projekt pak musí provést následující kroky:  
  
   - Pokud `VSQueryEditResult` je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>hodnota `pfEditCanceled` vrácená v parametru , může inovace pokračovat, protože soubor projektu může být zapsán.  
  
   - Pokud `VSQueryEditResult` `pfEditCanceled` je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> hodnota vrácená v `VSQueryEditResult` parametru <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> a hodnota <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> má nastavený bit, musí vrátit selhání, protože uživatelé by měli vyřešit problém oprávnění sami. Projekt by pak měl provést následující kroky:  
  
        Oznamte chybu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>uživateli voláním . a vrátí <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> kód <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>chyby na .  
  
   - Pokud `VSQueryEditResult` je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> hodnota `VSQueryEditResultFlags` a hodnota <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> má nastavený bit, pak soubor projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>by <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>měl být rezervován voláním ( , ,...).  
  
4. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> volání souboru projektu způsobí, že soubor má být rezervován a nejnovější verze, které mají být načteny, pak je projekt uvolněn a znovu načten. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> je volána znovu, jakmile je vytvořena jiná instance projektu. Při tomto druhém volání lze soubor projektu zapsat na disk; doporučujeme, aby projekt uložil kopii souboru projektu v předchozím formátu s . OLD příponu, proveďte potřebné změny upgradu a uložte soubor projektu v novém formátu. Opět platí, že pokud se nezdaří některá část <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>procesu upgradu, musí metoda indikovat selhání vrácením . To způsobí, že projekt má být uvolněnv Průzkumníka řešení.  
  
    Je důležité pochopit celý proces, ke kterému dochází v prostředí pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> případ, ve kterém volání metody (zadání hodnoty ReportOnly) vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> příznaky.  
  
5. Uživatel se pokusí otevřít soubor projektu.  
  
6. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementaci.  
  
7. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true`vrátí , pak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> prostředí volá implementaci.  
  
8. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementaci k otevření souboru a inicializaci objektu projektu, například Project1.  
  
9. Prostředí volá `IVsProjectUpgrade::UpgradeProject` implementaci k určení, zda je třeba upgradovat soubor projektu.  
  
10. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předání hodnoty <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> parametru. `rgfQueryEdit`  
  
11. Prostředí se <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> `VSQueryEditResult` vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> a bit `VSQueryEditResultFlags`je nastaven v .  
  
12. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementace `IVsQueryEditQuerySave::QueryEditFiles` <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, ).  
  
    Toto volání může způsobit novou kopii souboru projektu, které mají být rezervovány a nejnovější verze načtena, stejně jako potřeba znovu načíst soubor projektu. V tomto okamžiku se stane jedna ze dvou věcí:  
  
- Pokud zpracovat vlastní projekt znovu načíst, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> pak prostředí volá (VSITEMID_ROOT) implementace. Po přijetí tohoto volání znovu načtěte první instanci projektu (Project1) a pokračujte v inovaci souboru projektu. Prostředí ví, že zpracovat vlastní projekt `true` znovu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>načíst, pokud se vrátíte pro ( ).  
  
- Pokud nezvládáte vlastní projekt znovu `false` načíst, pak se vrátíte pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). V tomto případě <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>před ([QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags),) vrátí, prostředí vytvoří další novou, instanci projektu, například Project2, takto:  
  
  1. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> na první objekt projektu Project1, a tím umístit tento objekt do neaktivního stavu.  
  
  2. Prostředí volá `IVsProjectFactory::CreateProject` implementaci k vytvoření druhé instance projektu Project2.  
  
  3. Prostředí volá `IPersistFileFormat::Load` implementaci k otevření souboru a inicializaci druhého objektu projektu Project2.  
  
  4. Prostředí volá `IVsProjectUpgrade::UpgradeProject` podruhé k určení, zda má být upgradován objekt projektu. Toto volání je však na nové, second, instance projektu Project2. Toto je projekt, který je otevřen v řešení.  
  
      > [!NOTE]
      > V případě, že váš první projekt, Project1, je umístěn v <xref:Microsoft.VisualStudio.VSConstants.S_OK> neaktivním stavu, pak se musíte vrátit z první volání do implementace. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Viz [Základní projekt](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) pro `IVsProjectUpgrade::UpgradeProject`implementaci .  
  
  5. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předání hodnoty <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> parametru. `rgfQueryEdit`  
  
  6. Prostředí se <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> vrátí a upgrade může pokračovat, protože soubor projektu lze zapsat.  
  
  Pokud se vám nepodaří inovovat, vraťte se <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> z . `IVsProjectUpgrade::UpgradeProject` Pokud není nutný žádný upgrade nebo se `IVsProjectUpgrade::UpgradeProject` rozhodnete neupgradovat, považovat volání za no-op. Pokud vrátíte <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, zástupný uzel je přidán do řešení pro váš projekt.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce převodem sady Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Inovace položek projektu](../misc/upgrading-project-items.md)   
 [Projekty](../extensibility/internals/projects.md)