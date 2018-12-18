---
title: Vytváření vlastních projektů s ohledem na verzi | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: douge
ms.openlocfilehash: 038f478d6a8dbdd3dc050b6db85af82be377c325
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833002"
---
# <a name="making-custom-projects-version-aware"></a>Vytváření vlastních projektů s ohledem na verzi
Ve vaší vlastní projektový systém můžete povolit projektech tohoto typu se načíst ve více verzích sady Visual Studio. Můžete také zabránit projektech tohoto typu načítání v dřívější verzi sady Visual Studio. Můžete také povolit tento projekt v případě, že projekt vyžaduje opravu, převod nebo vyřazení identifikovat na novější verzi.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Umožňuje načíst projekty ve více verzích  
 Můžete upravit většinu projektů, které byly vytvořeny v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] s aktualizací SP1 nebo novějším na práci ve více verzích.  
  
 Před načtením projektu sady Visual Studio volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> metodou ke zjištění, zda je možné upgradovat projekt. Pokud je možné upgradovat projekt, `UpgradeProject_CheckOnly` metoda nastaví příznak, který způsobí, že pozdější volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metoda upgradovat projekt. Protože nekompatibilní projektů nejde upgradovat, `UpgradeProject_CheckOnly` musí nejprve vyhledat kompatibilita projektu, jak je popsáno v předchozí části.  
  
 Autor bude systém projektu implementujete `UpgradeProject_CheckOnly` (z `IVsProjectUpgradeViaFactory4` rozhraní) poskytovat uživatelům systému projektu kontrola upgradu. Když uživatelé otevřou projektu, tato metoda je volána k určení, zda projekt musíte opravit předtím, než je načten. Jsou uvedené možné požadavky na upgrade na `VSPUVF_REPAIRFLAGS`, a zahrnují tyto možnosti:  
  
1.  `SPUVF_PROJECT_NOREPAIR`: Vyžaduje žádná oprava.  
  
2.  `VSPUVF_PROJECT_SAFEREPAIR`: Vytvoří projekt kompatibilní s dřívější verzí bez problémů, které bude pravděpodobně dojde v předchozích verzích produktu.  
  
3.  `VSPUVF_PROJECT_UNSAFEREPAIR`: Vytvoří projekt zpětně kompatibilní, ale může představovat riziko problémy, které se pravděpodobně setkali s předchozími verzemi tohoto produktu. Například projekt nebudou kompatibilní, pokud závisí na různé verze sady SDK.  
  
4.  `VSPUVF_PROJECT_ONEWAYUPGRADE`: Projekt je nekompatibilní s předchozí verzí.  
  
5.  `VSPUVF_PROJECT_INCOMPATIBLE`: Označuje, že aktuální verze nepodporuje tento projekt.  
  
6.  `VSPUVF_PROJECT_DEPRECATED`: Označuje, že tento projekt už není podporovaná.  
  
> [!NOTE]
>  Aby nedocházelo k záměně, není kombinovat upgradu příznaky, při jejich nastavení. Například nejednoznačný stav upgradu, jako Nevytvářejte `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`.  
  
 Typy projektu mohou implementovat funkci `UpgradeProjectFlavor_CheckOnly` z `IVsProjectFlavorUpgradeViaFactory2` rozhraní. Chcete-li tato funkce pracovat, `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` ji musí volat implementaci již bylo zmíněno dříve. Toto volání je již implementováno v systému základního projektu jazyka Visual Basic nebo C#. Vliv tato funkce umožňuje typů projektu také určit požadavky na upgrade projektu, kromě co bylo zjištěno systému základního projektu. Kompatibilita dialogové okno zobrazuje nejzávažnějších z těchto dvou požadavků.  
  
 Visual Studio provede upgrade kontrolu, nabízí protokolovací nástroj místo hodnoty NULL jako v předchozích verzích sady Visual Studio. Protokolovací nástroj umožňuje systémů projektů a typů na další informace, které vám pomohou pochopit povaze změny, které jsou potřebné k tomu starší projekty správně načíst. Doporučujeme použít protokolovacího nástroje k poskytnutí dalších informací namísto použití dialogových oknech. Další informace najdete v tématu [protokolovací nástroj pro Upgrade](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) dále v tomto tématu.  
  
 Implementace spravované jsou k dispozici v Microsoft.VisualStudio.Shell.Interop.11.0.dll sestavení vzájemné spolupráce rozhraní upgradu projektu.  
  
 `UpgradeProject` Metody můžete určit, zda změny umožní by jinak znemožňovaly projektu načítání v předchozí verzi sady Visual Studio. Pokud ano, metoda označí projekt jako nekompatibilní. Vysvětlení, jak projekt je označen jako kompatibilní, najdete v tématu [označí projekt jako nekompatibilní](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) výše v tomto tématu. Doporučujeme vám, jakmile se zobrazí toto dialogové okno, abyste označili projektu jako nekompatibilní voláním metody `IVsAppCompat.BreakAssetCompatibility` přímo, namísto první volání `IVsAppCompat.AskForUserConsentToBreakAssetCompat` metoda vzhledem k tomu není nutné dialogové okno zobrazí dvakrát.  
  
 Tady je příklad pomohou shrnout kompatibility uživatelské prostředí. Pokud projekt byl vytvořen v dřívější verzi a aktuální verze Určuje, že upgrade je vyžadována, Visual Studio zobrazí dialogové okno požádat uživatele o souhlas provést změny. Pokud uživatel souhlasí, projekt upravit a pak načíst. Pokud toto řešení je pak zavřít a znovu otevřít ve starší verzi, jednoho-way-upgradovat projekt se nekompatibilní a nelze načíst. Pokud projekt měl pouze požadované opravy (ne upgradu), se nadále otevře opravený projektu v obou verzích.  
  
