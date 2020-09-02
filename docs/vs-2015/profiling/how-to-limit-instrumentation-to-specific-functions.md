---
title: 'Postupy: omezení instrumentace na konkrétní funkce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8923323a3aed96a9dd441a4a36b2084ffd8197e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788030"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Postupy: Omezení instrumentace na konkrétní funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Instrumentaci a shromažďování dat můžete omezit na jednu nebo více funkcí tak, že nastavíte možnosti na stránce **Upřesnit** v části **relace výkonu** nebo cílové binární vlastnosti:  
  
- Pokud zadáte funkce na stránce vlastností relace výkonu, budou instrumentovat pouze tyto funkce v rámci všech instrumentované binárních souborů relace.  
  
- Zadáte-li funkce na stránce vlastností cílového binárního souboru, budou instrumentované pouze ty funkce, které jsou v tomto konkrétním binárním souboru. Funkce v dalších binárních souborech výkonu jsou instrumentované jako obvykle.  
  
  Omezení shromažďování dat tímto způsobem se podporuje jenom v případě, že je vybraná metoda profilace instrumentace.  
  
> [!NOTE]
> Můžete také použít stránku **Upřesnit** na stránce vlastností **relace výkonu** a nastavit další možnosti, které jsou k dispozici pro nástroj nástroje pro profilaci [VSInstr](../profiling/vsinstr.md) příkazového řádku nástroje pro instrumentaci.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Omezení instrumentace na konkrétní funkce v relaci výkonu  
  
1. V **prohlížeč výkonu**klikněte pravým tlačítkem na název relace a pak klikněte na **vlastnosti**.  
  
    Zobrazí se dialogové okno **Stránky vlastností**.  
  
2. V dialogovém okně **stránky vlastností** klikněte na tlačítko **Upřesnit**.  
  
3. Do textového pole **Další možnosti instrumentace** zadejte název funkcí, které chcete instrumentovat, pomocí následující syntaxe:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`  
  
    `FuncSpec` je název oboru názvů a funkce. Má formát `Namespace` **::** `FunctionName` . K oddělení více funkcí použijte středník. Pomocí hvězdičky ( \* ) zadejte zástupný znak pro jeden nebo více znaků. Například **/include: MyNS:: \\ *** určuje všechny funkce v oboru názvů MyNS.  
  
   > [!NOTE]
   > Pokud chcete zobrazit seznam funkcí v binárním souboru, otevřete okno příkazového řádku v instalačním adresáři Nástroje pro profilaci (obvykle adresář nástrojů \Team Tools\Performance v [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] instalačním adresáři) a pak zadejte **VSInstr/DumpFuncs** .  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Omezení instrumentace na konkrétní funkce v binárním souboru  
  
1. V **prohlížeč výkonu**vyhledejte binární název v uzlu **cíle** relace výkonu.  
  
2. Klikněte pravým tlačítkem na název binárního souboru a pak klikněte na **vlastnosti**.  
  
    Zobrazí se dialogové okno **Stránky vlastností**.  
  
3. V dialogovém okně **stránky vlastností** klikněte na tlačítko **Upřesnit**.  
  
4. Do textového pole **Další možnosti instrumentace** zadejte název funkcí, které chcete instrumentovat, pomocí následující syntaxe:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`  
  
    `FuncSpec` je název oboru názvů a funkce. Má formát `Namespace` **::** `FunctionName` . K oddělení více funkcí použijte středník. Pomocí hvězdičky ( \* ) zadejte zástupný znak pro jeden nebo více znaků. Například **/include: MyNS:: \\ *** určuje všechny funkce v oboru názvů MyNS.  
  
   > [!NOTE]
   > Pokud chcete zobrazit seznam funkcí v binárním souboru, otevřete okno příkazového řádku v instalačním adresáři Nástroje pro profilaci (obvykle adresář nástrojů \Team Tools\Performance v [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] instalačním adresáři) a pak zadejte **VSInstr/DumpFuncs** .  
  
## <a name="see-also"></a>Viz také  
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)   
 [Postupy: omezení instrumentace na konkrétní knihovny DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Postupy: určení dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)
