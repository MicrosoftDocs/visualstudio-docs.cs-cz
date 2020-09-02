---
title: Příručka pro začátečníky k profilaci výkonu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ecfd329e0e5c096e6e0c2011b60cd97dcd1c2937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64838033"
---
# <a name="beginners-guide-to-performance-profiling"></a>Průvodce začátečníka profilováním výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí sady Visual Studio Nástroje pro profilaci můžete analyzovat problémy s výkonem v aplikaci. Tento postup vám ukáže, jak používat data **Vzorkování**.  
  
 **Vzorkování** je metoda statistické profilace, která vám předvede funkce provádějící nejvíce práce uživatelského režimu v aplikaci. Vzorkování je vhodným místem, odkud můžete začít vyhledávat oblasti aplikace, které můžete zrychlit.  
  
 V určených intervalech metoda **Vzorkování** shromažďuje informace o funkcích, které se spouštějí ve vaší aplikaci. Po skončení běhu profilace se v zobrazení **Souhrn** objeví strom volání nejaktivnějších funkcí označovaný jako **Kritická cesta**, kde se prováděla většina práce v aplikaci. Zobrazení také uvádí seznam funkcí, které provedly nejvíce individuální práce, a poskytuje graf s časovou osou, který můžete použít k řešení konkrétních segmentů relace vzorkování.  
  
 Pokud potřebná data nezískáte pomocí **vzorkování**, můžete v nástrojích pro profilaci použít jiné metody shromažďování, které poskytují různé druhy užitečných informací. Další informace o těchto metodách naleznete v tématu [How to: Choose Collection Method](../profiling/how-to-choose-collection-methods.md).  
  
