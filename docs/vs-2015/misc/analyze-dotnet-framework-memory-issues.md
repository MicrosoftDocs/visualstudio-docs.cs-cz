---
title: Analýza problémů s .NET Framework paměti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e89b3f04a3e0e1dcd0cc29e57e09b1c71fbc2279
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545545"
---
# <a name="analyze-net-framework-memory-issues"></a>Analýza problémů s pamětí rozhraní .NET Framework
Pomocí analyzátoru spravované paměti sady Visual Studio Najděte nevracení paměti a neefektivní využití paměti v .NET Framework kódu. Minimální .NET Framework verze cílového kódu je .NET Framework 4,5.  
  
 Nástroj Analýza paměti analyzuje informace v *souborech s výpisem paměti s daty haldy* , které kopíruje objekty v paměti aplikace. Soubory výpisu (. dmp) můžete shromáždit z integrovaného vývojového prostředí (IDE) sady Visual Studio nebo pomocí jiných systémových nástrojů.  
  
- Můžete analyzovat jeden snímek a pochopit relativní dopad typů objektů při použití paměti a vyhledat kód v aplikaci, která používá paměť neefektivně.  
  
- Můžete také porovnat (*diff*) dva snímky aplikace a vyhledat oblasti v kódu, které způsobí, že se využití paměti zvýší v čase.  
  
  Návod k analyzátoru spravované paměti najdete v tématu [použití Visual Studio 2013 k diagnostice problémů s pamětí .NET v produkci](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) na blogu Visual Studio ALM + Team Foundation Server.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Obsah  
 [Využití paměti v aplikacích .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identifikace problému s pamětí v aplikaci](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Shromáždit snímky paměti](#BKMK_Collect_memory_snapshots)  
  
 [Analyzovat využití paměti](#BKMK_Analyze_memory_use)  
  
## <a name="memory-use-in-net-framework-apps"></a><a name="BKMK_Memory_use_in__NET_Framework_apps"></a>Využití paměti v aplikacích .NET Framework  
 .NET Framework je modul runtime uvolňován paměti, takže ve většině aplikací není využití paměti problémem. Ale v dlouhotrvajících aplikacích, jako jsou webové služby a aplikace, a v zařízeních, která mají omezené množství paměti, může akumulace objektů v paměti ovlivnit výkon aplikace a zařízení, na kterém je spuštěný. Nadměrné využití paměti může omezují aplikaci a počítač prostředků, pokud je systém uvolňování paměti spuštěn příliš často, nebo pokud je operační systém nucen přesunout paměť mezi pamětí RAM a diskem. V nejhorším případě může dojít k chybě aplikace s výjimkou "nedostatek paměti".  
  
 *Halda spravovaná* rozhraním .NET je oblast virtuální paměti, kde jsou uloženy referenční objekty vytvořené aplikací. Životnost objektů je spravovaná systémem uvolňování paměti (GC). Systém uvolňování paměti používá odkazy k udržení přehledu o objektech, které zabírají bloky paměti. Odkaz je vytvořen při vytvoření objektu a jeho přiřazení proměnné. Jeden objekt může mít více odkazů. Například další odkazy na objekt lze vytvořit přidáním objektu do třídy, kolekce nebo jiné struktury dat nebo přiřazením objektu druhé proměnné. Méně zřejmý způsob, jak vytvořit odkaz, je jedním objektem přidání obslužné rutiny do události jiného objektu. V tomto případě druhý objekt obsahuje odkaz na první objekt, dokud není obslužná rutina explicitně odebrána, nebo když je druhý objekt zničen.  
  
 V případě každé aplikace udržuje GC strom odkazů, které sledují objekty, na které aplikace odkazuje. *Referenční strom* obsahuje sadu kořenů, včetně globálních a statických objektů, jakož i přidružených zásobníků vláken a dynamicky vytvořených objektů. Objekt je root, pokud má objekt alespoň jeden nadřazený objekt, který obsahuje odkaz na něj. GC může uvolnit paměť objektu pouze v případě, že žádný jiný objekt nebo proměnná v aplikaci na něj neodkazuje.  
  
 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="identify-a-memory-issue-in-an-app"></a><a name="BKMK_Identify_a_memory_issue_in_an_app"></a>Identifikace problému s pamětí v aplikaci  
 Nejužitečnější příznak potíží s pamětí je výkon vaší aplikace, zejména v případě, že se výkon snižuje v čase. Snížení výkonu jiných aplikací v době, kdy je aplikace spuštěná, může také znamenat problém s pamětí. Pokud se domníváte, že se jedná o problém s pamětí, použijte nástroj, jako je například Správce úloh nebo [sledování výkonu systému Windows](https://technet.microsoft.com/library/cc749249.aspx) . Můžete například vyhledat nárůst celkové velikosti paměti, kterou nemůžete vysvětlit jako možný zdroj nevracení paměti:  
  
 ![Konzistentní nárůst paměti v Sledování prostředků](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Můžete si také všimnout špičky paměti, které jsou větší než vaše znalosti kódu, což by vedlo k tomu, že by mohlo Ukázat neefektivní využití paměti v proceduře:  
  
 ![Špičky paměti v Správce prostředků](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="collect-memory-snapshots"></a><a name="BKMK_Collect_memory_snapshots"></a>Shromáždit snímky paměti  
 Nástroj Analýza paměti analyzuje informace v *souborech výpisu* paměti, které obsahují informace o haldě. Můžete vytvořit soubory s výpisem paměti v aplikaci Visual Studio nebo můžete použít nástroj jako [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) z [Windows Sysinternals](https://technet.microsoft.com/sysinternals). Podívejte [se, co je výpis paměti a jak ho vytvořit?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) na blogu týmu ladicího programu sady Visual Studio.  
  
> [!NOTE]
> Většina nástrojů může shromažďovat informace o vystavení s daty paměti haldy nebo bez ní. Analyzátor paměti sady Visual Studio vyžaduje úplné informace o haldě.  
  
 **Shromažďování výpisu paměti ze sady Visual Studio**  
  
1. Můžete vytvořit soubor s výpisem paměti pro proces, který byl spuštěn z projektu aplikace Visual Studio, nebo můžete připojit ladicí program ke spuštěnému procesu. Viz [připojit ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Zastavit provádění. Ladicí program se zastaví, když vyberete možnost **rozdělit vše** v nabídce **ladění** nebo na výjimku nebo na zarážku.  
  
3. V nabídce **ladění** vyberte možnost **Uložit výpis jako**. V dialogovém okně **Uložit výpis paměti** zadejte umístění a ujistěte se, že je v seznamu **Uložit jako typ** vybrána možnost **s minimálním výpisem s haldou** (výchozí).  
  
   **Porovnání dvou snímků paměti**  
  
   Chcete-li analyzovat nárůst využití paměti aplikací, shromážděte ze samostatné instance aplikace dva soubory s výpisem paměti.  
  
   ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="analyze-memory-use"></a><a name="BKMK_Analyze_memory_use"></a>Analyzovat využití paměti  
 [Filtrovat seznam objektů](#BKMK_Filter_the_list_of_objects) **&#124;** [analyzovat data paměti z jednoho snímku](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [porovnat dva snímky paměti](#BKMK_Compare_two_memory_snapshots)  
  
 Postup analýzy souboru s výpisem paměti pro problémy s využitím paměti:  
  
1. V aplikaci Visual Studio zvolte **soubor**, **otevřete** a zadejte soubor s výpisem paměti.  
  
2. Na stránce **Souhrn souborů s minimálním výpisem** vyberte **ladit spravovanou paměť**.  
  
    ![Stránka souhrnu souborů výpisu](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Analyzátor paměti spustí relaci ladění pro analýzu souboru a zobrazí výsledky na stránce zobrazení haldy:  
  
   ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="filter-the-list-of-objects"></a><a name="BKMK_Filter_the_list_of_objects"></a>Filtrovat seznam objektů  
 Analyzátor paměti standardně filtruje seznam objektů ve snímku paměti, aby zobrazil pouze typy a instance, které jsou v uživatelském kódu, a zobrazí pouze typy, jejichž celková celková velikost překračuje prahovou hodnotu celkové velikosti haldy. Tyto možnosti můžete změnit v seznamu **zobrazení nastavení** :  
  
|Name|Popis|  
|-|-|  
|**Povolit Pouze můj kód**|Pouze můj kód skrývá většinu běžných systémových objektů, takže se v seznamu zobrazí jenom typy, které vytvoříte.<br /><br /> Můžete také nastavit možnost Pouze můj kód v dialogovém okně **Možnosti** aplikace Visual Studio. V nabídce **ladění** vyberte **Možnosti a nastavení**. Na kartě **Debugging** / **Obecné** ladění vyberte nebo zrušte zaškrtnutí **pouze můj kód**.|  
|**Sbalit malé objekty**|**Sbalení malých objektů** skryje všechny typy, jejichž celková celková velikost je menší než 0,5 procent celkové velikosti haldy.|  
  
 Seznam typů můžete filtrovat také zadáním řetězce do **vyhledávacího** pole. V seznamu se zobrazí pouze typy, jejichž názvy obsahují řetězec.  
  
 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="analyze-memory-data-in-from-a-single-snapshot"></a><a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a>Analyzovat data paměti z jednoho snímku  
 Visual Studio spustí novou relaci ladění pro analýzu souboru a zobrazí data paměti v okně zobrazení haldy.  
  
 ![Seznam typů objektů](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Tabulka typů objektů  
 Horní tabulka obsahuje seznam typů objektů, které jsou uloženy v paměti.  
  
- **Count** zobrazuje počet instancí typu ve snímku.  
  
- **Velikost (bajty)** je velikost všech instancí typu s výjimkou velikosti objektů, na které jsou odkazy uloženy. Rozhraní  
  
- **Celková velikost (bajty)** zahrnuje velikosti odkazovaných objektů.  
  
  Můžete zvolit ikonu instance (![ikona instance ve sloupci Typ objektu](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) ve sloupci **typ objektu** , chcete-li zobrazit seznam instancí tohoto typu.  
  
#### <a name="instance-table"></a>Tabulka instancí  
 ![Tabulka instancí](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instance** je umístění v paměti objektu, které slouží jako identifikátor objektu objektu.  
  
- **Value** zobrazuje skutečnou hodnotu hodnotových typů. Můžete umístit ukazatel myši na název typu odkazu a zobrazit jeho hodnoty dat v datovém popisku.  
  
   ![Hodnoty instancí v popisku dat](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Velikost (bajty)** je velikost objektu s výjimkou velikosti objektů, na které obsahuje odkazy. Rozhraní  
  
- **Celková velikost (bajty)** zahrnuje velikosti odkazovaných objektů.  
  
  Ve výchozím nastavení jsou typy a instance seřazené podle **velikosti (bajty)**. Chcete-li změnit pořadí řazení, v seznamu vyberte záhlaví sloupce.  
  
#### <a name="paths-to-root"></a>Cesty ke kořenu  
  
- Pro typ vybraný z tabulky **typu objektu** , **cesty k kořenové** tabulce zobrazí jedinečné typy hierarchií, které vedou k kořenovým objektům pro všechny objekty typu, spolu s počtem odkazů na typ, který je nad ním v hierarchii.  
  
- Pro objekt vybraný z instance typu **cest k kořenu** zobrazuje graf skutečných objektů, které obsahují odkaz na instanci. Můžete umístit ukazatel myši na název objektu a zobrazit jeho hodnoty dat v datovém popisku.  
  
#### <a name="referenced-types--referenced-objects"></a>Odkazované typy/odkazované objekty  
  
- Pro typ vybraný z tabulky **typu objektu** zobrazuje karta **odkazované typy** velikost a počet odkazovaných typů držených všemi objekty vybraného typu.  
  
- Pro vybranou instanci typu jsou **odkazované objekty** zobrazeny objekty, které jsou uloženy vybranou instancí. Na název můžete umístit ukazatel myši a zobrazit jeho hodnoty dat v tipu dat.  
  
  **Cyklické odkazy**  
  
  Objekt může odkazovat na druhý objekt, který přímo nebo nepřímo drží odkaz na první objekt. Když analyzátor paměti zjistí tuto situaci, zastaví rozšiřování cesty odkazů a přidá anotaci **[zjistilo** se do výpisu prvního objektu a zastaví se.  
  
  **Kořenové typy**  
  
  Analyzátor paměti přidává poznámky ke kořenovým objektům, které popisují druh odkazovaného typu:  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**Statická proměnná**`VariableName`|Statická proměnná. `VariableName`je název proměnné.|  
|**Konečný popisovač**|Odkaz z fronty finalizační metody|  
|**Lokální proměnná**|Místní proměnná.|  
|**Silný popisovač**|Popisovač na silný odkaz z tabulky popisovače objektu.|  
|**Async. Připnutý popisovač**|Asynchronní připnutý objekt z tabulky popisovače objektu.|  
|**Závislý popisovač**|Závislý objekt z tabulky popisovače objektu.|  
|**Připnutý popisovač**|Připnutý silný odkaz z tabulky popisovače objektu.|  
|**RefCount popisovač**|Objekt pro vypočítané odkazy z tabulky popisovače objektu.|  
|**Popisovač sizedref popisovač**|Silný popisovač, který při uvolňování paměti udržuje přibližnou velikost souhrnu všech objektů a kořenových objektů.|  
|**Připnuté místní proměnná**|Připnuté místní proměnná.|  
  
### <a name="compare-two-memory-snapshots"></a><a name="BKMK_Compare_two_memory_snapshots"></a>Porovnat dva snímky paměti  
 Můžete porovnat dva soubory s výpisem paměti a vyhledat objekty, které by mohly být příčinou nevracení paměti. Interval mezi kolekcí prvního (předchozího) a druhého (pozdějšího) souboru by měl být dostatečně velký, aby nárůst počtu nevrácených objektů byl snadno zřejmý. Porovnání těchto dvou souborů:  
  
1. Otevřete druhý soubor výpisu a pak na stránce **Souhrn souborů s minimálním výpisem** zvolte **ladění spravované paměti** .  
  
2. Na stránce Sestava analýzy paměti otevřete seznam **Vybrat základní hodnoty** a zvolte možnost **Procházet** a zadejte první soubor s výpisem paměti.  
  
   Analyzátor přidá sloupce do horního podokna sestavy, které zobrazuje rozdíl mezi **počtem**, **velikostí**a **celkovou velikostí** typů s hodnotami v předchozím snímku.  
  
   ![Rozdílové sloupce v seznamu typů](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Sloupec **rozdíl počtu odkazů** je také přidán do **složky cesty ke kořenové** tabulce.  
  
   ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="see-also"></a>Viz také  
 [Blog sady TFS ALM sady Visual Studio: použití Visual Studio 2013 k diagnostice problémů s pamětí .NET v produkčním prostředí](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Kanál 9 &#124; analýzy spravované paměti v programu Visual Studio TV &#124;](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Kanál 9 &#124; sada nástrojů sady Visual Studio &#124; spravovanou analýzu paměti v Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)