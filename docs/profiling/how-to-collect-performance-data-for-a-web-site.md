---
title: 'Postup: Shromažďování údajů o výkonu webu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8b5cacba328c48b682fe9069d8ab4a9ee21635db
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302901"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Postup: Shromažďování údajů o výkonu webového serveru

**Průvodce výkonem** můžete použít ke shromažďování [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dat o výkonu webové aplikace. Můžete profilovat webovou aplikaci, která je otevřena [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] v sadě Visual Studio, nebo můžete profilovat web, který je umístěn v místním počítači a není otevřen v prostředí IDE sady Visual Studio.

> [!NOTE]
> **Průvodce výkonem** umožňuje přidat data interakce vrstvy (TIP), data výkonu jazyka JScript nebo obojí do shromážděných dat profilování. Tip možnost shromažďuje data z procesů na straně serveru. Profilování jazyka JScript shromažďuje data ze skriptů spuštěných na místním nebo vzdáleném webu. Ve většině případů byste měli zvolit pouze jednu z možností.

 V závislosti na nastavení oprávnění přístupu uživatelů, které správce zpřístupnil, může nebo nemusí mít jednotlivý uživatel oprávnění zabezpečení k vytvoření relace profileru v počítači, který je hostitelem procesu ASP.NET. Následující příklady ilustrují možné rozdíly mezi uživateli:

- Někteří uživatelé mohou získat přístup k pokročilým funkcím profilování, pokud správce nastavil spuštění ovladače a služby.

- Uživatelé domény mohou přistupovat pouze k profilování vzorků.

- Někteří uživatelé mohou odepřít přístup k profilování všem ostatním uživatelům.

  Další informace naleznete [v tématu Profilování a zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md) a možnosti ADMIN v [aplikaci VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Profilování projektu webu

1. Otevřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webový projekt v sadě Visual Studio.

2. V nabídce **Analyzovat** vyberte **Profilování výkonu**, vyberte **Průzkumník výkonu**a pak vyberte **Start**.

3. Na první stránce průvodce vyberte metodu profilování a klepněte na tlačítko **Další**. Další informace o metodách profilování naleznete v [tématu Understand performance collection methods](../profiling/understanding-performance-collection-methods.md). Všimněte si, že metoda profilování vizualizéru souběžnosti není k dispozici pro webové aplikace.

4. V **rozevíracím seznamu Která aplikace chcete cílit na profilování,** zkontrolujte, zda je vybrán aktuální projekt, a klepněte na tlačítko **Další**.

5. Na třetí stránce průvodce můžete přidat data profilování interakce úrovně (TIP), data z JavaScriptu spuštěného na webových stránkách nebo obojí.

    - Chcete-li shromáždit interakci s vrstvou, zaškrtněte políčko **Povolit profilování interakce na úrovni.**

    - Chcete-li shromažďovat data z JavaScriptu spuštěného na webových stránkách, zaškrtněte políčko **Profil JavaScriptu.**

6. Klikněte na **Další**.

7. Na čtvrté stránce průvodce klepněte na tlačítko **Dokončit**.

8. Pro aplikaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] je vytvořena relace výkonu a web je spuštěn v prohlížeči. Využijte funkce, které chcete profilovat, a zavřete prohlížeč.

     Profiler generuje datový soubor a zobrazí souhrnné zobrazení dat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v hlavním okně.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Profilování webu bez otevření projektu v sadě Visual Studio

1. Otevřete sadu Visual Studio.

2. V nabídce **Analyzovat** vyberte **Profilování výkonu**, vyberte **Průzkumník výkonu**a pak vyberte **Start**.

3. Na první stránce průvodce vyberte metodu profilování a klepněte na tlačítko **Další**. Další informace naleznete [v tématu Principy metod shromažďování výkonu](../profiling/understanding-performance-collection-methods.md).

4. Na druhé stránce průvodce vyberte možnost **Profil ASP.NET nebo JavaScript a** klepněte na tlačítko **Další**.

5. V poli **Co adresa URL nebo cesta spustí webová aplikace** na třetí stránce průvodce, zadejte adresu URL domovské stránky aplikace a klepněte na tlačítko **Další**.

   - Pro web založený na serveru (IIS) zadejte adresu URL, například ** < `http://localhost/MySite/default.aspx` **. To způsobí, že [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace v místním počítači v kořenovém adresáři aplikace MySite být profilován a výchozí stránku.aspx na tomto webu, které mají být spuštěny v aplikaci Internet Explorer ke spuštění relace.

   - Pro web založený na souborech zadejte cestu, například**soubor///c:\WebSites\MySite\default.aspx**. To způsobí, že [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace umístěná na adrese c:\webSites\MySite bude profilována a stránka, `http://localhost:nnnn/MySite/default.aspx` která má být spuštěna v aplikaci Internet Explorer, zahájí relaci.

   - U externích webů, na kterých chcete shromažďovat data `http://www.contoso.com`jazyka JavaScript, zadejte například adresu URL .

     Další informace naleznete na stránkách [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] vlastností cílového binárního souboru.

6. Na třetí stránce průvodce můžete přidat data profilování interakce úrovně (TIP), data z JavaScriptu spuštěného na webových stránkách nebo obojí.

    - Chcete-li shromáždit interakci s vrstvou, zaškrtněte políčko **Povolit profilování interakce na úrovni.**

    - Chcete-li shromažďovat data z JavaScriptu spuštěného na webových stránkách, zaškrtněte políčko **Profil JavaScriptu.**

7. Klikněte na **Další**.

8. Na čtvrté stránce průvodce klepněte na tlačítko **Dokončit**.

9. Pro ASP.NET aplikace je vytvořena relace výkonu a web je spuštěn v prohlížeči. Využijte funkce, které chcete profilovat, a zavřete prohlížeč.

     Profiler generuje datový soubor a zobrazí souhrnné zobrazení dat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v hlavním okně.

## <a name="see-also"></a>Viz také

[Přehledy](../profiling/overviews-performance-tools.md)
[Konfigurace výkonových relací](../profiling/configuring-performance-sessions.md)
Pochopit hodnoty
[dat instrumentace](../profiling/understanding-instrumentation-data-values.md)[Pochopit hodnoty vzorkovacích dat](../profiling/understanding-sampling-data-values.md)
