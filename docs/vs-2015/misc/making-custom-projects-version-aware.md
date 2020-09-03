---
title: Vytváření vlastních projektů s podporou verze | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 0b29728cffc962b5d09a5adc45f8cac2093b020a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825683"
---
# <a name="making-custom-projects-version-aware"></a>Vytváření vlastních projektů s podporou verzí
Ve vlastním systémovém systému projektu můžete dovolit projektům tohoto typu načíst v několika verzích sady Visual Studio. Můžete také zabránit tomu, aby se projekty tohoto typu načetly v dřívější verzi sady Visual Studio. Můžete také povolit, aby se tento projekt identifikoval k novější verzi pro případ, že projekt vyžaduje opravu, převod nebo vyřazení.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Umožnění načtení projektů v několika verzích  
 Můžete upravit většinu projektů, které byly vytvořeny v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] nástroji s aktualizací SP1 nebo novější, aby fungovaly v několika verzích.  
  
 Před načtením projektu aplikace Visual Studio volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> metodu k určení, zda lze projekt upgradovat. Pokud projekt lze upgradovat, `UpgradeProject_CheckOnly` Metoda nastaví příznak, který způsobí pozdější volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody k upgradu projektu. Vzhledem k tomu, že nekompatibilní projekty nelze upgradovat, `UpgradeProject_CheckOnly` je nutné nejprve vyhledat kompatibilitu s projektem, jak je popsáno v předchozí části.  
  
 Jako autor systému projektu implementujete `UpgradeProject_CheckOnly` (z `IVsProjectUpgradeViaFactory4` rozhraní), aby uživatelům svého systému projektu poskytoval kontrolu upgradu. Když uživatelé otevřou projekt, je volána Tato metoda, aby bylo možné určit, zda projekt musí být před načtením opraven. Možné požadavky na upgrade jsou uvedené v části `VSPUVF_REPAIRFLAGS` a zahrnují tyto možnosti:  
  
1. `SPUVF_PROJECT_NOREPAIR`: Nevyžaduje žádnou opravu.  
  
2. `VSPUVF_PROJECT_SAFEREPAIR`: Zajistí, aby byl projekt kompatibilní se starší verzí bez problémů, se kterými se můžete setkat s předchozími verzemi produktu.  
  
3. `VSPUVF_PROJECT_UNSAFEREPAIR`: Předává projekt zpětně kompatibilní, ale s rizikem problémů, které jste mohli narazit s předchozími verzemi produktu. Například projekt nebude kompatibilní, pokud je závislý na různých verzích sady SDK.  
  
4. `VSPUVF_PROJECT_ONEWAYUPGRADE`: Zpřístupní projekt nekompatibilní se starší verzí.  
  
5. `VSPUVF_PROJECT_INCOMPATIBLE`: Označuje, že aktuální verze nepodporuje tento projekt.  
  
6. `VSPUVF_PROJECT_DEPRECATED`: Označuje, že tento projekt již není podporován.  
  
> [!NOTE]
> Chcete-li předejít nejasnostem, Nekombinujte příznaky upgradu při jejich nastavování. Nevytvářejte například nejednoznačný stav upgradu, jako je `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED` .  
  
 Charakter projektu mohou implementovat funkci `UpgradeProjectFlavor_CheckOnly` z `IVsProjectFlavorUpgradeViaFactory2` rozhraní. Aby tato funkce fungovala, `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` musí výše zmíněná implementace zavolat. Toto volání je již implementováno v systému základního projektu Visual Basic nebo C#. Účinek této funkce umožňuje, aby projekt také určil požadavky na upgrade projektu, a to i v případě, že byl zjištěn základní projektový systém. Dialogové okno Kompatibilita zobrazuje nejpřísnější ze dvou požadavků.  
  
 Když aplikace Visual Studio provede kontrolu upgradu, poskytuje protokolovací nástroj místo hodnoty NULL jako v předchozích verzích sady Visual Studio. Protokolovací nástroj umožňuje systémům a charakterům projektů poskytovat další informace, které vám pomůžou pochopit, jaké změny jsou potřeba k tomu, aby se vaše starší projekty správně načetly. Doporučujeme použít protokolovací nástroj k poskytnutí dalších informací místo použití dialogových oken. Další informace najdete v části [protokolovací nástroj pro upgrade](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) dále v tomto tématu.  
  
 Pro spravované implementace jsou k dispozici rozhraní upgradu projektu ve Microsoft.VisualStudio.Shell.Interop.11.0.dll definičním sestavením.  
  
 `UpgradeProject`Metoda může určit, zda provedené změny by zabránila načtení projektu v předchozí verzi sady Visual Studio. Pokud ano, metoda označí projekt jako nekompatibilní. Chcete-li pochopit, jak je projekt označen jako nekompatibilní, přečtěte si téma [označení projektu jako nekompatibilního](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) dříve v tomto tématu. Doporučujeme, abyste po zobrazení tohoto dialogového okna označili projekt jako nekompatibilní voláním metody `IVsAppCompat.BreakAssetCompatibility` přímo místo prvního volání `IVsAppCompat.AskForUserConsentToBreakAssetCompat` metody, protože dialogové okno není nutné zobrazit dvakrát.  
  
 Tady je příklad, který vám může přispět k sumarizaci uživatelského prostředí kompatibility. Pokud byl projekt vytvořen v dřívější verzi a aktuální verze určuje, zda je vyžadován upgrade, Visual Studio zobrazí dialogové okno, které požádá uživatele o oprávnění k provedení změn. Pokud uživatel souhlasí, projekt se upraví a potom načte. Pokud je řešení potom zavřeno a znovu otevřeno v předchozí verzi, bude aktualizovaný projekt nekompatibilní a nebude načten. Pokud projekt vyžadoval pouze opravu (místo upgradu), Opravený projekt bude stále otevřen v obou verzích.  
  
