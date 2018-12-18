---
title: Využívání sítě | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3dd68bec55b53d1b4618e8ae1679603577daf295
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726852"
---
# <a name="network-usage"></a>Využití sítě
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio **sítě** diagnostický nástroj, který shromažďuje data o síťových operacích pomocí provádí [Windows.Web.Http API](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Analýza dat vám může pomoct vyřešit problémy, jako jsou problémy přístupu a ověřování, nesprávné použití mezipaměti a špatné zobrazení a stáhnout výkonu.  
  
 Nástroj pro sítě podporuje pouze aplikace univerzální platformy Windows. Jiné platformy nejsou v tuto chvíli nepodporuje.  
  
> [!NOTE]
>  Úplný popis nástroj sítě, naleznete v tématu [Představujeme nástroje Visual Studio vaší sítě](http://blogs.msdn.com/b/visualstudio/archive/2015/05/04/introducing-visual-studio-s-network-tool.aspx).  
  
## <a name="collecting-network-tool-data"></a>Shromažďování dat v síti nástroj  
 Měli byste spustit **sítě** nástroj s otevřít projekt aplikace Visual Studio na počítači aplikace Visual Studio.  
  
1. Otevřete projekt v sadě Visual Studio.  
  
2. V nabídce klikněte na tlačítko **ladění / Profiler výkonu...** . Zvolte **sítě**a klikněte na tlačítko **Start**.  
  
3. Nástroj pro sítě začne shromažďování provoz protokolu HTTP vaší aplikace.  
  
    Při spouštění vaší aplikace, souhrnné zobrazení v levém podokně automaticky zobrazí seznam zachycených operace HTTP. Vyberte položku na souhrnné zobrazení zobrazíte další informace najdete v podokně podrobností v pravém podokně.  
  
4. Zvolte **Zastavit** zavřít aplikaci.  
  
   V okně sestavy by měl vypadat přibližně takto:  
  
   ![V okně sítě](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analýza dat  
 Když vaše aplikace spuštěna, nebo i po zavření aplikace výběrem některé síťové operace zobrazí v souhrnném zobrazení můžete analyzovat zachycená data protokolu HTTP.  
  
 **Sítě** souhrnné zobrazení zobrazuje data pro každé ze síťových operací v běhu aplikace. Vyberte záhlaví sloupce seřadíte seznam a vyberte typy obsahu pro zobrazení v **Content Type** filtrovat zobrazení.  
  
 Zvolte **uložit jako HAR** vytvořte soubor JSON, které mohou být spotřebovány nástrojů třetích stran, jako je Fiddleru.  
  
 **Sítě** zobrazení podrobností se zobrazí další informace o síťové operace v souhrnném zobrazení.  
  
 ![Podokno podrobností nástroj Network](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Záhlaví**|Informace o hlavičkách žádosti o události.|  
|**Text**|Data datové části požadavku a odpovědi.|  
|**Parametry**|Názvy parametrů řetězce dotazu a hodnoty.|  
|**Soubory cookie**|Data souborů cookie odpovědí a požadavků.|  
|**Časování**|Graf fází v získávání vybrané prostředky.|  
  
 Síť **souhrnu** panel ukazuje počet síťových operací, které jsou zobrazeny v libovolném časovém okamžiku, kolik dat se přenesl, jak dlouho trvalo ke stažení je a kolik chyby (počet požadavků s odpověďmi 4xx nebo 5xx) viditelné.  
  
### <a name="analysis-tips"></a>Tipy pro analýzy  
 Tento nástroj světla, které určité oblasti, které mohou být užitečné při používání sítě související analýzy:  
  
1.  Požadavky, které jsou plně obsluhovat z mezipaměti se zobrazují jako **(z mezipaměti)** v **přijaté** sloupce. To může pomoct určit, jestli používáte mezipaměti efektivně ušetříte šířku pásma uživatele, nebo zda omylem ukládání do mezipaměti odpovědi a poskytuje koncových uživatelů vaší aplikace pomocí zastaralá data.  
  
2.  Chybové odpovědi (4xx nebo 5xx) se zobrazí v v **výsledky** sloupec v červeném stavu kódu a jsou také zvýrazněna v panelu souhrnu. Díky tomu je snadné sledovat chyby mezi mnoha potenciální požadavky na vaši aplikaci.  
  
3.  Tlačítko Tisk pretty odpovědi (uvnitř těla kartu) můžete analyzovat prostřednictvím datové části odpovědi JSON, XML, HTML, CSS, JavaScript a TypeScript zvýšením čitelnost obsahu.  
  
## <a name="see-also"></a>Viz také  
 [Spustit profilování nástroje bez ladění](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Visual Studio blog: Představení sady Visual Studio sítě inspektoru](http://go.microsoft.com/fwlink/?LinkId=535022)   
 [Video pro kanál 9: VS diagnostické nástroje – Profiler nové sítě](http://channel9.msdn.com/Series/ConnectOn-Demand/206)



