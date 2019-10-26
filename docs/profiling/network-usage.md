---
title: Analýza využití sítě v aplikacích pro UWP
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d1b81e35cdf08aef82c6e9c070d7127cb2debd5
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911913"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>Analýza využití sítě v aplikacích pro UWP
Nástroj Diagnostika **sítě** sady Visual Studio shromažďuje data o síťových operacích provedených pomocí [rozhraní API Windows. Web. http](/uwp/api/windows.web.http). Analýza dat vám může pomáhat vyřešit problémy, jako jsou problémy s přístupem a ověřováním, nesprávná použití mezipaměti a nízký výkon při zobrazení a stažení.

 Síťový nástroj podporuje jenom aplikace UWP. V tuto chvíli se nepodporují jiné platformy.

> [!NOTE]
> Podrobnější popis síťového nástroje najdete v tématu [představení síťového nástroje sady Visual Studio](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/).

## <a name="collect-network-tool-data"></a>Shromažďovat data nástrojů sítě
 **Síťový** nástroj byste měli spustit s otevřeným projektem sady Visual Studio na počítači se sadou Visual Studio.

1. Otevřete projekt v aplikaci Visual Studio.

2. V nabídce klikněte na **ladit/profilování výkonu**. Zvolte **síť**a pak zvolte **Spustit**.

3. Nástroj sítě zahájí shromažďování přenosů HTTP vaší aplikace.

    Při spuštění aplikace se v zobrazení souhrnu v levém podokně automaticky zobrazí seznam zachycených operací HTTP. Vyberte položku v zobrazení Souhrn a zobrazte další informace na panelu podrobností v pravém podokně.

4. Pokud chcete aplikaci zavřít, klikněte na tlačítko **zastavit** .

   Okno sestavy by mělo vypadat přibližně takto:

   ![Okno síť](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Analyzovat data
 Můžete analyzovat zaznamenaný přenos HTTP, když je aplikace spuštěná, nebo i po zavření aplikace výběrem libovolné síťové operace zobrazené v souhrnném zobrazení.

 Zobrazení Souhrn **sítě** zobrazuje data pro každou síťovou operaci při spuštění vaší aplikace. Vyberte záhlaví sloupce pro seřazení seznamu nebo vyberte typy obsahu, které se mají zobrazit v zobrazení filtru **typu obsahu** .

 Vyberte **Uložit jako Har** a vytvořte soubor JSON, který můžou využívat nástroje třetích stran, jako je Fiddler.

 Zobrazení podrobností **sítě** zobrazí další informace o síťové operaci v souhrnném zobrazení.

 ![Panel podrobností nástroje sítě](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|||
|-|-|
|**Záhlaví**|Informace o hlavičkách požadavku události.|
|**Těles**|Data datové části žádosti a odpovědi.|
|**Parametry**|Názvy a hodnoty parametrů řetězce dotazu.|
|**Soubory cookie**|Odpovědi a data souboru cookie žádosti.|
|**Časování**|Graf fází v rámci získání vybraných prostředků|

 Panel **Souhrn** sítě zobrazuje počet síťových operací, které se zobrazují v jakémkoli okamžiku, kolik dat se přeneslo, kolik času trvalo jejich stažení a kolik chyb (požadavky s 4xx nebo 5xxmi odpověďmi) jsou viditelné.

### <a name="analysis-tips"></a>Tipy k analýze
 Tento nástroj zvýrazňuje některé oblasti, které mohou být užitečné při spuštění analýzy související se sítí:

1. Požadavky, které jsou plně obsluhovány z mezipaměti, jsou zobrazeny ve sloupci **Received** jako **(z mezipaměti)** . To vám může pomoci určit, jestli mezipaměť efektivně používáte k ukládání šířky pásma uživatele, nebo jestli neukládáte odpovědi do mezipaměti omylem a zadáváte koncovému uživateli vaší aplikace se zastaralými daty.

2. Odpovědi na chyby (4xx nebo 5xx) se zobrazí ve sloupci **výsledky** s červeným stavovým kódem a jsou zvýrazněny také na panelu souhrnu. Díky tomu je snadné vymezit chyby v mnoha potenciálních požadavcích aplikace.

3. Tlačítko pro tisk s odezvou na více verzí (na kartě tělo) vám může pomáhat s analýzou dat v datových vytíženích JSON, XML, HTML, CSS, JavaScript a TypeScript tím, že se zvětší čitelnost obsahu.

## <a name="see-also"></a>Viz také:

- [Spouštění nástrojů pro profilaci s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Blog sady Visual Studio: Představení kontroly sítě sady Visual Studio](https://devblogs.microsoft.com/visualstudio/)
- [Video pro kanál 9: nástroje VS Diagnostic Tools – nový síťový profiler](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První pohled na nástroje pro profilaci](../profiling/profiling-feature-tour.md)