##  <a name="BKMK_Incompat"></a> Označí projekt jako nekompatibilní  
 Můžete označit jako kompatibilní s dřívějšími verzemi sady Visual Studio projekt.  Předpokládejme například, že vytvoříte projekt, který používá funkce rozhraní .NET Framework 4.5. Protože tento projekt nejde sestavit [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], lze ji označit jako kompatibilní, aby se zabránilo verze v pokusu o načtení.  
  
 Komponenta, která přidá funkci nekompatibilní zodpovídá za označí projekt jako nekompatibilní. Komponenta musí mít přístup k <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní, které představuje projekty, které vás zajímají.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Označit jako kompatibilní projektu  
  
1.  V komponentě, získat `IVsAppCompat` rozhraní z globální služby SVsSolution.  
  
     Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2.  V komponentě, volání `IVsAppCompat.AskForUserConsentToBreakAssetCompat`a předat jí pole `IVsHierarchy` rozhraní, které představují projekty, které vás zajímají.  
  
     Tato metoda má následující podpis:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Pokud se rozhodnete implementovat tento kód, zobrazí se dialogové okno kompatibilita projektu. Pole se dialogové okno požádá uživatele o souhlas pro označení všech zadaných projektů jako nekompatibilní. Pokud uživatel souhlasí, `AskForUserConsentToBreakAssetCompat` vrátí `S_OK`; v opačném případě `AskForUserConsentToBreakAssetCompat` vrátí `OLE_E_PROMPTSAVECANCELLED`.  
  
    > [!WARNING]
    >  V nejběžnějších scénářů `IVsHierarchy` pole bude obsahovat pouze jednu položku.  
  
3.  Pokud `AskForUserConsentToBreakAssetCompat` vrátí `S_OK`, součást netelefonuje, ani přijímá změny, které porušit kompatibilitu.  
  
4.  V komponentě, zavolejte `IVsAppCompat.BreakAssetCompatibility` metodu pro každý projekt, který chcete označit jako kompatibilní. Hodnotu parametru lze nastavit komponentu `lpszMinimumVersion` na konkrétní minimální verzi namísto toho, aby aplikace Visual Studio vyhledat řetězec s aktuální verzí v registru. Tento přístup minimalizuje se riziko zneužití neúmyslně nastavení vyšší hodnotu v budoucnosti, podle toho, co je v registru v daném čase komponenty. Pokud byla nastavena tato hodnota vyšší, Visual Studio nelze otevřít projekt.  
  
     Tato metoda má následující podpis:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Pokud je součást nastaví `lpszMinimumVersion` na hodnotu NULL, `BreakAssetCompatibility` volání metody `IVsAppCompat.GetCurrentDesignTimeCompatVersion` metoda získat řetězec, který představuje aktuální verzi sady Visual Studio.  
  
     Tato metoda má následující podpis:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     Pak zavolá metodu BreakAssetCompatibility `IVsHierarchy.SetProperty` metody nastavte kořenové `VSHPROPID_MinimumDesignTimeCompatVersion` vlastnost na hodnotu řetězce verze, který jste získali v předchozím kroku.  
  
     Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