## <a name="marking-a-project-as-incompatible"></a><a name="BKMK_Incompat"></a> Označení projektu jako nekompatibilního  
 Projekt můžete označit jako nekompatibilní s předchozími verzemi sady Visual Studio.  Předpokládejme například, že vytvoříte projekt, který používá funkci .NET Framework 4,5. Vzhledem k tomu, že tento projekt nemůže být sestaven [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] , můžete jej označit jako nekompatibilní, aby se jeho verze nemohla pokusit načíst.  
  
 Komponenta, která přidává nekompatibilní funkci, zodpovídá za označení projektu jako nekompatibilního. Komponenta musí mít přístup k <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní, které představuje projekty, které vás zajímají.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Označení projektu jako nekompatibilní  
  
1. V rámci komponenty Získejte `IVsAppCompat` rozhraní z globálního SVsSolution služby.  
  
     Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2. V komponentě zavolejte `IVsAppCompat.AskForUserConsentToBreakAssetCompat` a předejte jí pole `IVsHierarchy` rozhraní, které představuje projekty, které vás zajímají.  
  
     Tato metoda má následující signaturu:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Pokud tento kód implementujete, zobrazí se dialogové okno Kompatibilita projektu. Dialog zobrazí uživateli výzvu k zadání oprávnění k označení všech zadaných projektů jako nekompatibilních. Pokud uživatel souhlasí, `AskForUserConsentToBreakAssetCompat` vrátí, `S_OK` jinak `AskForUserConsentToBreakAssetCompat` vrátí `OLE_E_PROMPTSAVECANCELLED` .  
  
    > [!WARNING]
    > V nejběžnějších scénářích `IVsHierarchy` bude pole obsahovat pouze jednu položku.  
  
3. Pokud se `AskForUserConsentToBreakAssetCompat` vrátí `S_OK` , komponenta provede nebo přijme změny, které přeruší kompatibilitu.  
  
4. V rámci vaší komponenty zavolejte `IVsAppCompat.BreakAssetCompatibility` metodu pro každý projekt, který chcete označit jako nekompatibilní. Komponenta může nastavit hodnotu parametru `lpszMinimumVersion` na konkrétní minimální verzi místo toho, aby sada Visual Studio vyhledala aktuální řetězec verze v registru. Tento přístup minimalizuje riziko, že komponenta neúmyslně nastaví vyšší hodnotu v budoucnosti, a to na základě toho, co je v registru v daném okamžiku. Pokud byla nastavena vyšší hodnota, Visual Studio nemůže projekt otevřít.  
  
     Tato metoda má následující signaturu:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Pokud je komponenta nastavena `lpszMinimumVersion` na hodnotu null, `BreakAssetCompatibility` metoda volá `IVsAppCompat.GetCurrentDesignTimeCompatVersion` metodu pro získání řetězce, který představuje aktuální verzi sady Visual Studio.  
  
     Tato metoda má následující signaturu:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     Metoda BreakAssetCompatibility pak zavolá `IVsHierarchy.SetProperty` metodu pro nastavení kořenové `VSHPROPID_MinimumDesignTimeCompatVersion` vlastnosti na hodnotu řetězce verze, který jste získali v předchozím kroku.  
  
     Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
