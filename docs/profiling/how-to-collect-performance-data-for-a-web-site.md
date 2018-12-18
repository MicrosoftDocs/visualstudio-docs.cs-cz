---
title: 'Postupy: shromažďování dat o výkonu pro web | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2d9cb832d8797eb4ebf16482f4bef02aa6644a3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064294"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Postupy: shromažďování dat o výkonu pro webový server

Můžete použít **Průvodce výkonem** ke shromažďování dat výkonu pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci. Můžete profilovat webové aplikace, která je otevřený v sadě Visual Studio, nebo můžete provádět profilaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web, který je umístěn v místním počítači a není otevřen v integrovaném vývojovém prostředí sady Visual Studio.

> [!NOTE]
> **Průvodce výkonem** umožňuje přidat dat (TIP) interakce vrstev, údaje o výkonu JScript nebo obojí, aby se shromážděná data profilace. Možnost TIP shromažďuje data z procesů na straně serveru. Profilace JScript shromažďuje data ze skriptů, které běží na místním nebo vzdáleném webovém serveru. Ve většině případů měli byste vybrat pouze jednu z možností.

 V závislosti na nastavení oprávnění uživatelského přístupu, které správce má k dispozici jednotlivý uživatel může nebo nemusí mít oprávnění k vytvoření relace profileru v počítači, který je hostitelem procesu ASP.NET. Následující příklady znázorňují možné rozdíly mezi uživateli:

- Někteří uživatelé mohou přístup k rozšířeným funkcím profilace, pokud správce nastavil ovladač a spouštění služby.

- Uživatelé domény může přístup pouze profilace vzorku.

- Někteří uživatelé mohou odepřít přístup k profilaci a všem ostatním uživatelům.

  Další informace najdete v tématu [profilace a Windows Vista zabezpečení](../profiling/profiling-and-windows-vista-security.md) a možností správy v [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Chcete-li Profilovat webového projektu

1. Otevřít [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webový projekt v sadě Visual Studio.

2. Na **analyzovat** nabídce vyberte možnost **Profiler výkonu**vyberte **prohlížeč výkonu**a pak vyberte **Start**.

3. Na první stránce průvodce vyberte metodu profilace a potom klikněte na tlačítko **Další**. Další informace o metodách profilace naleznete v tématu [pochopit metody kolekce výkonu](../profiling/understanding-performance-collection-methods.md). Všimněte si, že metoda profilace vizualizátor souběžnosti není k dispozici pro webové aplikace.

4. V **kterou aplikaci chcete Profilovat?** rozevíracího seznamu, zkontrolujte, že je vybrána aktuální projekt a potom klikněte na tlačítko **Další**.

5. Na třetí stránce průvodce můžete k přidání dat interakce vrstev profilování (TIP), data z JavaScript spuštěný ve webové stránky, nebo obojí.

    - Chcete-li shromažďovat interakce vrstev, vyberte **povolit profilaci interakce vrstev** zaškrtávací políčko.

    - Chcete-li shromažďovat data z JavaScript spuštěný ve webové stránky, vyberte **Profilovat jazyk JavaScript** zaškrtávací políčko.

6. Klikněte na tlačítko **Další**.

7. Na čtvrté stránce průvodce, klikněte na tlačítko **Dokončit**.

8. Pro vytvoření relace výkonu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] spuštění aplikace a webové stránky v prohlížeči. Vykonává funkce, které chcete profil a potom ukončete prohlížeč.

     Profiler generuje datový soubor a zobrazuje souhrnné zobrazení dat v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hlavního okna.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Chcete-li profilovat webové stránky bez otevření projektu v sadě Visual Studio

1. Otevřít Visual Studio.

2. Na **analyzovat** nabídce vyberte možnost **Profiler výkonu**vyberte **prohlížeč výkonu**a pak vyberte **Start**.

3. Na první stránce průvodce vyberte metodu profilace a potom klikněte na tlačítko **Další**. Další informace najdete v tématu [metody kolekce výkonu Principy](../profiling/understanding-performance-collection-methods.md).

4. Na druhé stránce průvodce, vyberte **Profilovat aplikaci ASP.NET nebo JavaScript** možnost a potom klikněte na tlačítko **Další**.

5. V **jaká adresa URL nebo cesta se spustí webovou aplikaci** na třetí stránce průvodce zadejte adresu URL na domovskou stránku aplikace a potom klikněte na tlačítko **Další**.

   - Pro server (IIS) na základě webové stránky, zadejte adresu URL jako **< `http://localhost/MySite/default.aspx` >**. To způsobí, že [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace v místním počítači v kořenovém adresáři aplikace MySite určených k profilaci a stránku default.aspx dané lokality ke spuštění v aplikaci Internet Explorer spustit relaci.

   - Pro soubor založené na webu, zadejte umístění, například soubor / / / / /**c:\WebSites\MySite\default.aspx**. To způsobí, že [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace umístěné v c:\webSites\MySite určených k profilaci a na stránce `http://localhost:nnnn/MySite/default.aspx` ke spuštění v aplikaci Internet Explorer spustit relaci.

   - Pro externí servery, které chcete sbírat dat jazyka JavaScript, zadejte adresu URL, třeba `http://www.contoso.com`.

     Další informace o zobrazení stránky vlastností [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] cílový binární soubor.

6. Na třetí stránce průvodce můžete k přidání dat interakce vrstev profilování (TIP), data z JavaScript spuštěný ve webové stránky, nebo obojí.

    - Chcete-li shromažďovat interakce vrstev, vyberte **povolit profilaci interakce vrstev** zaškrtávací políčko.

    - Chcete-li shromažďovat data z JavaScript spuštěný ve webové stránky, vyberte **Profilovat jazyk JavaScript** zaškrtávací políčko.

7. Klikněte na tlačítko **Další**.

8. Na čtvrté stránce průvodce, klikněte na tlačítko **Dokončit**.

9. Relace výkonu se vytvoří pro aplikace ASP.NET a webový server je spuštěn v prohlížeči. Vykonává funkce, které chcete profil a potom ukončete prohlížeč.

     Profiler generuje datový soubor a zobrazuje souhrnné zobrazení dat v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hlavního okna.

## <a name="see-also"></a>Viz také:

[Přehledy](../profiling/overviews-performance-tools.md)  
[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)  
[Vysvětlení hodnotám dat instrumentace](../profiling/understanding-instrumentation-data-values.md)  
[Vysvětlení hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)