>  Je nutné implementovat `VSHPROPID_MinimumDesignTimeCompatVersion` vlastnost projektu označit jako kompatibilní nebo nekompatibilní. Například pokud systém projektu používá souboru projektu MSBuild, přidejte do souboru projektu `<MinimumVisualStudioVersion>` vlastnost, jejíž hodnota se rovná odpovídající sestavení `VSHPROPID_MinimumDesignTimeCompatVersion` hodnotu vlastnosti.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Zjištění, zda projekt je nekompatibilní  
 Projekt, který je kompatibilní s aktuální verzí sady Visual Studio musí být udržovány načítání. Kromě toho projekt, který není kompatibilní nelze upgradovat nebo opravit. Proto se projekt musí být kontrolované kompatibility dvakrát: první, když se považuje pro upgrade nebo opravu a druhé, než je načten.  
  
 Pokud chcete povolit zjišťování nekompatibilitu projektu, je nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metody. Pokud projekt není kompatibilní, `UpgradeProject_CheckOnly` musí vrátit kód úspěšnosti `VS_S_INCOMPATIBLEPROJECT`, a `CreateProject` musí vrátit kód chyby: `VS_E_INCOMPATIBLEPROJECT`. Pro projekty s charakterem, je nutné implementovat `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` místo `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`.  
  
 Systém projektu se označuje do flavored, pokud má web, Office (VSTO), Silverlight nebo jiný typ projektu nástavbou ho. Starší systémy, které již implementují `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` a flavored systémů projektů, které již implementují `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` i dál podporovaná. Starší verzi `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` má následující podpis implementace:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Pokud je tato metoda nastaví `pUpgradeRequired` na hodnotu TRUE a vrátí `S_OK`, výsledek je považován za "Upgrade" a jako by metoda nastavena na hodnotu upgradu příznak `VSPUVF_PROJECT_ONEWAYUPGRADE`, která je popsána dále v tomto tématu. Vrátí následující hodnoty jsou podporovány pomocí této starší metoda, ale pouze tehdy, když `pUpgradeRequired` je nastavena na hodnotu TRUE:  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Převádí tuto hodnotu `pUpgradeRequired` hodnotu na hodnotu TRUE jako ekvivalentní `VSPUVF_PROJECT_SAFEREPAIR`, která je popsána dále v tomto tématu.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Převádí tuto hodnotu `pUpgradeRequired` hodnotu na hodnotu TRUE jako ekvivalentní `VSPUVF_PROJECT_UNSAFEREPAIR`, která je popsána dále v tomto tématu  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Převádí tuto hodnotu `pUpgradeRequired` hodnotu na hodnotu TRUE jako ekvivalentní `VSPUVF_PROJECT_ONEWAYUPGRADE`, která je popsána dále v tomto tématu.  
  
   Nové implementace v `IVsProjectUpgradeViaFactory4` a `IVsProjectFlavorUpgradeViaFactory2` povolit zadávání typ migrace vybraný k vyšší přesností.  
  
> [!NOTE]
>  Můžete ukládat do mezipaměti výsledek kontroly kompatibility pomocí `UpgradeProject_CheckOnly` metoda, takže ji můžete použít také následných volání `CreateProject`.  
  
 Například pokud `UpgradeProject_CheckOnly` a `CreateProject` metody, které jsou určeny pro [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] s SP1 projektový systém zkontrolujte soubor projektu a zjistíte, že `<MinimumVisualStudioVersion>` vlastnost sestavení je "11.0", Visual Studio 2010 s aktualizací SP1 nebudou načtení projektu. Kromě toho **řešení Navigátor** by označoval, že projekt je "nekompatibilní" a nebude načten.  
  
##  <a name="BKMK_UpgradeLogger"></a> Upgrade protokolovací nástroj  
 Volání `IVsProjectUpgradeViaFactory::UpgradeProject` obsahuje `IVsUpgradeLogger` protokolovacího nástroje, které systémů projektů a typů by měl použít poskytnout podrobné trasování upgradu pro řešení potíží. Pokud je přihlášení upozornění nebo chybu, sada Visual Studio zobrazí zprávu o upgradu.  
  
 Při zápisu do upgradu protokolovač, vezměte v úvahu následující pokyny:  
  
-   Visual Studio bude volat vyprázdnění po dokončení upgradu všech projektů. Nevolejte ji v systému projektu.  
  
-   LogMessage funkce má následující hodnoty parametru ERRORLEVEL při:  
  
    -   pro všechny informace, které byste chtěli trasování je 0.  
  
    -   1 je pro upozornění.  
  
    -   2 je pro chybu  
  
    -   3 je pro formátování sestav. Při upgradu projektu protokolu slovo "Převedený" jednou a lokalizaci slovo.  
  
-   Pokud projekt nevyžaduje žádné opravy nebo upgrade, Visual Studio vygeneruje soubor protokolu pouze v případě, že systém projektu měl protokoluje upozornění nebo chybu během UpgradeProject_CheckOnly nebo UpgradeProjectFlavor_CheckOnly metody.