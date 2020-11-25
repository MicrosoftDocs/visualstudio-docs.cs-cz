---
title: Použití souborů výpisu paměti v ladicím programu | Microsoft Docs
ms.custom: seodec18
ms.date: 11/05/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbfd8ac877fce4b1808a76e3bb2a66ac595693de
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970618"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Soubory s výpisem paměti v ladicím programu sady Visual Studio

<a name="BKMK_What_is_a_dump_file_"></a>*Soubor výpisu paměti* je snímek, který znázorňuje proces, který byl spuštěn, a moduly, které byly načteny pro aplikaci v určitém časovém okamžiku. Výpis paměti s informacemi o haldě zahrnuje také snímek paměti aplikace v daném okamžiku.

Otevření souboru s výpisem paměti s haldou v aplikaci Visual Studio je něco jako zastavení na zarážce v ladicí relaci. I když nemůžete pokračovat v provádění, můžete prostudovat zásobníky, vlákna a proměnné hodnoty aplikace v době výpisu.

Výpisy paměti se většinou používají k ladění problémů z počítačů, ke kterým nemají přístup vývojáři. Můžete použít soubor s výpisem paměti z počítače zákazníka, pokud nemůžete reprodukování chybně nebo nereagující program na vašem počítači. Testery taky vytvoří výpisy paměti, aby ušetřili chyby nebo nereagující data programu, která se mají použít pro další testování.

Ladicí program Visual Studio může uložit soubory s výpisem paměti pro spravovaný nebo nativní kód. Může ladit soubory výpisu paměti vytvořené pomocí sady Visual Studio nebo jiné aplikace, které ukládají soubory ve formátu *s minimálním výpisem* .

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Požadavky a omezení

- Chcete-li ladit soubory výpisu paměti z 64-bitových počítačů, musí být v systému Visual Studio spuštěna na 64 počítači.

- Visual Studio můžete ladit soubory s výpisem paměti nativních aplikaci ze zařízení ARM. Může taky ladit výpisy spravovaných aplikací ze zařízení ARM, ale jenom v nativním ladicím programu.

