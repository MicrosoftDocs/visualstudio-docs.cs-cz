---
title: Ukládání informací o symbolech pomocí datových souborů výkonu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 74137752900d082c545dd5e5271b7700ec81fa01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778294"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Ukládání informací o symbolech se soubory s údaji o výkonu

Pokud používáte ide sady Visual Studio k analýze souborů a plánujete přesunout soubor VSP do jiného počítače, je nutné nastavit nastavení projektu výkonu pro uložení nebo *serializaci* symbolů v souboru sestavy. Tím se zvětší velikost souboru sestavy. Serializace symbolů je nezbytná ze dvou důvodů:

- Chcete-li vložit symboly kódu do sestavy výkonu před cílové sestavení jsou ztraceny z jejich umístění v dočasném úložišti.

- Chcete-li zachovat symboly, tak, aby zpráva o výkonu je přenosný z profilovaného počítače a výstupy stejné informace, pokud je sestava otevřena pro analýzu v jiném počítači, který může mít různé symboly.

Symboly můžete serializovat z ide sady Visual Studio nebo z příkazového řádku:

- Chcete-li v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prostředí IDE serializovat symboly, přejděte na panelu nabídek na **položku Nástroje** a klepněte na příkaz **Možnosti**. V okně **Možnosti** vyberte **Nástroje výkonu**a zaškrtněte políčko **Automaticky serializovat informace o symbolu.**

- PACKSYMBOLS je ekvivalentní možnost příkazového řádku při ukládání souborů sestavy. Chcete-li serializovat symboly, zadejte **vsperfreport /summary:all /packsymbols filename.vsp**.

## <a name="troubleshooting-symbol-problems"></a>Poradce při potížích se symboly

Pokud ve vlastním kódu nevidíte žádné symboly, jsou k dispozici některá běžná řešení:

- Spusťte vsperfreport /debugsympath na příkazovém řádku a zobrazte úplný seznam umístění, kde komponenty profileru načítají informace o symbolech a zda se používané soubory symbolů shodují se soubory, které projekt používá.

- Ujistěte se, že spustíte vsperfreport s příznakem /PACKSYMBOLS nebo v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozhraní IDE, že máte možnost serializovat informace o symbolu vybranou v obecných možnostech průzkumníka výkonu.

- Pokud jste shromáždili data typu, přidejte /SUMMARY:TYPE do příkazového řádku vsperfreport.

  Pokud nevidíte symboly ze systému Windows nebo jiných programů společnosti Microsoft:

- Ujistěte se, že jste nastavili cestu mezipaměť symbolů systému Windows. Chcete-li nastavit cestu mezipaměti symbolů, proveďte jeden z následujících akcí:

  - Nastavte volbu Symboly >ladicího programu v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ide na správnou cestu.

  - Přidejte volbu -symbolpath do příkazového řádku VSPerfReport, aby obsahovala vaše symboly.

- Pokud v [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]aplikaci nevidíte žádné symboly , ujistěte se, že je server symbolů správně nastaven pro server ASP.

## <a name="repacking-symbols"></a>Přebalování symbolů

Pokud chcete znovu zabalit symboly do sestavy, můžete to provést pomocí nástroje příkazového řádku VsPerfReport. Použijte následující příkazové řádky:

VsPerfReport -clearpackedsymbols filename.vsp

VsPerfReport -packsymbols -summary:all filename.vsp

## <a name="see-also"></a>Viz také

[Ukládání a export dat](../profiling/saving-and-exporting-performance-tools-data.md)
nástrojů výkonu[Postup: Odkaz na informace o symbolu](../profiling/how-to-reference-windows-symbol-information.md)
systému Windows[VSPerfReport](../profiling/vsperfreport.md)
