---
title: Analýza problémů paměti rozhraní .NET Framework | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: douge
ms.openlocfilehash: 5b5b79e351f828f443e133f40c322ffba3f1a8b6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810478"
---
# <a name="analyze-net-framework-memory-issues"></a>Analýza problémů s pamětí rozhraní .NET Framework
Hledání nevrácené paměti a neefektivní paměti použijte v kódu rozhraní .NET Framework pomocí sady Visual Studio managed analyzátoru paměti. Minimální verze rozhraní .NET Framework cílový kód je rozhraní .NET Framework 4.5.  
  
 Nástroj pro analýzu paměti analyzuje informace v *soubory s daty haldy výpisu paměti* , která kopie objektů v paměti aplikace. Soubory s výpisem paměti (.dmp) můžete shromažďovat z integrovaného vývojového prostředí sady Visual Studio nebo pomocí jiných nástrojů systému.  
  
- Jeden snímek pochopit jeho relativní dopad typů objektů na využití paměti a vyhledání kódu vaší aplikace, která používá paměť neefektivně, můžete analyzovat.  
  
- Můžete také porovnat (*diff*) dvěma snímky aplikaci pro hledání oblastí ve vašem kódu, které způsobují paměť můžete postupem doby zvyšuje.  
  
  Návod analýza spravované paměti najdete v tématu [pomocí Visual Studio 2013 k diagnostice problémů paměti rozhraní .NET v produkčním prostředí](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) na Visual Studio ALM + blog Team Foundation Server.  
  
