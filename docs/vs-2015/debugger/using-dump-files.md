---
title: Použití souborů výpisu paměti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 1a2d6215887512f2e0c1410688b2bc924dc1fe3a
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387054"
---
# <a name="using-dump-files"></a>Použití souborů výpisu paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soubory s výpisem paměti s nebo bez haldy –vytvořte soubor s výpisem, otevřete jej, vyhledejte binární soubory, PDB a zdrojový soubor souboru s výpisem. 
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Obsah  
 [Co je soubor s výpisem paměti?](#BKMK_What_is_a_dump_file_)  
  
 [Soubory s výpisem paměti s haldami nebo bez](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Požadavky a omezení](#BKMK_Requirements_and_limitations)  
  
 [Vytvoření souboru s výpisem paměti](#BKMK_Create_a_dump_file)  
  
 [Otevření souboru s výpisem paměti](#BKMK_Open_a_dump_file)  
  
 [Najít binární soubory, soubory symbolů (PDB) a zdrojové soubory](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
## <a name="what-is-a-dump-file"></a><a name="BKMK_What_is_a_dump_file_"></a>Co je soubor s výpisem paměti?  
 *Soubor výpisu paměti* je snímek aplikace v bodě v čase, kdy je výpis paměti pořízen. Ukazuje, jaký proces probíhal a které moduly byly načteny. Pokud byl výpis paměti uložen s informacemi o haldě, soubor s výpisem paměti obsahuje snímek toho, co bylo v paměti aplikace v daném okamžiku. Otevření souboru s výpisem paměti pomocí haldy v sadě Visual Studio odpovídá zastavení na zarážce v ladicí relaci. Ačkoli nelze pokračovat v provádění, můžete zkoumat zásobníky, vlákna a proměnné hodnoty aplikace v době, kdy došlo k výpisu paměti.  
  
 Výpisy paměti se používají především pro ladění problémů, ke kterým dochází v počítačích, ke kterým nemá vývojář přístup. Můžete například použít soubor s výpisem paměti z počítače zákazníka, pokud nemůžete reprodukování programu nebo nereagující programu zákazníka v počítači. Výpisy paměti jsou vytvářeny také testery k ukládání chybných nebo nereagujících programových dat, aby bylo možné testovací počítač použít pro další testování. Ladicí program Visual Studio může uložit soubory s výpisem paměti pro spravovaný nebo nativní kód. Ladicí program může načíst soubory s výpisem paměti, které byly vytvořeny pomocí aplikace Visual Studio, nebo jinými programy, které ukládají soubory ve formátu *s minimálním výpisem* .  
  
 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a>Soubory s výpisem paměti s haldami nebo bez  
 Můžete vytvořit soubory s výpisem paměti s informacemi o haldě nebo bez nich.  
  
- **Soubory s výpisem paměti s haldami** obsahují snímek paměti aplikace. Zahrnuje hodnoty proměnných v době, kdy byl vytvořen výpis paměti. Pokud načtete soubor s výpisem paměti, který byl uložen s haldou, sada Visual Studio může načíst symboly i v případě, že binární soubor aplikace není nalezen. Visual Studio také ukládá binární verze načtených nativních modulů v souboru s výpisem paměti, díky čemu může být ladění mnohem snazší.  
  
- **Soubory výpisu paměti bez haldy** jsou mnohem menší než výpisy paměti s informacemi o haldě. Ladicí program má však načíst binární soubory aplikace a nalézt tak informace o symbolu. Binární soubory musí být přesná shoda binárních souborů, které byly použity při vytvoření výpisu paměti. Pouze hodnoty proměnných zásobníku jsou ukládány do souborů výpisu paměti bez dat haldy.  
  
  ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a>Požadavky a omezení  
  
- Ladění souborů s výpisem paměti pro optimalizaci kódu může být matoucí. Například vkládání funkcí kompilátoru může mít za následek neočekávané volání zásobníků a další optimalizace může upravit délku platnosti proměnných.  
  
- Soubory s výpisem paměti u 64bitových počítačů je nutné ladit v instanci aplikace Visual Studio, která běží na 64bitovém počítači.  
  
- Ve verzích sady Visual Studio před verzí 2013 výpisy paměti 32bitových aplikací běžících v 64bitových počítačích, které byly shromážděny pomocí některých nástrojů (například Správce úloh a WinDbg v 64bitové verzi) nelze otevřít v sadě Visual Studio. Toto omezení bylo ve verzi 2013 odebráno.  
  
- Visual Studio můžete ladit soubory s výpisem paměti nativních aplikaci ze zařízení ARM. Visual Studio může také ladit soubory s výpisem paměti aplikací spravovaných aplikace ze zařízení ARM, avšak pouze v nativním ladicím programu.  
  
- Chcete-li ladit soubory výpisu paměti [režimu jádra](https://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) v nástroji Visual Studio 2013, stáhněte [Windows 8.1 verzi ladicích nástrojů pro systém Windows](https://msdn.microsoft.com/windows/hardware/gg463009). Viz [ladění jádra v aplikaci Visual Studio](https://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- Visual Studio nemůže ladit soubory výpisu paměti uložené ve starším formátu výpisu, který je známý jako [úplný výpis paměti v uživatelském režimu](/windows-hardware/drivers/debugger/user-mode-dump-files#full). Pamatujte, že výpis paměti s úplným uživatelským režimem není stejný jako výpis s daty haldy.  
  
- Chcete-li ladit s [SOS.dll (rozšíření ladění SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) v sadě Visual Studio, je nutné nainstalovat ladicí nástroje pro systém Windows, které jsou součástí sady Windows Driver Kit (WDK). Viz [Windows 8.1 Preview: stažení sad, bitů a nástrojů](https://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a>Vytvoření souboru s výpisem paměti  
 Vytvoření souboru s výpisem paměti pomocí aplikace Visual Studio:  
  
- Při ladění procesu v aplikaci Visual Studio, můžete uložit soubor s výpisem paměti, když se ladicí program zastaví na výjimce nebo v bodu přerušení. Vyberte možnost **Uložit výpis jako**, **ladit**. V dialogovém okně **Uložit výpis paměti jako** v seznamu **Uložit jako typ** můžete vybrat možnost **s minimálním výpisem** nebo **s minimálním výpisem s haldou** (výchozí).  
  
- Když je povoleno [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md) , můžete připojit ladicí program k neúspěšnému procesu, který je spuštěn mimo ladicí program, a následně uložit soubor s výpisem paměti. Viz [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  Můžete také vytvořit soubory s výpisem paměti pomocí libovolného programu, který podporuje formát minimálního výpisu Windows. Například nástroj příkazového řádku **ProcDump** ze [systému Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) může vytvořit soubory s výpisem stavu systému procesu v závislosti na triggerech nebo na vyžádání. Další informace o používání dalších nástrojů k vytváření souborů s výpisem paměti najdete v tématu [požadavky a omezení](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) v tomto tématu.  
  
  ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a>Otevření souboru s výpisem paměti  
  
1. V aplikaci Visual Studio vyberte **soubor**, **otevřít**, **soubor**.  
  
2. V dialogovém okně **otevřít soubor** vyhledejte a vyberte soubor s výpisem paměti. Obvykle má příponu .dmp. Pak zvolte **OK**.  
  
3. Zobrazí se okno **Souhrn souborů výpisu paměti** . V tomto okně můžete zobrazit souhrnné informace o ladění pro soubor s výpisem paměti, nastavit cestu symbolů, spustit ladění a souhrnné informace zkopírovat do schránky.  
  
     ![Souhrnná stránka s minimálním výpisem](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4. Chcete-li spustit ladění, přejít do části **Akce** a vyberte buď možnost **ladění pouze s nativním** rozhraním, nebo **ladění se smíšeným**režimem.  
  
## <a name="find-binaries-symbol-pdb-files-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a>Najít binární soubory, soubory symbolů (PDB) a zdrojové soubory  
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
  
3. Cesty symbolů zadané na stránce **ladění**, **Možnosti**, **symboly** dialogového okna **nástroje**sady Visual Studio, dialogové okno **Možnosti** . Můžete přidat více míst pro vyhledávání na této stránce.  
  
   **Použití stránky bez binárních souborů, symbolů a zdrojů**  
  
   Pokud Visual Studio nemůže najít soubory potřebné k ladění modulu ve výpisu paměti, zobrazí odpovídající stránku (nebyl**nalezen žádný binární soubor**, nebyl **nalezen žádný symbol**nebo **nebyl nalezen žádný zdroj**). Tyto stránky obsahují podrobné informace o příčině problému a poskytují odkazy na akce, které vám mohou pomoci identifikovat správné umístění souborů. Viz [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="see-also"></a>Viz také  
 [Ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)
