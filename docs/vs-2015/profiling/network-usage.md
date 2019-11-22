---
title: Využití sítě | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eed389a3847145a0f37eb3141526a38e4374d368
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297909"
---
# <a name="network-usage"></a>Využití sítě
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio **sítě** diagnostický nástroj, který shromažďuje data o síťových operacích pomocí provádí [Windows.Web.Http API](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Analýza dat vám může pomoct vyřešit problémy, jako jsou problémy přístupu a ověřování, nesprávné použití mezipaměti a špatné zobrazení a stáhnout výkonu.  
  
 Síťový nástroj podporuje pouze aplikace pro univerzální platformu Windows. Jiné platformy nejsou v tuto chvíli nepodporuje.  
  
> [!NOTE]
> Podrobnější popis síťového nástroje najdete v tématu [představení síťového nástroje sady Visual Studio](https://devblogs.microsoft.com/visualstudio/?m=20155).  
  
## <a name="collecting-network-tool-data"></a>Shromažďování dat nástroje sítě  
 Měli byste spustit **sítě** nástroj s otevřít projekt aplikace Visual Studio na počítači aplikace Visual Studio.  
  
1. Otevřete projekt v sadě Visual Studio.  
  
2. V nabídce klikněte na **ladění/profilování výkonu...** . Zvolte **síť**a pak zvolte **Spustit**.  
  
3. Nástroj sítě zahájí shromažďování přenosů HTTP vaší aplikace.  
  
    Při spouštění vaší aplikace, souhrnné zobrazení v levém podokně automaticky zobrazí seznam zachycených operace HTTP. Vyberte položku na souhrnné zobrazení zobrazíte další informace najdete v podokně podrobností v pravém podokně.  
  
4. Zvolte **Zastavit** zavřít aplikaci.  
  
   Okno sestavy by mělo vypadat přibližně takto:  
  
   ![Okno síť](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analýza dat  
 Když vaše aplikace spuštěna, nebo i po zavření aplikace výběrem některé síťové operace zobrazí v souhrnném zobrazení můžete analyzovat zachycená data protokolu HTTP.  
  
 **Sítě** souhrnné zobrazení zobrazuje data pro každé ze síťových operací v běhu aplikace. Vyberte záhlaví sloupce seřadíte seznam a vyberte typy obsahu pro zobrazení v **Content Type** filtrovat zobrazení.  
  
 Zvolte **uložit jako HAR** vytvořte soubor JSON, které mohou být spotřebovány nástrojů třetích stran, jako je Fiddleru.  
  
 **Sítě** zobrazení podrobností se zobrazí další informace o síťové operace v souhrnném zobrazení.  
  
 ![Panel podrobností nástroje sítě](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Záhlaví**|Informace o hlavičkách žádosti o události.|  
|**Text**|Data datové části požadavku a odpovědi.|  
|**Parametry**|Názvy parametrů řetězce dotazu a hodnoty.|  
|**Soubory cookie**|Data souborů cookie odpovědí a požadavků.|  
|**Časování**|Graf fází v získávání vybrané prostředky.|  
  
 Síť **souhrnu** panel ukazuje počet síťových operací, které jsou zobrazeny v libovolném časovém okamžiku, kolik dat se přenesl, jak dlouho trvalo ke stažení je a kolik chyby (počet požadavků s odpověďmi 4xx nebo 5xx) viditelné.  
  
### <a name="analysis-tips"></a>Tipy pro analýzy  
 Tento nástroj zvýrazňuje některé oblasti, které mohou být užitečné při spuštění analýzy související se sítí:  
  
1. Požadavky, které jsou plně obsluhovat z mezipaměti se zobrazují jako **(z mezipaměti)** v **přijaté** sloupce. To může pomoct určit, jestli používáte mezipaměti efektivně ušetříte šířku pásma uživatele, nebo zda omylem ukládání do mezipaměti odpovědi a poskytuje koncových uživatelů vaší aplikace pomocí zastaralá data.  
  
2. Odpovědi na chyby (4xx nebo 5xx) se zobrazí ve sloupci **výsledky** s červeným stavovým kódem a jsou zvýrazněny také na panelu souhrnu. Díky tomu je snadné sledovat chyby mezi mnoha potenciální požadavky na vaši aplikaci.  
  
3. Tlačítko pro tisk s odezvou na více odpovědí (uvnitř karty tělo) vám může pomáhat s analýzou dat pomocí formátu JSON, XML, HTML, CSS, JavaScriptu a TypeScript, a to zvýšením čitelnosti obsahu.  
  
## <a name="see-also"></a>Viz také  
 [Spustit nástroje pro profilaci bez ladění](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Blog sady Visual Studio: představujeme  kontroly sítě sady Visual Studio](https://go.microsoft.com/fwlink/?LinkId=535022)  
 [Video pro kanál 9: nástroje VS Diagnostic Tools – nový síťový profiler](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
