---
title: 'Postupy: shromažďování dat o výkonu pro web | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 646d5a59dee68123e478da074901c9d6f98c2763
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783906"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Postupy: shromažďování dat výkonu pro webovou stránku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít **Průvodce výkonem** ke shromažďování dat výkonu pro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci. Můžete profilovat webové aplikace, která je otevřen v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nebo můžete Profilovat [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] web, který je umístěn v místním počítači a ne otevřít v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí.  
  
> [!NOTE]
>  **Průvodce výkonem** umožňuje přidat dat (TIP) interakce vrstev, údaje o výkonu JScript nebo obojí, aby se shromážděná data profilace. Možnost TIP shromažďuje data z procesů na straně serveru. Profilace JScript shromažďuje data ze skriptů, které běží na místním nebo vzdáleném webovém serveru. Ve většině případů měli byste vybrat pouze jednu z možností.  
  
 V závislosti na nastavení oprávnění uživatelského přístupu, které správce má k dispozici jednotlivý uživatel může nebo nemusí mít oprávnění k vytvoření relace profileru v počítači, který je hostitelem procesu ASP.NET. Následující příklady znázorňují možné rozdíly mezi uživateli:  
  
- Někteří uživatelé mohou přístup k rozšířeným funkcím profilace, pokud správce nastavil ovladač a spouštění služby.  
  
- Uživatelé domény mohou přistupovat k pouze profilace vzorku.  
  
- Někteří uživatelé Moje odepřít přístup k profilaci a všem ostatním uživatelům.  
  
  Další informace najdete v tématu [profilace a zabezpečení Windows Vista](../profiling/profiling-and-windows-vista-security.md) a možností správy v [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-profile-a-web-site-project"></a>Chcete-li Profilovat webového projektu  
  
1.  Otevřít [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webový projekt v [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] nebo [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2.  Na **analyzovat** nabídky, klikněte na tlačítko **spustit Průvodce výkonem**.  
  
3.  Na první stránce průvodce vyberte metodu profilace a potom klikněte na tlačítko **Další**. Další informace o metodách profilace naleznete v tématu [metody kolekce výkonu Principy](../profiling/understanding-performance-collection-methods.md). Všimněte si, že metoda profilace vizualizátor souběžnosti není k dispozici pro webové aplikace.  
  
4.  V **kterou aplikaci chcete Profilovat?** rozevíracího seznamu, zkontrolujte, že je vybrána aktuální projekt a potom klikněte na tlačítko **Další**.  
  
5.  Na třetí stránce průvodce můžete k přidání dat interakce vrstev profilování (TIP), data z JavaScript spuštěný ve webové stránky, nebo obojí.  
  
    -   Chcete-li shromažďovat interakce vrstev, vyberte **povolit profilaci interakce vrstev** zaškrtávací políčko.  
  
    -   Chcete-li shromažďovat data z JavaScript spuštěný ve webové stránky, vyberte **Profilovat jazyk JavaScript** zaškrtávací políčko.  
  
6.  Klikněte na tlačítko **Další**.  
  
7.  Na čtvrté stránce průvodce, klikněte na tlačítko **Dokončit**.  
  
8.  Pro vytvoření relace výkonu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] spuštění aplikace a webové stránky v prohlížeči. Vykonává funkce, které chcete profil a potom ukončete prohlížeč.  
  
     Profiler generuje datový soubor a zobrazuje souhrnné zobrazení dat v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hlavního okna.  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Chcete-li profilovat webové stránky bez otevření projektu v sadě Visual Studio  
  
1. Otevřít [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] nebo [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2. Na **analyzovat** nabídky, klikněte na tlačítko **spustit Průvodce výkonem**.  
  
3. Na první stránce průvodce vyberte metodu profilace a potom klikněte na tlačítko **Další**. Další informace najdete v tématu [metody kolekce výkonu Principy](../profiling/understanding-performance-collection-methods.md).  
  
4. Na druhé stránce průvodce, vyberte **Profilovat aplikaci ASP.NET nebo JavaScript** možnost a potom klikněte na tlačítko **Další**.  
  
5. V **jaká adresa URL nebo cesta se spustí webovou aplikaci** na třetí stránce průvodce zadejte adresu URL na domovskou stránku aplikace a potom klikněte na tlačítko **Další**.  
  
   - Pro server (IIS) na základě webové stránky, zadejte adresu URL jako **http://localhost/MySite/default.aspx**. To způsobí, že [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace v místním počítači v kořenovém adresáři aplikace MySite určených k profilaci a stránku default.aspx dané lokality ke spuštění v aplikaci Internet Explorer spustit relaci.  
  
   - Pro soubor založené na webu, zadejte umístění, například soubor / / / / /**c:\WebSites\MySite\default.aspx**. To způsobí, že [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace umístěné v c:\webSites\MySite určených k profilaci a na stránce http://localhost:nnnn/MySite/default.aspx ke spuštění v aplikaci Internet Explorer spustit relaci.  
  
   - Pro externí servery, které chcete sbírat dat jazyka JavaScript, zadejte adresu URL, třeba http://www.contoso.com.  
  
     Další informace o zobrazení stránky vlastností [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] cílový binární soubor.  
  
6. Na třetí stránce průvodce můžete k přidání dat interakce vrstev profilování (TIP), data z JavaScript spuštěný ve webové stránky, nebo obojí.  
  
   -   Chcete-li shromažďovat interakce vrstev, vyberte **povolit profilaci interakce vrstev** zaškrtávací políčko.  
  
   -   Chcete-li shromažďovat data z JavaScript spuštěný ve webové stránky, vyberte **Profilovat jazyk JavaScript** zaškrtávací políčko.  
  
7. Klikněte na tlačítko **Další**.  
  
8. Na čtvrté stránce průvodce, klikněte na tlačítko **Dokončit**.  
  
9. Relace výkonu se vytvoří pro aplikace ASP.NET a webový server je spuštěn v prohlížeči. Vykonává funkce, které chcete profil a potom ukončete prohlížeč.  
  
     Profiler generuje datový soubor a zobrazuje souhrnné zobrazení dat v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hlavního okna.  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Porozumění hodnotám dat instrumentace](../profiling/understanding-instrumentation-data-values.md)   
 [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)



