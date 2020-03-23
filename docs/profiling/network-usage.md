---
title: Analýza využití sítě v aplikacích UPW
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 16c17c6f39980b115b34869fdc6b4912ca94ab0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73144696"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>Analýza využití sítě v aplikacích UPW
Nástroj diagnostika **sítě** sady Visual Studio shromažďuje data o síťových operacích prováděných pomocí [rozhraní Windows.Web.Http API](/uwp/api/windows.web.http). Analýza dat vám může pomoci vyřešit problémy, jako je problémy s přístupem a ověřováním, nesprávné použití mezipaměti a špatný výkon zobrazení a stahování.

 Nástroj Síť podporuje pouze aplikace UPW. Jiné platformy nejsou v současné době podporovány.

> [!NOTE]
> Podrobnější popis síťového nástroje naleznete v [tématu Introducing Visual Studio's network tool](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/).

## <a name="collect-network-tool-data"></a>Shromažďování dat síťového nástroje
 Nástroj **Síť** byste měli spustit s otevřeným projektem sady Visual Studio v počítači sady Visual Studio.

1. Otevřete projekt v sadě Visual Studio.

2. V nabídce klepněte na položku **Ladění / Profilování výkonu**. Zvolte **Síť**a pak zvolte **Spustit**.

3. Síťový nástroj začne shromažďovat provoz HTTP vaší aplikace.

    Při spuštění aplikace se v souhrnném zobrazení v levém podokně automaticky zobrazí seznam zachycených operací HTTP. Výběrem položky v souhrnném zobrazení zobrazíte další informace v panelu podrobností v pravém podokně.

4. Chcete-li aplikaci zavřít, zvolte **Zastavit.**

   Okno sestavy by mělo vypadat nějak takto:

   ![Okno Síť](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Analýza dat
 Zachycený provoz HTTP můžete analyzovat v době, kdy je aplikace spuštěná, nebo dokonce i po zavření aplikace, výběrem některého ze síťových operací zobrazených v souhrnném zobrazení.

 Souhrnné zobrazení **sítě** zobrazuje data pro každou síťovou operaci v průběhu aplikace. Zvolte záhlaví sloupce, chcete-li seznam seřadit, nebo zvolte typy obsahu, které se mají zobrazit v zobrazení filtru **Typ obsahu.**

 Zvolte **Uložit jako HAR,** chcete-li vytvořit soubor JSON, který může být spotřebován nástroji třetích stran, jako je Šumař.

 Zobrazení Podrobnosti **sítě** zobrazuje další informace o operaci sítě v souhrnném zobrazení.

 ![Podokno podrobností síťového nástroje](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|||
|-|-|
|**Hlavičky**|Informace o hlavičkách požadavku události.|
|**Text**|Data datové části požadavku a odpovědi.|
|**Parametry**|Názvy a hodnoty parametrů řetězce dotazu.|
|**Soubory cookie**|Údaje o souborech cookie odpovědí a žádostí.|
|**Časování**|Graf fází získávání vybraných zdrojů.|

 **Souhrnný** panel sítě zobrazuje počet síťových operací, které jsou zobrazeny v daném bodě, kolik dat bylo přeneseno, kolik času trvalo jejich stažení a kolik chyb (požadavky s odpověďmi 4xx nebo 5xx) jsou viditelné.

### <a name="analysis-tips"></a>Tipy pro analýzu
 Tento nástroj zvýrazní určité oblasti, které mohou být užitečné při spuštění analýzy související se sítí:

1. Požadavky, které jsou plně obsluhovány z mezipaměti jsou zobrazeny jako **(z mezipaměti)** ve sloupci **Přijato.** To vám může pomoci určit, zda používáte mezipaměť efektivně k uložení šířky pásma uživatele, nebo zda omylem ukládáte odpovědi do mezipaměti a poskytujete koncovému uživateli aplikace zastaralá data.

2. Odpovědi na chyby (4xx nebo 5xx) jsou zobrazeny ve sloupci **Výsledky** s červeným stavovým kódem a jsou také zvýrazněny v souhrnném pruhu. To usnadňuje rozpoznat chyby mezi mnoha potenciálními požadavky na vaší aplikaci.

3. Tlačítko odezvy docela tisk (uvnitř karty tělo) vám může pomoci analyzovat JSON, XML, HTML, CSS, JavaScript a data odezvy TypeScript zvýšením čitelnosti obsahu.

## <a name="see-also"></a>Viz také

- [Spouštění nástrojů pro profilaci s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Blog visual studia: Představujeme síťového inspektora sady Visual Studio](https://devblogs.microsoft.com/visualstudio/)
- [Channel 9 Video: Diagnostické nástroje VS - nový síťový profiler](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)