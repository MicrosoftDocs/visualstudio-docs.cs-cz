---
title: Použití souborů výpisu paměti v ladicím programu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e30f9d29ba3c922d70c8acdf7d4db5d8a1670fd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066951"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Soubory s výpisem paměti v ladicím programu sady Visual Studio

<a name="BKMK_What_is_a_dump_file_"></a> A *soubor s výpisem paměti* je snímek, který popisuje proces, která byla spuštěna a moduly, které byly načteny pro aplikace v bodě v čase. Výpis paměti s informacemi o haldě také obsahují i snímek paměti aplikace v daném okamžiku. 

Otevřete soubor s výpisem paměti s haldou v sadě Visual Studio je něco jako je zastavení na zarážce v ladicí relaci. Ačkoli nelze pokračovat v provádění, můžete zkoumat zásobníky, vlákna a proměnné hodnoty aplikace v okamžiku výpisu paměti.

Výpisy paměti se nejčastěji používají pro ladění problémů z počítače, které vývojářům nemají přístup k. Soubor s výpisem paměti z počítače zákazníka můžete použít, když nelze reprodukovat zhroucení nebo zablokování, na svém počítači. Testerům vytvářet také výpisy stavu uložit zhroucení nebo zablokování, data se mají použít pro další testování. 

Ladicí program Visual Studio může uložit soubory s výpisem paměti pro spravovaný nebo nativní kód. To můžete ladit soubory výpisu stavu systému vytvořené pomocí sady Visual Studio nebo jinými aplikacemi, které ukládají soubory ve *s minimálním výpisem* formátu.

##  <a name="BKMK_Requirements_and_limitations"></a> Požadavky a omezení

-   Chcete-li ladit soubory s výpisem paměti z 64bitové počítače se systémem Visual Studio musí běžet na 64bitovém počítači.

-   Visual Studio můžete ladit soubory s výpisem paměti nativních aplikaci ze zařízení ARM. Můžete také ladit výpisy spravovaných aplikací ze zařízení ARM, ale pouze v nativním ladicím programu.

