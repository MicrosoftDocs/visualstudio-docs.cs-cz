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
ms.openlocfilehash: 58f69d5188a82937c44552e8fd192ea2dba28d3e
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128143"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>Analýza využití sítě v aplikacích pro UWP
Visual Studio **sítě** diagnostický nástroj, který shromažďuje data o síťových operacích pomocí provádí [Windows.Web.Http API](/uwp/api/windows.web.http). Analýza dat vám může pomoct vyřešit problémy, jako jsou problémy přístupu a ověřování, nesprávné použití mezipaměti a špatné zobrazení a stáhnout výkonu.

 Nástroj pro sítě podporuje pouze aplikace UWP. Jiné platformy nejsou v tuto chvíli nepodporuje.

> [!NOTE]
> Úplný popis nástroj sítě, naleznete v tématu [Představujeme nástroje Visual Studio vaší sítě](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/).

## <a name="collect-network-tool-data"></a>Shromažďovat data nástroj sítě.
 Měli byste spustit **sítě** nástroj s otevřít projekt aplikace Visual Studio na počítači aplikace Visual Studio.

1. Otevřete projekt v sadě Visual Studio.

2. V nabídce klikněte na tlačítko **ladění / Profiler výkonu**. Zvolte **sítě**a klikněte na tlačítko **Start**.

3. Nástroj pro sítě začne shromažďování provoz protokolu HTTP vaší aplikace.

    Při spouštění vaší aplikace, souhrnné zobrazení v levém podokně automaticky zobrazí seznam zachycených operace HTTP. Vyberte položku na souhrnné zobrazení zobrazíte další informace najdete v podokně podrobností v pravém podokně.

4. Zvolte **Zastavit** zavřít aplikaci.

   V okně sestavy by měl vypadat přibližně takto:

   ![V okně sítě](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Analýza dat
 Když vaše aplikace spuštěna, nebo i po zavření aplikace výběrem některé síťové operace zobrazí v souhrnném zobrazení můžete analyzovat zachycená data protokolu HTTP.

 **Sítě** souhrnné zobrazení zobrazuje data pro každé ze síťových operací v běhu aplikace. Vyberte záhlaví sloupce seřadíte seznam a vyberte typy obsahu pro zobrazení v **Content Type** filtrovat zobrazení.

 Zvolte **uložit jako HAR** vytvořte soubor JSON, které mohou být spotřebovány nástrojů třetích stran, jako je Fiddleru.

 **Sítě** zobrazení podrobností se zobrazí další informace o síťové operace v souhrnném zobrazení.

 ![Podokno podrobností nástroj Network](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|||
|-|-|
|**Záhlaví**|Informace o hlavičkách žádosti o události.|
|**Text**|Data datové části požadavku a odpovědi.|
|**Parametry**|Názvy parametrů řetězce dotazu a hodnoty.|
|**Soubory cookie**|Data souborů cookie odpovědí a požadavků.|
|**Časování**|Graf fází v získávání vybrané prostředky.|

 Síť **souhrnu** panel ukazuje počet síťových operací, které jsou zobrazeny v libovolném časovém okamžiku, kolik dat se přenesl, jak dlouho trvalo ke stažení je a kolik chyby (počet požadavků s odpověďmi 4xx nebo 5xx) viditelné.

### <a name="analysis-tips"></a>Tipy pro analýzy
 Tento nástroj najdete některé oblasti, které mohou být užitečné při spouštění analýzy související se sítí:

1. Požadavky, které jsou plně obsluhovat z mezipaměti se zobrazují jako **(z mezipaměti)** v **přijaté** sloupce. To může pomoct určit, jestli používáte mezipaměti efektivně ušetříte šířku pásma uživatele, nebo zda omylem ukládání do mezipaměti odpovědi a poskytuje koncových uživatelů vaší aplikace pomocí zastaralá data.

2. Chybové odpovědi (4xx nebo 5xx) se zobrazí v **výsledky** sloupec v červeném stavu kódu a jsou také zvýrazněna v panelu souhrnu. Díky tomu je snadné sledovat chyby mezi mnoha potenciální požadavky na vaši aplikaci.

3. Tlačítko Tisk pretty odpovědi (uvnitř těla kartu) můžete analyzovat prostřednictvím datové části odpovědi JSON, XML, HTML, CSS, JavaScript a TypeScript zvýšením čitelnost obsahu.

## <a name="see-also"></a>Viz také:

- [Spouštění nástrojů pro profilaci s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Blog sady Visual Studio: Představení kontroly sítě sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=535022)
- [Video pro kanál 9: Diagnostické nástroje VS – nové síťové profilery](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)