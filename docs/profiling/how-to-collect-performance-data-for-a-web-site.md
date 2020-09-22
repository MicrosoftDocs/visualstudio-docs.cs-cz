---
title: Shromažďování údajů o výkonu pro web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7ea4e3309fc003a4fc4fc73377e8b2bbe12cd567
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851473"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Postupy: shromažďování údajů o výkonu webu

K shromažďování údajů o výkonu webové aplikace můžete použít **Průvodce výkonem** [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . Můžete profilovat webovou aplikaci, která je otevřena v aplikaci Visual Studio, nebo můžete profilovat web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , který je umístěn v místním počítači a není otevřen v integrovaném vývojovém prostředí sady Visual Studio.

> [!NOTE]
> **Průvodce výkonem** umožňuje přidat data interakce vrstev (Tip), data o výkonu JScript nebo obojí do shromážděných dat profilace. Možnost TIP shromažďuje data z procesů na straně serveru. Profilace jazyka JScript shromažďuje data ze skriptů, které jsou spuštěny na místním nebo vzdáleném webu. Ve většině případů byste měli zvolit jenom jednu z možností.

 V závislosti na nastavení uživatelských oprávnění přístupu, které správce zpřístupnil, může mít jednotliví uživatelé oprávnění zabezpečení k vytvoření relace profileru v počítači, který je hostitelem procesu ASP.NET. Následující příklady ilustrují možné rozdíly mezi uživateli:

- Někteří uživatelé můžou získat přístup k funkcím pokročilého profilování, když správce nastavil ovladač a službu tak, aby se spouštěly.

- Uživatelé domény mohou přistupovat pouze k ukázkovému profilaci.

- Někteří uživatelé můžou odepřít přístup k profilaci všem ostatním uživatelům.

  Další informace najdete v tématech [profilace a zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md) a možnosti správy v [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Profilování projektu webu

1. Otevřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webový projekt v aplikaci Visual Studio.

2. V nabídce **analyzovat** vyberte **Profiler výkonnosti**, vyberte **prohlížeč výkonu**a pak vyberte **Spustit**.

3. Na první stránce průvodce vyberte metodu profilace a potom klikněte na tlačítko **Další**. Další informace o metodách profilování naleznete v tématu [vysvětlení metod shromažďování výkonu](../profiling/understanding-performance-collection-methods.md). Všimněte si, že metoda profilování Vizualizátor souběžnosti není k dispozici pro webové aplikace.

4. V části **jakou aplikaci chcete profilovat?** vyberte rozevírací seznam, ujistěte se, že je vybrána možnost aktuální projekt, a poté klikněte na tlačítko **Další**.

5. Na třetí stránce průvodce se můžete rozhodnout přidat data profilování interakce vrstev (TIP), data z JavaScriptu běžícího na webových stránkách nebo obojí.

    - Pokud chcete shromažďovat interakce vrstev, zaškrtněte políčko **Povolit Profilování interakce vrstev** .

    - Chcete-li shromažďovat data z JavaScriptu běžícího na webových stránkách, zaškrtněte políčko **profil JavaScript** .

6. Klikněte na **Next** (Další).

7. Na čtvrté stránce průvodce klikněte na tlačítko **Dokončit**.

8. Pro aplikaci je vytvořena relace výkonu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a web je spuštěn v prohlížeči. Vyzkoušejte funkci, kterou chcete profilovat, a pak zavřete prohlížeč.

     Profiler vygeneruje datový soubor a zobrazí souhrnný přehled dat v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hlavním okně.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Profilování webu bez otevření projektu v aplikaci Visual Studio

1. Otevřete sadu Visual Studio.

2. V nabídce **analyzovat** vyberte **Profiler výkonnosti**, vyberte **prohlížeč výkonu**a pak vyberte **Spustit**.

3. Na první stránce průvodce vyberte metodu profilace a potom klikněte na tlačítko **Další**. Další informace najdete v tématu [principy metod shromažďování výkonu](../profiling/understanding-performance-collection-methods.md).

4. Na druhé stránce průvodce vyberte možnost **profilovat aplikaci ASP.NET nebo JavaScript** a pak klikněte na tlačítko **Další**.

5. V poli **Jaká adresa URL nebo cesta spustí vaši webovou aplikaci** na třetí stránce průvodce zadejte adresu URL domovské stránky aplikace a klikněte na tlačítko **Další**.

   - Pro web založený na serveru (IIS) zadejte adresu URL, jako je například **<`http://localhost/MySite/default.aspx`>** . Tím dojde k tomu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , že aplikace v místním počítači v kořenovém adresáři aplikace v aplikaci bude profilovat a na této stránce bude spuštěna stránka default. aspx v aplikaci Internet Explorer, aby bylo možné spustit relaci.

   - Pro web založený na souboru zadejte cestu, například File///**c:\WebSites\MySite\default.aspx**. To způsobí, že se [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace nacházející v c:\webSites\MySite bude profilovat a stránka, která se má spustit `http://localhost:nnnn/MySite/default.aspx` v Internet Exploreru, aby spustila relaci.

   - Pro externí weby, na kterých chcete shromažďovat data JavaScriptu, zadejte adresu URL, například `http://www.contoso.com` .

     Další informace zobrazíte na stránkách vlastností pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] cílový binární soubor.

6. Na třetí stránce průvodce se můžete rozhodnout přidat data profilování interakce vrstev (TIP), data z JavaScriptu běžícího na webových stránkách nebo obojí.

    - Pokud chcete shromažďovat interakce vrstev, zaškrtněte políčko **Povolit Profilování interakce vrstev** .

    - Chcete-li shromažďovat data z JavaScriptu běžícího na webových stránkách, zaškrtněte políčko **profil JavaScript** .

7. Klikněte na **Next** (Další).

8. Na čtvrté stránce průvodce klikněte na tlačítko **Dokončit**.

9. Pro aplikaci ASP.NET je vytvořena relace výkonu a web je spuštěn v prohlížeči. Vyzkoušejte funkci, kterou chcete profilovat, a pak zavřete prohlížeč.

     Profiler vygeneruje datový soubor a zobrazí souhrnný přehled dat v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hlavním okně.

## <a name="see-also"></a>Viz také

[Přehledy](../profiling/overviews-performance-tools.md) 
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md) 
 [Porozumění hodnotám](../profiling/understanding-instrumentation-data-values.md) 
 dat instrumentace [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)