> Je nutné implementovat `VSHPROPID_MinimumDesignTimeCompatVersion` vlastnost k označení projektu jako kompatibilního nebo nekompatibilního. Například pokud systém projektu používá soubor projektu MSBuild, přidejte do souboru projektu `<MinimumVisualStudioVersion>` vlastnost sestavení, která má hodnotu rovnou odpovídající `VSHPROPID_MinimumDesignTimeCompatVersion` hodnotě vlastnosti.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Zjištění, zda je projekt nekompatibilní  
 Projekt, který je nekompatibilní s aktuální verzí sady Visual Studio, musí být udržován od načtení. Navíc nekompatibilní projekt není možné upgradovat ani opravit. Proto musí být projekt zkontrolován na kompatibilitu dvakrát: první, při zvažování pro upgrade nebo opravu a druhý, před načtením.  
  
 Chcete-li povolit detekci nekompatibility projektu, je nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metody a. Pokud je projekt nekompatibilní, `UpgradeProject_CheckOnly` musí vrátit kód úspěšné `VS_S_INCOMPATIBLEPROJECT` a `CreateProject` musí vrátit kód chyby `VS_E_INCOMPATIBLEPROJECT` . Pro projekty, které jsou ve vlastnictví, je nutné implementovat `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` místo `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` .  
  
 Systém projektu je označován jako přidaný, pokud má web, Office (VSTO), Silverlight nebo jiný typ projektu sestavený nad ním. Starší projektové systémy, které již implementují `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` a mají charakter systému projektu, které již implementují `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` i nadále podporované. Starší verze nástroje `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` má následující signaturu implementace:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Pokud tato metoda nastaví `pUpgradeRequired` na hodnotu true a vrátí `S_OK` , výsledek bude považován za "upgrade", a to i v případě, že metoda nastavila příznak upgradu na hodnotu `VSPUVF_PROJECT_ONEWAYUPGRADE` , která je popsána dále v tomto tématu. Následující návratové hodnoty jsou podporovány pomocí této starší metody, ale pouze v případě `pUpgradeRequired` , že je nastavena na hodnotu true:  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Tato návratová hodnota překládá `pUpgradeRequired` hodnotu na true jako ekvivalent `VSPUVF_PROJECT_SAFEREPAIR` , která je popsána dále v tomto tématu.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Tato návratová hodnota překládá `pUpgradeRequired` hodnotu na true jako ekvivalent `VSPUVF_PROJECT_UNSAFEREPAIR` , která je popsána dále v tomto tématu.  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Tato návratová hodnota překládá `pUpgradeRequired` hodnotu na true jako ekvivalent `VSPUVF_PROJECT_ONEWAYUPGRADE` , která je popsána dále v tomto tématu.  
  
   Nové implementace v nástroji `IVsProjectUpgradeViaFactory4` a `IVsProjectFlavorUpgradeViaFactory2` umožňují přesnější určení typu migrace.  
  
> [!NOTE]
> Výsledek kontroly kompatibility můžete ukládat do mezipaměti pomocí `UpgradeProject_CheckOnly` metody, aby ji bylo možné použít i při následném volání `CreateProject` .  
  
 Například pokud `UpgradeProject_CheckOnly` `CreateProject` metody a, které jsou zapsány pro [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] systém projektu s aktualizací SP1, prozkoumají soubor projektu a zjistí, že `<MinimumVisualStudioVersion>` vlastnost Build je "11,0", Visual Studio 2010 s aktualizací SP1 nenačte projekt. Kromě toho **navigátor řešení** by označil, že projekt je "nekompatibilní" a nenačte ho.  
  
## <a name="the-upgrade-logger"></a><a name="BKMK_UpgradeLogger"></a> Protokolovací nástroj pro upgrade  
 Volání `IVsProjectUpgradeViaFactory::UpgradeProject` obsahuje `IVsUpgradeLogger` protokolovací nástroj, který by měl používat systémy a charaktery projektu k poskytnutí podrobného trasování upgradu pro řešení problémů. Pokud je zaznamenáno upozornění nebo chyba, Visual Studio zobrazí zprávu o upgradu.  
  
 Při zápisu do protokolovacího nástroje pro upgrade Vezměte v úvahu následující pokyny:  
  
- Po dokončení upgradu všech projektů bude Visual Studio volat Flush. Nevolejte ho v systému projektu.  
  
- Funkce LogMessage – má následující ErrorLevel:  
  
  - 0 je pro všechny informace, které byste chtěli trasovat.  

  - 1 je pro upozornění.  

  - 2 je pro chybu  

  - 3 je pro formátovací modul sestavy. Když je projekt upgradován, Zaprotokolujte slovo "převedeno" jednou a Nelokalizovat slovo.  
  
- Pokud projekt nevyžaduje žádnou opravu nebo upgrade, aplikace Visual Studio vygeneruje soubor protokolu pouze v případě, že systém projektu zaznamenal upozornění nebo chybu během UpgradeProject_CheckOnly nebo UpgradeProjectFlavor_CheckOnly metody.
