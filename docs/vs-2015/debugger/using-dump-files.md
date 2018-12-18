---
title: Použití souborů výpisu paměti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.crashdump
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 56
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c117e0aa7922c70f919a7b16fa6d40a447f2ce2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761138"
---
# <a name="using-dump-files"></a>Použití souborů výpisu paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soubory s výpisem paměti s nebo bez haldy –vytvořte soubor s výpisem, otevřete jej, vyhledejte binární soubory, PDB a zdrojový soubor souboru s výpisem. 
  
##  <a name="BKMK_Contents"></a> Obsah  
 [Co je soubor s výpisem paměti?](#BKMK_What_is_a_dump_file_)  
  
 [Soubory s výpisem paměti s haldou nebo bez haldy](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Požadavky a omezení](#BKMK_Requirements_and_limitations)  
  
 [Vytvoření souboru výpisu paměti](#BKMK_Create_a_dump_file)  
  
 [Otevřete souboru výpisu paměti](#BKMK_Open_a_dump_file)  
  
 [Najít binární soubory, soubory symbolů (PDB) a zdrojové soubory](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
##  <a name="BKMK_What_is_a_dump_file_"></a> Co je soubor s výpisem paměti?  
 A *soubor s výpisem paměti* je snímek aplikace v bodě v čase je výpis paměti pořízen. Ukazuje, jaký proces probíhal a které moduly byly načteny. Pokud byl výpis paměti uložen s informacemi o haldě, soubor s výpisem paměti obsahuje snímek toho, co bylo v paměti aplikace v daném okamžiku. Otevření souboru s výpisem paměti pomocí haldy v sadě Visual Studio odpovídá zastavení na zarážce v ladicí relaci. Ačkoli nelze pokračovat v provádění, můžete zkoumat zásobníky, vlákna a proměnné hodnoty aplikace v době, kdy došlo k výpisu paměti.  
  
 Výpisy paměti se používají především pro ladění problémů, ke kterým dochází v počítačích, ke kterým nemá vývojář přístup. Můžete například použít soubor s výpisem paměti z počítače zákazníka, pokud nelze ve vašem počítači reprodukovat situaci, kdy produkt zákazníka selže nebo přestane reagovat. Výpisy paměti jsou vytvářeny také testery, kteří v nich ukládají data o zhroucení nebo zablokování, aby bylo možné testovací počítač použít pro další testování. Ladicí program Visual Studio může uložit soubory s výpisem paměti pro spravovaný nebo nativní kód. Ladicí program můžete načíst soubory s výpisem paměti, které byly vytvořeny pomocí sady Visual Studio nebo jinými programy, které ukládají soubory ve *s minimálním výpisem* formátu.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Soubory s výpisem paměti s haldou nebo bez haldy  
 Můžete vytvořit soubory s výpisem paměti s informacemi o haldě nebo bez nich.  
  
- **Soubory s haldou výpisu paměti** obsahují snímek paměti aplikace. Zahrnuje hodnoty proměnných v době, kdy byl vytvořen výpis paměti. Pokud načtete soubor s výpisem paměti, který byl uložen s haldou, sada Visual Studio může načíst symboly i v případě, že binární soubor aplikace není nalezen. Visual Studio také ukládá binární verze načtených nativních modulů v souboru s výpisem paměti, díky čemu může být ladění mnohem snazší.  
  
- **Výpis paměti bez haldy soubory** jsou mnohem menší než výpisů paměti s informacemi o haldě. Ladicí program má však načíst binární soubory aplikace a nalézt tak informace o symbolu. Binární soubory musí být přesná shoda binárních souborů, které byly použity při vytvoření výpisu paměti. Pouze hodnoty proměnných zásobníku jsou ukládány do souborů výpisu paměti bez dat haldy.  
  
  ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Requirements_and_limitations"></a> Požadavky a omezení  
  
- Ladění souborů s výpisem paměti pro optimalizaci kódu může být matoucí. Například vkládání funkcí kompilátoru může mít za následek neočekávané volání zásobníků a další optimalizace může upravit délku platnosti proměnných.  
  
- Soubory s výpisem paměti u 64bitových počítačů je nutné ladit v instanci aplikace Visual Studio, která běží na 64bitovém počítači.  
  
- Ve verzích sady Visual Studio před verzí 2013 výpisy paměti 32bitových aplikací běžících v 64bitových počítačích, které byly shromážděny pomocí některých nástrojů (například Správce úloh a WinDbg v 64bitové verzi) nelze otevřít v sadě Visual Studio. Toto omezení bylo ve verzi 2013 odebráno.  
  
- Visual Studio můžete ladit soubory s výpisem paměti nativních aplikaci ze zařízení ARM. Visual Studio může také ladit soubory s výpisem paměti aplikací spravovaných aplikace ze zařízení ARM, avšak pouze v nativním ladicím programu.  
  
- Chcete-li ladit [režimu jádra](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) vypsat soubory v sadě Visual Studio 2013, stáhněte si [Windows 8.1 verze z ladění nástroje pro Windows](http://msdn.microsoft.com/windows/hardware/gg463009). Zobrazit [ladění jádra v aplikaci Visual Studio](http://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- Visual Studio nemůže ladit soubory s výpisem paměti uložené ve starším formátu výpisu, známé jako [úplným uživatelským režimem výpisu](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx). Pamatujte, že výpis paměti s úplným uživatelským režimem není stejný jako výpis s daty haldy.  
  
- Chcete-li ladit s [SOS.dll (SOS Debugging Extension)](http://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) v sadě Visual Studio, je nutné nainstalovat ladění nástroje pro Windows, který je součástí sad Windows Driver Kit (WDK). Zobrazit [Windows 8.1 Preview: stažení sad, bitů a nástrojů](http://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Create_a_dump_file"></a> Vytvoření souboru výpisu paměti  
 Vytvoření souboru s výpisem paměti pomocí aplikace Visual Studio:  
  
- Při ladění procesu v aplikaci Visual Studio, můžete uložit soubor s výpisem paměti, když se ladicí program zastaví na výjimce nebo v bodu přerušení. Zvolte **uložit výpis paměti jako**, **ladění**. V **uložit výpis paměti jako** v dialogu **uložit jako typ** seznamu můžete vybrat **s minimálním výpisem** nebo **minimální výpis s haldou** (výchozí).  
  
- S [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md) povolená, můžete připojit ladicí modul k neúspěšnému procesu, který běží mimo ladicí program a následně uložit soubor s výpisem paměti. Zobrazit [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  Můžete také vytvořit soubory s výpisem paměti pomocí libovolného programu, který podporuje formát minimálního výpisu Windows. Například **Procdump** nástroj příkazového řádku z [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) můžete vytvořit soubory s výpisem paměti při selhání procesu na základě aktivační události nebo na vyžádání. Zobrazit [požadavky a omezení](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) v tomto tématu pro další informace o použití jiných nástrojů pro vytváření souborů s výpisem paměti.  
  
  ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Open_a_dump_file"></a> Otevřete souboru výpisu paměti  
  
1.  V sadě Visual Studio, zvolte **souboru**, **otevřít**, **souboru**.  
  
2.  V **otevřít soubor** dialogového okna, vyhledejte a vyberte soubor s výpisem paměti. Obvykle má příponu .dmp. Klikněte na tlačítko **OK**.  
  
3.  **Souhrn souborů výpisu paměti** zobrazí se okno. V tomto okně můžete zobrazit souhrnné informace o ladění pro soubor s výpisem paměti, nastavit cestu symbolů, spustit ladění a souhrnné informace zkopírovat do schránky.  
  
     ![Stránka souhrnu minimálního výpisu](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4.  Chcete-li spustit ladění, přejděte **akce** a zvolte buď **ladit pouze nativní** nebo **ladit s různými typy**.  
  
##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Najít binární soubory, soubory symbolů (PDB) a zdrojové soubory  
 Chcete-li používat úplné funkce aplikace Visual Studio pro ladění souboru s výpisem paměti, potřebujete přístup k:  
  
- Soubor .exe, pro který byl pořízen výpis paměti přijatých a další binárních souborů (knihovny DLL, atd.), které byly použity v procesu s výpisem paměti.  
  
   Jestliže ladíte výpis paměti s daty haldy, sada Visual Studio se může vypořádat s chybějícími binárními soubory pro některé moduly, ale musí mít binární soubory pro dostatek modulů, aby mohla vygenerovat platné zásobníky volání. Visual Studio obsahuje nativní moduly v souboru s výpisem paměti s haldou.  
  
- Soubory symbolů (PDB) .exe a další binární soubory.  
  
- Zdrojové soubory pro moduly, které vás zajímají.  
  
   Spustitelné soubory a soubory PDB musí odpovídat přesně verzi a sestavení souborů použitých při tvorbě výpisu paměti.  
  
   Pokud nemůžete najít zdrojové soubory, můžete ladit pomocí zpětného překladu modulů,  
  
  **Výchozí vyhledávací cesty pro spustitelné soubory**  
  
  Visual Studio automaticky hledá v těchto umístěních spustitelné soubory, které nejsou zahrnuty v souboru s výpisem paměti:  
  
1. Adresář obsahující soubor s výpisem paměti.  
  
2. Cesta modulu, který je zadaný v souboru s výpisem paměti. Toto je cesta modulu v počítači, kde byl výpis paměti shromážděn.  
  
3. Cesty symbolů zadané **ladění**, **možnosti**, **symboly** stránku sady Visual Studio **nástroje**, **možnosti**  dialogové okno. Můžete přidat více míst pro vyhledávání na této stránce.  
  
   **Pomocí ne binární / Symbol / zdroj stránky**  
  
   Pokud aplikace Visual Studio nemůže najít soubory potřebné k ladění modulu ve výpisu paměti, zobrazí odpovídající stránku (**nalezen žádný binární soubor**, **nebyl nalezen žádný symbol**, nebo **nebyl nalezen žádný zdroj**). Tyto stránky obsahují podrobné informace o příčině problému a poskytují odkazy na akce, které vám mohou pomoci identifikovat správné umístění souborů. Zobrazit [zadání symbolu (.pdb) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
## <a name="see-also"></a>Viz také  
 [Ladění Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Zadání symbolu (.pdb) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)

