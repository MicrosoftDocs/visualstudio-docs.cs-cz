---
title: Ukládání informací o symbolech pomocí datových souborů výkonu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9d2e8b0414746523d0f76e8266f6463d9c05574
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160288"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Ukládání informací o symbolech se soubory s údaji o výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k analýze souborů používáte integrované vývojové prostředí (IDE) a chcete soubor VSP přesunout do jiného počítače, musíte nastavit nastavení projektu výkonu pro ukládání nebo *serializaci* symbolů v souboru sestavy. Tím se zvětší velikost souboru sestavy. Serializace symbolů je nutná ze dvou důvodů:  
  
- Pro vložení symbolů kódu do sestavy o výkonu před tím, než jsou cílová sestavení ztracena z jejich umístění v dočasném úložišti.  
  
- Chcete-li zachovat symboly, aby sestava výkonu byla přenosná z profilované počítače, a vypíše stejné informace, pokud je sestava otevřena pro analýzu na jiném počítači, což může mít různé symboly.  
  
  **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Můžete serializovat symboly z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE) nebo z příkazového řádku:  
  
- Chcete-li serializovat symboly v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí, přejděte na panel nabídek **nástroje** a potom klikněte na tlačítko **Možnosti**. V okně **Možnosti** vyberte nástroje pro **sledování výkonu**a pak zaškrtněte políčko **automaticky serializovat informace o symbolech** .  
  
- PACKSYMBOLS je ekvivalentní možnost příkazového řádku při ukládání souborů sestav. K serializaci symbolů zadejte **VSPerfReport/Summary: ALL/packsymbols filename. vsp**.  
  
## <a name="troubleshooting-symbol-problems"></a>Řešení potíží se symboly  
 Pokud nevidíte žádné symboly ve vlastním kódu, jsou k dispozici některá běžná řešení:  
  
- Spusťte VSPerfReport/debugsympath na příkazovém řádku pro zobrazení úplného seznamu umístění, kde komponenty profileru načítají informace o symbolech a zda se použité soubory symbolů shodují se soubory, které váš projekt používá.  
  
- Ujistěte se, že jste spustili VSPerfReport pomocí příznaku/PACKSYMBOLS nebo v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE), že máte vybranou možnost informace o serializaci, kterou jste vybrali v části Obecné možnosti Průzkumníka výkonu.  
  
- Pokud jste shromáždili data typu, přidejte/SUMMARY: TYPE do příkazového řádku VSPerfReport.  
  
  Pokud nevidíte symboly z Windows nebo jiných programů Microsoftu:  
  
- Ujistěte se, že jste nastavili cestu k mezipaměti symbolů Windows. Chcete-li nastavit cestu k mezipaměti symbolů, proveďte jednu z následujících akcí:  
  
  - V integrovaném vývojovém prostředí nastavte možnost ladicí program->symboly na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] správnou cestu.  
  
  - Přidejte do příkazového řádku VSPerfReport možnost-SymbolPath, aby se zahrnuly vaše symboly.  
  
- Pokud v nástroji nevidíte žádné symboly [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , ujistěte se, že je správně nastavený symbolový server pro server ASP.  
  
## <a name="repacking-symbols"></a>Opětovné balení symbolů  
 Pokud chcete znovu zabalit symboly do sestavy, můžete k tomu použít nástroj příkazového řádku VsPerfReport. Použijte následující příkazové řádky:  
  
 VsPerfReport-clearpackedsymbols název_souboru. vsp  
  
 VsPerfReport-packsymbols-Summary: ALL filename. vsp  
  
## <a name="see-also"></a>Viz také  
 [Ukládání a export dat nástrojů pro sledování výkonu](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Postupy: odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
