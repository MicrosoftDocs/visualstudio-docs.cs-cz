---
title: Ukládání informací o symbolech pomocí datových souborů výkonu | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778294"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Ukládání informací o symbolech se soubory s údaji o výkonu

Pokud používáte Visual Studio IDE k analýze souborů a plánujete přesunout soubor VSP do jiného počítače, musíte nastavit nastavení projektu výkonu pro ukládání nebo *serializaci* symbolů v souboru sestavy. Tím se zvětší velikost souboru sestavy. Serializace symbolů je nutná ze dvou důvodů:

- Pro vložení symbolů kódu do sestavy o výkonu před tím, než jsou cílová sestavení ztracena z jejich umístění v dočasném úložišti.

- Chcete-li zachovat symboly, aby sestava výkonu byla přenosná z profilované počítače, a vypíše stejné informace, pokud je sestava otevřena pro analýzu na jiném počítači, což může mít různé symboly.

Můžete serializovat symboly z integrovaného vývojového prostředí (IDE) sady Visual Studio nebo z příkazového řádku:

- Chcete-li serializovat symboly v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí, přejděte na panel nabídek **nástroje** a pak klikněte na tlačítko **Možnosti**. V okně **Možnosti** vyberte nástroje pro **sledování výkonu**a pak zaškrtněte políčko **automaticky serializovat informace o symbolech** .

- PACKSYMBOLS je ekvivalentní možnost příkazového řádku při ukládání souborů sestav. K serializaci symbolů zadejte **VSPerfReport/Summary: ALL/packsymbols filename. vsp**.

## <a name="troubleshooting-symbol-problems"></a>Řešení potíží se symboly

Pokud nevidíte žádné symboly ve vlastním kódu, jsou k dispozici některá běžná řešení:

- Spusťte VSPerfReport/debugsympath na příkazovém řádku pro zobrazení úplného seznamu umístění, kde komponenty profileru načítají informace o symbolech a zda se použité soubory symbolů shodují se soubory, které váš projekt používá.

- Ujistěte se, že jste spustili VSPerfReport pomocí příznaku/PACKSYMBOLS nebo v prostředí IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], že máte vybranou možnost informace o serializaci symbolů v části Obecné možnosti Průzkumníka výkonu.

- Pokud jste shromáždili data typu, přidejte/SUMMARY: TYPE do příkazového řádku VSPerfReport.

  Pokud nevidíte symboly z Windows nebo jiných programů Microsoftu:

- Ujistěte se, že jste nastavili cestu k mezipaměti symbolů Windows. Chcete-li nastavit cestu k mezipaměti symbolů, proveďte jednu z následujících akcí:

  - Nastavte možnost ladicí program-> symboly v rozhraní IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na správnou cestu.

  - Přidejte do příkazového řádku VSPerfReport možnost-SymbolPath, aby se zahrnuly vaše symboly.

- Pokud nevidíte žádné symboly v [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], ujistěte se, že je správně nastavený symbolový server pro server ASP.

## <a name="repacking-symbols"></a>Opětovné balení symbolů

Pokud chcete znovu zabalit symboly do sestavy, můžete k tomu použít nástroj příkazového řádku VsPerfReport. Použijte následující příkazové řádky:

VsPerfReport-clearpackedsymbols název_souboru. vsp

VsPerfReport-packsymbols-Summary: ALL filename. vsp

## <a name="see-also"></a>Viz také:

[Ukládání a export dat nástrojů pro sledování výkonu](../profiling/saving-and-exporting-performance-tools-data.md)
[: odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)
[VSPerfReport](../profiling/vsperfreport.md)