- Chcete-li ladit soubory výpisu paměti [režimu jádra](/windows-hardware/drivers/debugger/kernel-mode-dump-files) nebo použít rozšíření [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) ladění v sadě Visual Studio, Stáhněte si ladicí nástroje pro systém Windows v [sadě Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

- Visual Studio nemůže ladit soubory výpisu paměti uložené ve starším formátu [výpisu paměti v celém uživatelském režimu](/windows/desktop/wer/collecting-user-mode-dumps) . Úplný výpis paměti v uživatelském režimu není stejný jako výpis paměti s haldou.

- Ladění souborů s výpisem paměti pro optimalizaci kódu může být matoucí. Například vkládání kompilátoru funkcí může mít za následek neočekávané zásobníky volání a jiné optimalizace mohou změnit životnost proměnných.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> Soubory s výpisem paměti s haldami nebo bez haldy

Soubory výpisu paměti mohou nebo nemusí obsahovat informace o haldě.

- **Soubory s výpisem paměti s haldami** obsahují snímek paměti aplikace, včetně hodnot proměnných, v době výpisu. Visual Studio také ukládá binární soubory načtených nativních modulů v souboru s výpisem paměti s haldou, což může být ladění mnohem snazší. Visual Studio může načíst symboly ze souboru s výpisem paměti s haldou, a to i v případě, že nemůže najít binární soubor aplikace.

- **Soubory výpisu paměti bez hald** jsou mnohem menší než výpisy paměti s haldami, ale ladicí program musí načíst binární soubory aplikace, aby mohl najít informace o symbolech. Načtené binární soubory se musí přesně shodovat s těmi, které jsou spuštěny během vytváření výpisu paměti. Soubory s výpisem paměti bez haldy uloží pouze hodnoty proměnných zásobníku.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Vytvoření souboru s výpisem paměti

Při ladění procesu v aplikaci Visual Studio můžete uložit výpis paměti, když se ladicí program zastaví na výjimku nebo zarážku.

Když je povoleno [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md) , můžete připojit ladicí program sady Visual Studio k selhání procesu mimo aplikaci Visual Studio a následně uložit soubor s výpisem paměti z ladicího programu. Viz [připojit ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Uložení souboru s výpisem paměti:**

1. Při zastavení při chybě nebo zarážce během ladění vyberte **ladit**  >  **Uložit výpis jako**.

1. V dialogovém okně **Uložit výpis paměti jako** v části **Uložit jako typ** vyberte možnost **s minimálním výpisem** nebo **s minimálním výpisem s haldou** (výchozí).

1. Přejděte k cestě a vyberte název souboru s výpisem paměti a pak vyberte **Uložit**.

>[!NOTE]
>Soubory s výpisem paměti můžete vytvořit pomocí libovolného programu, který podporuje formát s minimálním výpisem Windows. Například nástroj příkazového řádku **ProcDump** ze [systému Windows Sysinternals](/sysinternals/) může vytvořit soubory s výpisem stavu systému procesu v závislosti na triggerech nebo na vyžádání. V tématu [požadavky a omezení](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) najdete informace o použití jiných nástrojů pro vytváření souborů s výpisem paměti.

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Otevření souboru s výpisem paměti

1. V aplikaci Visual Studio vyberte **soubor**  >  **otevřít**  >  **soubor**.

1. V dialogovém okně **otevřít soubor** vyhledejte a vyberte soubor s výpisem paměti. Obvykle bude mít příponu *. dmp* . Vyberte **OK**.

   V okně **Souhrn souboru s minimálním výpisem** se zobrazí souhrn a informace o modulu pro soubor s výpisem paměti a akce, které můžete provést.

   ![Souhrnná stránka s minimálním výpisem](../debugger/media/dbg_dump_summarypage.png "Souhrnná stránka s minimálním výpisem")

1. V části **Akce**:
   - Chcete-li nastavit umístění pro načítání symbolů, vyberte možnost **nastavit cesty k symbolům**.
   - Chcete-li spustit ladění, vyberte možnost **ladit pouze se spravovanými**, **ladit pouze s nativním**, **laděním se smíšeným** nebo **laděním pomocí spravované paměti**.

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Najít. exe,. pdb a zdrojové soubory

Pro použití úplných funkcí ladění pro soubor s výpisem paměti vyžaduje aplikace Visual Studio:

- Soubor *. exe* , pro který byl vytvořen výpis paměti, a další binární soubory (knihovny DLL atd.), které použil proces výpisu paměti.
- Soubory symbolů (*PDB*) pro soubor *. exe* a další binární soubory.
- Soubory *. exe* a *. pdb* , které přesně odpovídají verzi a sestavení souborů při vytváření výpisu.
- Zdrojové soubory pro příslušné moduly. Pokud nemůžete najít zdrojové soubory, můžete použít zpětný překlad modulů.

Pokud má výpis dat haldy, sada Visual Studio se může vypořádat s chybějícími binárními soubory pro některé moduly, ale musí mít binární soubory pro dostatek modulů, aby mohla vygenerovat platné zásobníky volání.

### <a name="search-paths-for-exe-files"></a>Cesty hledání pro soubory. exe

Visual Studio automaticky vyhledá tato umístění pro soubory *. exe* , které nejsou zahrnuté v souboru s výpisem paměti:

1. Složka, která obsahuje soubor s výpisem paměti.
2. Cesta k modulu, který obsahuje soubor s výpisem paměti, což je cesta modulu v počítači, kde je výpis paměti shromážděn.
3. Cesty symbolů zadané v **nástrojích** (nebo **ladění**) > **Možnosti**  >  **ladění**  >  **symbolů**. Můžete také otevřít stránku **symboly** z podokna **Akce** okna **Souhrn souboru výpisu** . Na této stránce můžete přidat další umístění pro hledání.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Použití žádného binárního souboru, žádných symbolů nebo stránek nenalezených zdrojů

Pokud Visual Studio nemůže najít soubory potřebné k ladění modulu ve výpisu paměti, zobrazí se **žádný binární soubor**, **nenašly se žádné symboly** nebo se **nenašly žádné zdrojové** stránky. Tyto stránky obsahují podrobné informace o příčině problému a poskytují odkazy na akce, které vám mohou pomáhat při hledání souborů. Viz [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Viz také

- [Ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)