-   Chcete-li ladit [režimu jádra](/windows-hardware/drivers/debugger/kernel-mode-dump-files) soubory s výpisem paměti, nebo použijte [knihovny SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) ladění rozšíření v sadě Visual Studio, stáhněte si nástroje pro ladění pro Windows v [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

-   Visual Studio nemůže ladit soubory s výpisem paměti uložené ve starším, [úplným uživatelským režimem výpisu](/windows/desktop/wer/collecting-user-mode-dumps) formátu. S výpisem paměti úplným uživatelským režimem není stejný jako výpis s haldou.

-   Ladění souborů s výpisem paměti pro optimalizaci kódu může být matoucí. Například vkládání funkcí kompilátoru může mít za následek neočekávané volání zásobníků a další optimalizace může upravit platnosti proměnných.

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Soubory s výpisem paměti s haldou nebo bez haldy

Soubory s výpisem paměti může nebo nemusí mít informace o haldě.

-   **Soubory s haldou výpisu paměti** obsahují snímek paměti aplikace, včetně hodnot proměnných, v okamžiku výpisu paměti. Visual Studio také ukládá binární verze načtených nativních modulů v souboru s výpisem paměti s haldou, což může být ladění mnohem snazší. Visual Studio můžete načíst symboly z soubor s výpisem paměti s haldou, i v případě, že aplikace nemůže najít binární. 

-   **Výpis paměti bez haldy soubory** jsou mnohem menší než výpisů paměti s haldou, ale ladicí program musí načíst binární soubory aplikace k nalezení informací o symbolu. Načíst binární soubory musí přesně odpovídat těm, které jsou během vytváření s výpisem paměti. Soubory s výpisem paměti bez haldy uložit hodnoty proměnných zásobníku pouze.

##  <a name="BKMK_Create_a_dump_file"></a> Vytvoření souboru výpisu paměti

Při ladění procesu v sadě Visual Studio, můžete uložit výpis paměti, když ladicí program zastaví na výjimce nebo zarážku. 

S [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md) povolená, můžete připojit ladicí program sady Visual Studio k neúspěšnému procesu mimo sadu Visual Studio a následně uložit soubor s výpisem paměti z ladicího programu. Zobrazit [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Uložte soubor s výpisem paměti:**

1. Při zastavení na chybu nebo zarážce při ladění, vyberte **ladění** > **uložit výpis paměti jako**. 

1. V **uložit výpis paměti jako** dialogovém okně **uložit jako typ**vyberte **s minimálním výpisem** nebo **minimální výpis s haldou** (výchozí).

1. Vyhledejte cestu a název souboru s výpisem paměti vyberte a pak vyberte **Uložit**. 

>[!NOTE]
>Můžete vytvořit soubory s výpisem paměti pomocí libovolného programu, který podporuje formát minimálního výpisu Windows. Například **Procdump** nástroj příkazového řádku z [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) můžete vytvořit soubory s výpisem paměti při selhání procesu na základě aktivační události nebo na vyžádání. Zobrazit [požadavky a omezení](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) informace o použití jiných nástrojů pro vytváření souborů s výpisem paměti.

##  <a name="BKMK_Open_a_dump_file"></a> Otevřete souboru výpisu paměti

1. V sadě Visual Studio, vyberte **souboru** > **otevřít** > **souboru**.

1. V **otevřít soubor** dialogového okna, vyhledejte a vyberte soubor s výpisem paměti. Obvykle bude mít *.dmp* rozšíření. Vyberte **OK**.

   **s minimálním výpisem soubor souhrnu** okno s informacemi summary a modulu pro soubor s výpisem paměti a akce může trvat.

   ![Stránka souhrnu minimálního výpisu](../debugger/media/dbg_dump_summarypage.png "stránka souhrnu minimálního výpisu")

1. V části **akce**:
   - Chcete-li nastavit načítání umístění symbolů, vyberte **nastavit cesty symbolu**.
   - Chcete-li spustit ladění, vyberte **ladit spravované pouze**, **ladit pouze nativní**, **ladit s různými typy**, nebo **ladit spravovanou paměť**.

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Najít .exe, .pdb a zdrojové soubory

Používat úplné funkce na soubor s výpisem paměti ladění sady Visual Studio potřebuje:

- *.Exe* souboru výpisu paměti bylo vytvořeno za a další binárních souborů (knihovny DLL, atd.), které používají procesu s výpisem paměti.
- Symbol (*PDB*) soubory *.exe* a další binární soubory.
- *.Exe* a *PDB* soubory, které přesně odpovídají verzi a sestavení soubory výpisu paměti vytváření.
- Zdrojové soubory pro příslušné moduly. Pokud nemůžete najít zdrojové soubory, můžete použít zpětného překladu modulů.

Pokud je výpis paměti haldy data, Visual Studio se může vypořádat s chybějícími binárními soubory pro některé moduly, ale musí mít binární soubory pro dostatek modulů, chcete-li vygenerovat platné zásobníky volání. 

### <a name="search-paths-for-exe-files"></a>Cesty hledání pro soubory .exe

Visual Studio automaticky hledá v těchto umístěních *.exe* soubory, které nejsou zahrnuty v souboru s výpisem paměti:

1. Tato složka obsahuje soubor s výpisem paměti.
2. Cesta modulu souboru s výpisem paměti určuje, který je cesta modulu na počítači, který slouží ke shromažďování výpisu paměti.
3. Cesty symbolů zadané v **nástroje** (nebo **ladění**) > **možnosti** > **ladění**  >  **Symboly**. Můžete také otevřít **symboly** stránku ze **akce** podokně **souhrn souborů výpisu paměti** okna. Na této stránce můžete přidat více míst pro vyhledávání.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Použití stránek ne binární, ne symboly nebo nebyl nalezen žádný zdroj

Pokud aplikace Visual Studio nemůže najít soubory potřebuje k ladění modulu ve výpisu paměti, zobrazuje **nalezen žádný binární soubor**, **nebyl nalezen žádný symbol**, nebo **nebyl nalezen žádný zdroj** stránky. Tyto stránky obsahují podrobné informace o příčině problému a poskytují odkazy na akce, které vám pomůžou najít soubory. Zobrazit [zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Viz také:

- [Ladění Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)