##  <a name="BKMK_Contents"></a> Obsah  
 [Využití paměti v aplikacích rozhraní .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identifikovat problém paměti v aplikaci](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Shromažďovat snímky paměti](#BKMK_Collect_memory_snapshots)  
  
 [Analýza využití paměti](#BKMK_Analyze_memory_use)  
  
##  <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Využití paměti v aplikacích rozhraní .NET Framework  
 Rozhraní .NET Framework je uklizena modulem runtime, aby ve většině aplikací, využití paměti nepředstavuje žádný problém. Ale dlouho běžící aplikace jako webové služby a aplikace a zařízení, která mají omezené množství paměti, akumulací objektů v paměti může mít vliv na výkon aplikace a zařízení, na kterém poběží. Použití využívala příliš mnoho paměti se může zhoršit výkon aplikace a počítače prostředky systému uvolňování paměti běží příliš často nebo pokud se musí přesunout paměti mezi paměti RAM a disk operačního systému. V nejhorším případě aplikace může dojít k selhání s výjimkou "nedostatek paměti".  
  
 .NET *spravované haldě* je oblast virtuální paměti, kde jsou uloženy odkazů na objekty vytvořené aplikace. Doba života objektů spravuje systému uvolňování paměti (GC). Uvolňování paměti používá odkazů ke sledování objektů, které zabírají bloky paměti. Pokud objekt je vytvořen a přiřadit proměnné je vytvořen odkaz. Jeden objekt může mít více odkazů. Další odkazy na objekt lze například vytvořit přidáním objekt do třídy, kolekce nebo jiné datové struktury, nebo přiřazení objektu k druhé proměnné. Méně zřejmé způsob vytvoření odkazu je jeden objekt přidání obslužné rutiny událostí jiného objektu. V takovém případě druhý objekt, který obsahuje odkaz na první objekt, dokud se explicitně odebere obslužnou rutinu nebo druhý objekt je zničen.  
  
 Pro každou aplikaci uvolňování paměti uchovává strom odkazy, které sleduje objekty odkazují aplikace. *Odkaz stromu* má sadu kořenových adresářů, které zahrnuje globální a statické objekty, a také zásobníky přidružené vlákno a dynamicky vytvořit instanci objektů. Objekt je kořenem, pokud má aspoň jeden nadřazený objekt, který obsahuje odkaz na objekt. Uvolňování paměti mohl uvolnit paměť objektu, pouze v případě, že na ni odkaz nemá žádný objekt nebo proměnná v aplikaci.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Identifikovat problém paměti v aplikaci  
 Většina viditelným projevem problémy s pamětí je výkon vaší aplikace, zejména v případě, že v čase snižuje výkon. Snížení výkonu dalších aplikací, když běží vaše aplikace může také znamenat problém s paměti. Pokud máte podezření na chybu paměti, použijte nástroj jako správce úloh nebo [Windows Performance Monitor](http://technet.microsoft.com/library/cc749249.aspx) dále prozkoumat. Například vyhledejte nárůst celkové velikosti paměti, kterou nelze vysvětlují jako možné příčiny nevracení paměti:  
  
 ![Konzistentní paměti nárůst sledování prostředků](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Můžete také všimnout špičky využití paměti, které jsou větší, než byste navrhnout svoje znalosti v oblasti kód, který může ukazovat na neefektivní využití paměti v postupu:  
  
 ![Špičky využití paměti v Resource Manageru](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
##  <a name="BKMK_Collect_memory_snapshots"></a> Shromažďovat snímky paměti  
 Nástroj pro analýzu paměti analyzuje informace v *soubory s výpisem paměti* obsahující informace o haldě. V sadě Visual Studio můžete vytvořit soubory s výpisem paměti, nebo můžete použít nástroje, jako je [ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx) z [Windows Sysinternals](http://technet.microsoft.com/sysinternals). Zobrazit [co je výpis paměti, a jak jeden vytvořit?](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) na blogu týmu Visual Studio Debugger.  
  
> [!NOTE]
>  Většina nástrojů může shromažďovat informace z výpisu paměti s nebo bez dat kompletní haldy paměti. Analyzátor paměti Visual Studio vyžaduje úplnou haldy informace.  
  
 **Shromažďovat výpis ze sady Visual Studio**  
  
1. Můžete vytvořit soubor s výpisem paměti pro proces, který bylo spuštěné z projektu sady Visual Studio, nebo můžete připojit ladicí program ke spuštěnému procesu. Zobrazit [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Zastavte provádění. Ladicí program zastaví, když zvolíte **příkaz Pozastavit vše** na **ladění** nabídky, nebo na výjimku, nebo na zarážce  
  
3. Na **ladění** nabídce zvolte **uložit výpis paměti jako**. V **uložit výpis paměti jako** dialogové okno pole, zadejte umístění a ujistěte se, že **minimální výpis s haldou** (výchozí) je vybraná v **uložit jako typ** seznamu.  
  
   **K porovnání dvou snímků paměti**  
  
   Pokud chcete analyzovat nárůst využití paměti aplikace, shromážděte dva soubory s výpisem paměti z jedné instance aplikace.  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Analyze_memory_use"></a> Analýza využití paměti  
 [Filtrovat seznam objektů](#BKMK_Filter_the_list_of_objects) **&#124;** [analýza dat z jednoho snímku paměti](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [porovnat dva paměti snímky](#BKMK_Compare_two_memory_snapshots)  
  
 K analýze souboru s výpisem paměti pomocí problémy:  
  
1. V sadě Visual Studio, zvolte **souboru**, **otevřít** a určete soubor s výpisem paměti.  
  
2. Na **soubor souhrnu minimálního výpisu** zvolte **ladit spravovanou paměť**.  
  
    ![Stránka souhrnného souboru výpisu](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Analyzátor paměti spustí relaci ladění analyzovat soubor a zobrazí výsledky v haldě zobrazení stránky:  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Filter_the_list_of_objects"></a> Filtrovat seznam objektů  
 Analyzátor paměti ve výchozím nastavení, filtruje seznam objektů v paměti snímku zobrazíte jen typy a instance, které mají kód pod licencí uživatelů a zobrazíte pouze ty typy, jejichž celková velikost včetně překročit prahovou hodnotu Procento celkovou velikost haldy. Tyto možnosti v můžete změnit **nastavení zobrazení** seznamu:  
  
|||  
|-|-|  
|**Povolit volbu pouze vlastní kód**|Pouze můj kód skryje nejběžnější systémové objekty tak, aby se v seznamu zobrazí pouze typy, které vytvoříte.<br /><br /> Můžete také nastavit možnost pouze vlastní kód v sadě Visual Studio **možnosti** dialogové okno. Na **ladění** nabídce zvolte **možnosti a nastavení**. V **ladění**/**Obecné** kartu, vyberte nebo zrušte **pouze můj kód**.|  
|**Sbalit malé objekty**|**Sbalit malé objekty** skryje všechny typy, jejichž celková velikost (včetně) je menší než 0,5 procent celkovou velikost haldy.|  
  
 Můžete také filtrovat seznam typů tak, že zadáte řetězec **hledání** pole. V seznamu zobrazí pouze ty typy, jejichž názvy obsahují řetězec.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analýza dat z jednoho snímku paměti  
 Visual Studio spustí novou relaci ladění analyzovat soubor a zobrazí v okně haldě zobrazení dat paměti.  
  
 ![Typ objektu seznamu](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Tabulka typů objektů  
 Hlavní tabulka uvádí typy objektů, které jsou uložené v paměti.  
  
- **Počet** zobrazuje počet instancí typu ve snímku.  
  
- **Velikost (bajty)** je velikost všechny instance daného typu, s výjimkou velikost obsahuje odkazy na objekty. Rozhraní  
  
- **Celková velikost (bajty)** zahrnuje velikosti odkazované objekty.  
  
  Můžete použít ikonu instance (![ikonu instance ve sloupci Typ objektu](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) v **typ objektu** sloupce a zobrazit seznam instancí Zadejte.  
  
#### <a name="instance-table"></a>Instance tabulky  
 ![Instance tabulky](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instance** je umístění v paměti objektu, který slouží jako identifikátor objektu objektu  
  
- **Hodnota** zobrazovat skutečné hodnoty typů hodnot. Při najetí myší na název typu odkazu k zobrazení hodnot dat v popisu dat.  
  
   ![Instance hodnoty v popisu dat](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Velikost (bajty)** je velikost objektu, s výjimkou velikost obsahuje odkazy na objekty. Rozhraní  
  
- **Celková velikost (bajty)** zahrnuje velikosti odkazované objekty.  
  
  Ve výchozím nastavení, typy a instance jsou seřazeny podle **celkové velikosti (bajty)**. Vyberte záhlaví sloupce v seznamu, chcete-li změnit pořadí řazení.  
  
#### <a name="paths-to-root"></a>Cesty ke kořenu  
  
-   Pro typ vybrali **typ objektu** tabulky, **cesty ke kořenu** tabulce jsou uvedeny jedinečný typ hierarchie, které vedou k kořenové objekty pro všechny objekty typu spolu s počtem odkazů na typ, který je nad ním v hierarchii.  
  
-   Vybrat z instance typu, objektu **cesty ke kořenu** zobrazuje graf skutečných objektů, které obsahují odkaz na instanci. Název objektu k zobrazení hodnot dat v popisu dat můžete myši.  
  
#### <a name="referenced-types--referenced-objects"></a>Odkazované typy / odkazované objekty  
  
- Pro typ vybrali **typ objektu** tabulky, **odkazované typy** karta zobrazuje velikosti a počtu odkazovaných typů drží všech objektů vybraného typu.  
  
- Pro vybranou instanci typu **odkazované objekty** zobrazí objekty, které jsou uloženy ve vybrané instanci. Při najetí myší na název zobrazíte jeho hodnoty dat v popisu dat.  
  
  **Cyklické odkazy**  
  
  Druhý objekt, který přímo nebo nepřímo obsahuje odkaz na první objekt, který můžete odkazovat na objekt. Když v analyzátoru paměti dojde této situaci, přestane rozšíření cestu odkazu a přidá **[zjištěn cyklus]** poznámky na výpis prvního objektu a zastaví.  
  
  **Typy kořenové**  
  
  Analyzátor paměti přidá do kořenové objekty, které popisují typ odkazu, který se koná poznámky:  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**Statická proměnná** `VariableName`|Statická proměnná. `VariableName` je název proměnné.|  
|**Popisovač finalizace**|Odkaz z fronta finalizační metody|  
|**Lokální proměnná**|Místní proměnné.|  
|**Silný popisovač**|Popisovač silného odkazu z tabulky popisovač objektu.|  
|**Asynchronní. Připojený popisovač**|Asynchronní objekt připnuté z tabulky popisovač objektu.|  
|**Závislý popisovač**|Závislý objekt z tabulky popisovač objektu.|  
|**Připojený popisovač**|Připnuté silného odkazu z tabulky popisovač objektu.|  
|**Popisovač RefCount**|Referenčně započítaný objekt z tabulky popisovač objektu.|  
|**Popisovač Sizedref**|Silný popisovač, který udržuje přibližné velikosti kolektivní ukončení všech objektů a objektů kořeny během uvolňování paměti kolekce.|  
|**Připnutá lokální proměnná**|Připojenou lokální proměnnou.|  
  
###  <a name="BKMK_Compare_two_memory_snapshots"></a> Porovnání dvou snímků paměti  
 Můžete porovnat dva soubory s výpisem paměti procesu k nalezení objektů, které mohou být příčinou nevracení paměti. Interval mezi sadu první (dříve) a druhé (k tomu později) soubor by měl být dostatečně velký, že nárůst počtu uniklé objektů je snadno zřejmý. Chcete-li porovnat dva soubory:  
  
1. Otevřete druhý soubor s výpisem paměti a klikněte na tlačítko **ladit spravovanou paměť** na **soubor souhrnu minimálního výpisu** stránky.  
  
2. Na stránce sestavy analýzy paměti, spusťte **vyberte směrný plán** seznamu a klikněte na tlačítko **Procházet** k určení prvního souboru s výpisem paměti.  
  
   Analyzátor přidá sloupce do horní podokno sestavy, který zobrazí rozdíl mezi **počet**, **velikost**, a **celkové velikosti** typy těchto hodnot předchozí snímek.  
  
   ![Diff sloupců v seznamu typ](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   A **rozdíl počtu odkazů** sloupec je taky přidaný ke **cesty ke kořenu** tabulky.  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
## <a name="see-also"></a>Viz také  
 [Blog VS ALM TFS: Pomocí sady Visual Studio 2013 k diagnostice problémů paměti rozhraní .NET v produkčním prostředí](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Na webu Channel 9 &#124; sady Visual Studio TV &#124; spravovaná analýza paměti](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Na webu Channel 9 &#124; nástrojů sady Visual Studio &#124; spravované paměti analýzy v sadě Visual Studio 2013](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)