> [!TIP]
> Při profilování kódu, který volá funkce Windows, zkontrolujte, že používáte nejaktuálnější soubory .pdb. Bez těchto souborů se v zobrazeních sestav zobrazí seznam funkcí Windows, jejichž názvy jsou nesrozumitelné a obtížně pochopitelné. Další informace o tom, jak se ujistit, že máte soubory, které potřebujete, najdete v tématu [How to: Reference Windows symbol Information](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="create-and-run-a-performance-session"></a><a name="Step1"></a> Vytvoření a spuštění výkonnostní relace  
 Abyste získali data potřebná k analýze, musíte nejprve vytvořit výkonnostní relaci a potom ji spustit. S oběma úlohami vám pomůže **Průvodce výkonu**.  
  
 Pokud neprofilujete desktopovou aplikaci pro Windows ani aplikaci pro ASP.NET, musíte použít některý z jiných nástrojů pro profilaci. Další informace najdete v článku věnovaném [nástrojům pro profilaci](../profiling/profiling-tools.md).  
  
#### <a name="to-create-and-run-a-performance-session"></a>Vytvoření a spuštění výkonnostní relace  
  
1. Otevřete řešení v sadě Visual Studio. Nastavte konfiguraci na Verze. (Na panelu nástrojů vyhledejte pole **Konfigurace řešení**, které je ve výchozím nastavení nastaveno na **Ladit**. Změňte nastavení na **Verze**.)  
  
    > [!IMPORTANT]
    > Pokud nejste správcem na počítači, který používáte, musíte při použití profileru spustit Visual Studio jako správce. (Pravým tlačítkem myši klikněte na ikonu aplikace Visual Studio a potom klikněte na **Spustit jako správce**.  
  
2. V nabídce **ladění** klikněte na položku **Profiler výkonu**.  
  
3. Zaškrtněte políčko **Průvodce výkonu** a klikněte na **Spustit**.  
  
4. Zaškrtněte políčko **Vzorkování procesoru (doporučeno)** a klikněte na **Dokončit**.  
  
5. Aplikace se spustí a profiler začne shromažďovat data.  
  
6. Spusťte funkci, která by mohla obsahovat problémy s výkonem.  
  
7. Aplikaci zavřete jako obvykle.  
  
     Po spuštění a ukončení aplikace se zobrazení **Souhrn** dat profilace zobrazí v hlavním okně sady Visual Studio a ikona nové relace se zobrazí v okně **Prohlížeč výkonu**.  
  
## <a name="step-2-analyze-sampling-data"></a><a name="Step2"></a> Krok 2: Analýza dat vzorkování  
 Po spuštění a ukončení výkonnostní relace se zobrazení **Souhrn** sestavy profilace objeví v hlavním okně v sadě Visual Studio.  
  
 Doporučujeme začít analýzu dat tím, že pomocí **časové osy v souhrnu** zkontrolujete **kritickou cestu**, potom seznam nejvytíženějších funkcí a nakonec se zaměříte na ostatní funkce. V okně **Seznam chyb** se můžete podívat také na návrhy a upozornění týkající se profilace.  
  
 Nezapomeňte, že metoda vzorkování vám nemusí poskytnout informace, které potřebujete. Vzorky se například shromažďují pouze v případě, že aplikace spouští kód uživatelského režimu. Z tohoto důvodu vzorkování nezachytává některé funkce, jako jsou operace vstupu a výstupu. Nástroje pro profilaci poskytují několik metod shromažďování, které vám umožňují zaměřit se na důležitá data. Další informace o dalších metodách naleznete v tématu [How to: Choose Method Collection](../profiling/how-to-choose-collection-methods.md).  
  
 Každé číslo na následujícím obrázku odpovídá některému kroku v postupu.  
  
 ![Souhrnné zobrazení sestavy pro vzorkování](../profiling/media/summary-sampling.png "Summary_Sampling")  
  
#### <a name="to-analyze-sampling-data"></a>Analýza dat vzorkování  
  
1. V zobrazení **Souhrn** se v části **Kritická cesta** zobrazí větev stromu volání v aplikaci s nejvyšším počtem inkluzivních vzorků. Jedná se o cestu provedení, která byla při shromažďování dat nejaktivnější. Vysoké hodnoty u inkluzivních vzorků označují, že algoritmus generující strom volání je možné optimalizovat. Vyhledejte v kódu funkci, která se v cestě nachází na nejnižším místě. Všimněte si, že cesta může zahrnovat také systémové funkce nebo funkce v externích modulech.  
  
     ![Horká cesta profileru](../profiling/media/profiler-hotpath.png "Profiler_HotPath")  
  
    1. **Inkluzivní vzorky** označují, kolik práce daná funkce vykonala, a všechny funkce, které volala. Vysoký počet inkluzivních vzorků ukazuje na funkce, které jsou celkově nejnáročnější.  
  
    2. **Výhradní vzorky** označují, kolik práce vykonal daný kód v těle funkce, vyjma práce vykonané funkcemi, které volal. Vysoký počet výhradních vzorků může signalizovat kritické místo v samotné funkci.  
  
2. Kliknutím na název funkce otevřete zobrazení **Podrobnosti funkce** dat profilace. Zobrazení **Podrobnosti funkce** znázorňuje grafické zobrazení dat profilace pro vybranou funkci a zobrazuje všechny funkce, které volaly danou funkci, a všechny funkce, které volala vybraná funkce.  
  
    - Velikost bloků volajících a volaných funkcí představuje relativní četnost, s jakou funkce volaly nebo byly volány.  
  
    - Můžete kliknout na název volající nebo volané funkce a nastavit ji jako vybranou funkci v zobrazení Podrobnosti funkce.  
  
    - Dolní podokno v okně **Podrobnosti funkce** zobrazuje samotný kód funkce. Pokud prohlížíte kód a narazíte na možnost optimalizace jeho výkonu, klikněte na název zdrojového souboru a otevřete ho v editoru sady Visual Studio.  
  
3. Pokud chcete v analýze pokračovat, vraťte se do zobrazení **Souhrn** tak, že vyberete možnost **Souhrn** v rozevíracím seznamu zobrazení. Potom si prohlédněte funkce v části **Funkce provádějící nejvíce individuální práce**. V seznamu se zobrazují funkce s nejvyšším počtem výhradních vzorků. Kód v těle těchto funkcí provedl významnou část práce a je možné, že ho budete moci optimalizovat. Chcete-li dále analyzovat konkrétní funkci, klikněte na název funkce, aby se zobrazila v zobrazení **podrobností funkce** .  
  
     ![Seznam funkcí, které fungují nejvíce práce](../profiling/media/functions-mostwork.png "Functions_MostWork")  
  
     Pokud chcete běh profilace zkoumat dále, můžete znovu analyzovat segment dat profilace pomocí časové osy v zobrazení **Souhrn**. V tomto zobrazení si můžete prohlédnout **Kritickou cestu** a **Funkce provádějící nejvíce individuální práce** u vybraného segmentu. Když se například zaměříte na menší špičku na časové ose, můžete odhalit náročné stromy volání a funkce, které se nezobrazily v analýze celkového běhu profilace.  
  
     Pokud chcete segment znovu analyzovat, vyberte segment v poli časové osy souhrnu a potom klikněte na **Filtrovat podle výběru**.  
  
     ![Časová osa zobrazení souhrnu výkonu](../profiling/media/performancesummary.png "PerformanceSummary")  
  
4. Profiler také prostřednictvím sady pravidel navrhuje způsoby vylepšení běhu profilace a identifikuje možné problémy s výkonem. Pokud najde problém, zobrazí upozornění v okně **Seznam chyb**. Pokud chcete zobrazit okno **Seznam chyb**, klikněte v nabídce **Zobrazit** na **Seznam chyb**.  
  
    - Pokud se chcete v zobrazení **Podrobnosti funkce** podívat na funkci, která upozornění vyvolala, poklikejte na upozornění.  
  
    - Podrobné informace o upozornění zobrazíte kliknutím pravého tlačítka myši na chybu a potom kliknutím na **Zobrazit nápovědu chyby**.  
  
## <a name="step-3-revise-code-and-rerun-a-session"></a><a name="Step3"></a> Krok 3: Revize kódu a opakované spuštění relace  
 Po vyhledání a optimalizaci jedné nebo více funkcí můžete běh profilace zopakovat a porovnat data, abyste zjistili, jaký vliv měly změny na výkon aplikace.  
  
#### <a name="to-revise-code-and-rerun-the-profiler"></a>Revize kódu a opakované spuštění profileru  
  
1. Změňte kód.  
  
2. **Prohlížeč výkonu** otevřete tak, že v nabídce **Ladit** kliknete na **Profiler**, dále kliknete na **Prohlížeč výkonu** a nakonec na **Zobrazit Prohlížeč výkonu**.  
  
3. V **Prohlížeči výkonu** klikněte pravým tlačítkem myši na relaci, kterou chcete spustit znovu, a potom klikněte na **Spustit s profilací**.  
  
4. Po dokončení opakovaného běhu relace se v **Prohlížeči výkonu** do složky **Sestavy** přidá další datový soubor pro danou relaci. Vyberte původní i nová data profilace, klikněte pravým tlačítkem myši na výběr a potom klikněte na **Porovnat sestavy výkonu**.  
  
     Otevře se nové okno sestavy s výsledky porovnání. Další informace o použití zobrazení porovnání naleznete v tématu [How to: Compare data Performance Files](../profiling/how-to-compare-performance-data-files.md).  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč výkonu](../profiling/performance-explorer.md)   
 [Začínáme](../profiling/getting-started-with-performance-tools.md)   
 [Přehledy](../profiling/overviews-performance-tools.md)
