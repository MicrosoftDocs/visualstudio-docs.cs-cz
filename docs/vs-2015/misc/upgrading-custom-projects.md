---
title: Upgrade vlastních projektů | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037204"
---
# <a name="upgrading-custom-projects"></a>Upgrade vlastních projektů
Pokud změníte trvale uložené informace v souboru projektu mezi různými verzemi sady Visual Studio, je třeba podporovat upgrade souboru projektu z původní na novou verzi. Pro podporu upgradu, která vám umožní zúčastnit se **Průvodce převodem sady Visual Studio**, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní. Toto rozhraní obsahuje jediný mechanismus, který je k dispozici pro upgrade kopírování. Upgrade projektu se stane součástí řešení. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>Rozhraní je implementováno pomocí objektu pro vytváření projektu, nebo by mělo být z objektu pro vytváření projektu získáno nejméně.  
  
 Starý mechanismus, který používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> rozhraní, je stále podporován, ale koncepčně upgraduje systém projektu jako součást projektu otevřeného. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>Rozhraní je proto voláno [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředím i v případě, že <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> je rozhraní voláno nebo implementováno. Tento přístup umožňuje použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> k implementaci kopírování a projektu pouze částí upgradu a delegovat zbývající práci, která bude provedena místně (případně v novém umístění) <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> rozhraním.  
  
 Ukázkovou implementaci nástroje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> naleznete v tématu [VSSDK Samples](../misc/vssdk-samples.md).  
  
 V případě upgradu projektu se vyskytnou následující scénáře:  
  
- Pokud je soubor v novějším formátu, než může projekt podporovat, pak musí vrátit chybu informující o tom. Předpokládá se, že starší verze vašeho produktu, například Visual Studio .NET 2003 – obsahuje kód pro kontrolu verze.  
  
- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> je příznak zadán v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodě, upgrade bude implementován jako místní upgrade před otevřením projektu.  
  
- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> je v metodě zadaný příznak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> , upgrade se implementuje jako upgrade pro kopírování.  
  
- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> je příznak zadán ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání, pak uživatel byl vyzván v prostředí pro upgrade souboru projektu jako místní upgrade po otevření projektu. Například prostředí vyzve uživatele k upgradu, když uživatel otevře starší verzi řešení.  
  
- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> příznak není zadán v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání, je nutné, aby uživatel vyzvat uživatele k upgradu souboru projektu.  
  
     Následuje příklad zprávy s výzvou k upgradu:  
  
     "Projekt" %1 "byl vytvořen ve starší verzi sady Visual Studio. Pokud jej otevřete v této verzi aplikace Visual Studio, pravděpodobně jej nebudete moci otevřít ve starších verzích sady Visual Studio. Chcete pokračovat a otevřít tento projekt? "  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Implementace IVsProjectUpgradeViaFactory  
  
1. Implementujte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> rozhraní, konkrétně <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodu v implementaci vaší továrny projektu, nebo proveďte implementace z implementace výroby projektu.  
  
2. Pokud chcete provést místní upgrade jako součást otevírání řešení, poskytněte příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametr v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementaci.  
  
3. Pokud chcete provést místní upgrade jako součást otevírání řešení, poskytněte příznak <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametr v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementaci.  
  
4. V obou krocích 2 a 3 je možné implementovat vlastní postup upgradu souborů pomocí nástroje <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> , jak je popsáno v části "implementace `IVsProjectUpgade` " níže, nebo můžete delegovat vlastní upgrade souboru na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>K publikování zpráv souvisejících s upgradem pro uživatele pomocí Průvodce migrací sady Visual Studio použijte metody.  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> rozhraní se používá k implementaci jakéhokoli typu upgradu souboru, který se musí nacházet jako součást upgradu projektu. Toto rozhraní není voláno z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , ale je zadáno jako mechanismus pro upgrade souborů, které jsou součástí systému projektu, ale hlavní systém projektu nemusí být přímo vědom. Tato situace může nastat například v případě, že soubory a vlastnosti související s kompilátorem nejsou zpracovávány stejným vývojovým týmem, který zpracovává zbytek projektového systému.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementace IVsProjectUpgrade  
 Pokud systém projektu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> pouze, nemůže se zúčastnit **Průvodce převodem sady Visual Studio**. Nicméně i v případě, že rozhraní implementujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , můžete i nadále delegovat upgrade souboru na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementaci.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Implementace IVsProjectUpgrade  
  
1. Když se uživatel pokusí otevřít projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Metoda je volána prostředím po otevření projektu a před provedením jakékoli jiné akce uživatele v projektu. Pokud uživatel již byl vyzván k upgradu řešení, pak se <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> příznak předává v `grfUpgradeFlags` parametru. Pokud uživatel otevře projekt přímo, například pomocí příkazu **Přidat existující projekt** , <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> příznak není předán a projekt musí uživateli požádat o upgrade.  
  
2. V reakci na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> volání musí projekt vyhodnotit, zda je soubor projektu upgradován. Pokud projekt není potřeba upgradovat typ projektu na novou verzi, pak může jednoduše vrátit <xref:Microsoft.VisualStudio.VSConstants.S_OK> příznak.  
  
3. Pokud projekt potřebuje upgradovat typ projektu na novou verzi, pak musí určit, zda lze soubor projektu upravit voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody a předáním hodnoty <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametru. Projekt pak musí provést následující akce:  
  
   - Pokud `VSQueryEditResult` hodnota vrácená `pfEditCanceled` parametrem je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> , může upgrade pokračovat, protože soubor projektu lze zapsat.  
  
   - Pokud `VSQueryEditResult` je hodnota vrácená `pfEditCanceled` parametrem <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a `VSQueryEditResult` hodnota má <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bitovou sadu, pak se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musí vrátit chyba, protože uživatelé by měli vyřešit vlastní problém s oprávněním. Projekt by pak měl provádět následující akce:  
  
        Nahlaste chybu uživateli voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> . a vrátí <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> kód chyby <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
   - Pokud `VSQueryEditResult` hodnota je <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a `VSQueryEditResultFlags` hodnota má <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bitovou sadu, soubor projektu by měl být rezervován voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> ,...).  
  
4. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> volání na soubor projektu způsobí, že soubor bude rezervován a bude načtena nejnovější verze, projekt je uvolněn a znovu načten. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Metoda je volána znovu po vytvoření jiné instance projektu. Při tomto druhém volání se soubor projektu může zapsat na disk. doporučuje se, aby projekt uložil kopii souboru projektu v předchozím formátu pomocí. STARÉ rozšíření, proveďte potřebné změny upgradu a uložte soubor projektu v novém formátu. Pokud dojde k selhání jakékoli části procesu upgradu, metoda musí indikovat selhání vrácením <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> . To způsobí, že se projekt uvolní v Průzkumník řešení.  
  
    Je důležité pochopit kompletní proces, který se vyskytuje v prostředí pro případ, kdy volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody (určení hodnoty ReportOnly) vrací <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> příznaky.  
  
5. Uživatel se pokusí otevřít soubor projektu.  
  
6. Prostředí volá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementaci.  
  
7. Pokud se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> vrátí `true` , prostředí zavolá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementaci.  
  
8. Prostředí volá vaši <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementaci k otevření souboru a inicializaci objektu projektu, například Project1.  
  
9. Prostředí volá vaši `IVsProjectUpgrade::UpgradeProject` implementaci a určí, jestli se soubor projektu musí upgradovat.  
  
10. Zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předáte hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametru.  
  
11. Prostředí vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> pro `VSQueryEditResult` a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit je nastaven v `VSQueryEditResultFlags` .  
  
12. Vaše <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementace volání `IVsQueryEditQuerySave::QueryEditFiles` ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> ).  
  
    Toto volání může způsobit rezervaci nové kopie souboru projektu a nejnovější načtenou verzi a také nutnost opětovného načtení souboru projektu. V tomto okamžiku nastane jedna ze dvou věcí:  
  
- Pokud zpracováváte vlastní opětovné načtení projektu, prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementaci vaší (VSITEMID_ROOT). Po obdržení tohoto volání znovu načtěte první instanci projektu (Project1) a pokračujte v upgradu souboru projektu. Prostředí ví, že při návratu `true` pro () zpracováváte vlastní opětovné načtení <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> projektu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
- Pokud nezpracováváte svůj vlastní projekt opětovného načtení, vrátíte se `false` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ). V tomto případě, před <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> vrácením ([QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags),), prostředí vytvoří další novou instanci projektu, například "Project2", následovně:  
  
  1. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> svůj první objekt projektu Project1, takže tento objekt umísťuje do neaktivního stavu.  
  
  2. Prostředí volá vaši `IVsProjectFactory::CreateProject` implementaci a vytvoří druhou instanci projektu, "Project2".  
  
  3. Prostředí volá vaši `IPersistFileFormat::Load` implementaci k otevření souboru a inicializaci druhého objektu projektu, "Project2".  
  
  4. Prostředí volá `IVsProjectUpgrade::UpgradeProject` určitou dobu, aby bylo možné určit, zda má být objekt projektu upgradován. Toto volání je však provedeno na nové, druhé instanci projektu "Project2". Toto je projekt, který je otevřen v řešení.  
  
      > [!NOTE]
      > V instanci, která je v prvním projektu Project1, je umístěn v neaktivním stavu, je nutné se vrátit <xref:Microsoft.VisualStudio.VSConstants.S_OK> z prvního volání do vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementace. Viz [Základní projekt](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) pro implementaci `IVsProjectUpgrade::UpgradeProject` .  
  
  5. Zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a předáte hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametru.  
  
  6. Prostředí se vrátí <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a upgrade může pokračovat, protože soubor projektu lze zapsat.  
  
  Pokud se upgrade nezdaří, vraťte se <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> z `IVsProjectUpgrade::UpgradeProject` . Pokud upgrade není nutný nebo pokud se rozhodnete neupgradovat, považovat `IVsProjectUpgrade::UpgradeProject` volání za No-op. Pokud se vrátíte <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> , je do řešení pro váš projekt přidán zástupný uzel.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce převodem sady Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Upgrade položek projektu](../misc/upgrading-project-items.md)   
 [Projekty](../extensibility/internals/projects.md)