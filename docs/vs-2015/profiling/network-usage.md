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
ms.openlocfilehash: 20f7003bbcd319a6a8487d496697d3dcd0b7a18a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548418"
---
# <a name="network-usage"></a>Využití sítě
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj Diagnostika **sítě** sady Visual Studio shromažďuje data o síťových operacích provedených pomocí [rozhraní API Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Analýza dat vám může pomáhat vyřešit problémy, jako jsou problémy s přístupem a ověřováním, nesprávná použití mezipaměti a nízký výkon při zobrazení a stažení.  
  
 Síťový nástroj podporuje pouze aplikace pro univerzální platformu Windows. V tuto chvíli se nepodporují jiné platformy.  
  
> [!NOTE]
> Podrobnější popis síťového nástroje najdete v tématu [představení síťového nástroje sady Visual Studio](https://devblogs.microsoft.com/visualstudio/?m=20155).  
  
## <a name="collecting-network-tool-data"></a>Shromažďování dat nástroje sítě  
 **Síťový** nástroj byste měli spustit s otevřeným projektem sady Visual Studio na počítači se sadou Visual Studio.  
  
1. Otevřete projekt v sadě Visual Studio.  
  
2. V nabídce klikněte na **ladění/profilování výkonu...**. Zvolte **síť**a pak zvolte **Spustit**.  
  
3. Nástroj sítě zahájí shromažďování přenosů HTTP vaší aplikace.  
  
    Při spuštění aplikace se v zobrazení souhrnu v levém podokně automaticky zobrazí seznam zachycených operací HTTP. Vyberte položku v zobrazení Souhrn a zobrazte další informace na panelu podrobností v pravém podokně.  
  
4. Pokud chcete aplikaci zavřít, klikněte na tlačítko **zastavit** .  
  
   Okno sestavy by mělo vypadat přibližně takto:  
  
   ![Okno síť](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analýza dat  
 Můžete analyzovat zaznamenaný přenos HTTP, když je aplikace spuštěná, nebo i po zavření aplikace výběrem libovolné síťové operace zobrazené v souhrnném zobrazení.  
  
 Zobrazení Souhrn **sítě** zobrazuje data pro každou síťovou operaci při spuštění vaší aplikace. Vyberte záhlaví sloupce pro seřazení seznamu nebo vyberte typy obsahu, které se mají zobrazit v zobrazení filtru **typu obsahu** .  
  
 Vyberte **Uložit jako Har** a vytvořte soubor JSON, který můžou využívat nástroje třetích stran, jako je Fiddler.  
  
 Zobrazení podrobností **sítě** zobrazí další informace o síťové operaci v souhrnném zobrazení.  
  
 ![Panel podrobností nástroje sítě](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|Name|Popis|  
|-|-|  
|**Hlavičky**|Informace o hlavičkách požadavku události.|  
|**Text**|Data datové části žádosti a odpovědi.|  
|**Parametry**|Názvy a hodnoty parametrů řetězce dotazu.|  
|**Soubory cookie**|Odpovědi a data souboru cookie žádosti.|  
|**Časování**|Graf fází v rámci získání vybraných prostředků|  
  
 Panel **Souhrn** sítě zobrazuje počet síťových operací, které se zobrazují v jakémkoli okamžiku, kolik dat se přeneslo, kolik času trvalo jejich stažení a kolik chyb (požadavky s 4xx nebo 5xxmi odpověďmi) jsou viditelné.  
  
### <a name="analysis-tips"></a>Tipy k analýze  
 Tento nástroj zvýrazňuje některé oblasti, které mohou být užitečné při spuštění analýzy související se sítí:  
  
1. Požadavky, které jsou plně obsluhovány z mezipaměti, jsou zobrazeny ve sloupci **Received** jako **(z mezipaměti)** . To vám může pomoci určit, jestli mezipaměť efektivně používáte k ukládání šířky pásma uživatele, nebo jestli neukládáte odpovědi do mezipaměti omylem a zadáváte koncovému uživateli vaší aplikace se zastaralými daty.  
  
2. Odpovědi na chyby (4xx nebo 5xx) se zobrazí ve sloupci **výsledky** s červeným stavovým kódem a jsou zvýrazněny také na panelu souhrnu. Díky tomu je snadné vymezit chyby v mnoha potenciálních požadavcích aplikace.  
  
3. Tlačítko pro tisk s odezvou na více odpovědí (uvnitř karty tělo) vám může pomáhat s analýzou dat pomocí formátu JSON, XML, HTML, CSS, JavaScriptu a TypeScript, a to zvýšením čitelnosti obsahu.  
  
## <a name="see-also"></a>Viz také  
 [Spustit nástroje pro profilaci bez ladění](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Blog sady Visual Studio: Představení kontroly sítě sady Visual Studio](https://blogs.msdn.com/b/visualstudio/)   
 [Video pro kanál 9: nástroje VS Diagnostic Tools – nový síťový profiler](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
