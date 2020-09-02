---
title: 'Návod: Identifikace problémů s výkonem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 58
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc4135b9b861a460295c67c576405edd5c63211
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695003"
---
# <a name="walkthrough-identifying-performance-problems"></a>Návod: Identifikace problémů s výkonem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak profilovat aplikaci pro identifikaci problémů s výkonem.  
  
 V tomto návodu budete postupovat v procesu profilace spravované aplikace a používání vzorkování a instrumentace k izolaci a identifikaci potíží s výkonem v aplikaci.  
  
 V tomto návodu budete postupovat podle těchto kroků:  
  
- Profilování aplikace pomocí metody vzorkování.  
  
- Analyzovat ukázkové výsledky profilace a vyhledat a opravit problém s výkonem.  
  
- Profilování aplikace pomocí metody instrumentace.  
  
- Analyzovat instrumentované výsledky profilace pro vyhledání a opravu potíží s výkonem.  
  
## <a name="prerequisites"></a>Předpoklady  
  
- Mezilehlé porozumění C#.  
  
- Kopie [ukázky PeopleTrax –](../profiling/peopletrax-sample-profiling-tools.md)  
  
  Chcete-li pracovat s informacemi poskytnutými profilací, je vhodné mít k dispozici informace o symbolech ladění.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Profilace pomocí metody vzorkování  
 Vzorkování je metoda profilace, podle které se pravidelně dotazuje proces, aby se zjistila aktivní funkce. Výsledná data poskytují počet, jak často se jednalo o funkci v zásobníku volání při vzorkování procesu.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Profilování aplikace pomocí metody vzorkování  
  
1. Otevřete [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] s oprávněními správce. K profilaci se vyžaduje spuštění jako správce.  
  
2. Otevřete řešení PeopleTrax –.  
  
     Řešení PeopleTrax – nyní naplňuje Průzkumník řešení.  
  
3. Nastavte nastavení konfigurace projektu na **release**.  
  
     K detekci problémů s výkonem v aplikaci byste měli použít sestavení pro vydání. Pro profilaci se doporučuje sestavit sestavení, protože ladicí sestavení obsahuje další informace, které se do něj kompilují, což by mohlo negativně ovlivnit výkon a neilustrovat problémy s výkonem přesně.  
  
4. V nabídce **analyzovat** klikněte na možnost **Spustit Průvodce výkonem**.  
  
     Zobrazí se Průvodce výkonem.  
  
5. Ujistěte se, že je vybráno **vzorkování procesoru (doporučeno)** , a potom klikněte na tlačítko **Další**.  
  
6. V **aplikaci, ve které chcete profilaci cílit**, vyberte PeopleTrax – a potom klikněte na **Další**.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Vytvoří projekt a začne profilovat aplikaci. Zobrazí se okno aplikace **PeopleTrax –** .  
  
7. Klikněte na **získat lidi**.  
  
8. Klikněte na **ExportData**.  
  
     Poznámkový blok otevře a zobrazí nový soubor, který obsahuje exportovaná data z **PeopleTrax –**.  
  
9. Zavřete Poznámkový blok a pak zavřete aplikaci **PeopleTrax –** .  
  
     Profiler vygeneruje soubor dat profilování ( \* . vsp), vypíše název souboru v části sestavy okna Prohlížeč výkonu a automaticky načte **souhrnné** zobrazení datového souboru v hlavním okně [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .  
  
#### <a name="to-analyze-sampled-profiling-results"></a>Postup analýzy ukázkových výsledků profilace  
  
1. Zobrazení souhrnu zobrazuje časovou osu využití procesoru v průběhu spuštění profilování, seznam **cest k Hotu** , který představuje větev stromu volání aplikace, která byla nejvíce aktivní, a seznam **funkcí provádějících většinu individuálních** funkcí, které zobrazují funkce, které byly nejčastěji vzorkovat při provádění kódu v těle vlastní funkce.  
  
     Prohlédněte si seznam **cest za provozu** a Všimněte si, že metoda PeopleNS. lidé. GetNames je funkce PeopleTrax –, která je nejblíže konci seznamu. Jeho poloha je vhodným kandidátem na analýzu. Kliknutím na název funkce zobrazíte podrobnosti o GetNames v zobrazení **podrobností funkce** .  
  
2. Zobrazení **podrobností funkce** obsahuje dvě okna. Okno distribuce nákladů poskytuje grafické zobrazení práce provedené funkcí, práci prováděnou funkcemi, které volá, a příspěvek funkcí, které volaly funkci, na počet instancí, které byly vzorkovat. Můžete změnit funkci, která je soustředěná na zobrazení, kliknutím na název funkce. Můžete například kliknout na PeopleNS. lidé. getlidé a umožnit tak funkci getlidech pro vybranou funkci.  
  
     Okno **zobrazení kódu funkce** zobrazuje zdrojový kód funkce, je-li k dispozici a zvýrazní nejdražších řádků ve vybrané funkci. Pokud je vybráno GetNames, vidíte, že tato funkce přečte řetězec z prostředků aplikace a poté pomocí <xref:System.IO.StringReader> přidá jednotlivé řádky do řetězce do <xref:System.Collections.ArrayList> . Neexistuje žádný zřejmý způsob, jak tuto funkci optimalizovat.  
  
3. Vzhledem k tomu, že PeopleNS. lidi. getlidé je jediným volajícím GetNames, klikněte na getlidé v okně rozdělení nákladů a prověřte svůj kód. Tato metoda vrací <xref:System.Collections.ArrayList> objekt PersonInformationNS. PersonInformation z názvů lidí a společností vytvořených pomocí GetNames. GetNames je však volána dvakrát pokaždé, když je vytvořen objekt PersonInformation. Můžete vidět, že metodu lze snadno optimalizovat vytvořením seznamů pouze jednou na začátku metody a jejím indexováním do těchto seznamů během PersonInformation smyčky vytváření.  
  
4. V ukázkovém kódu aplikace je k dispozici alternativní verze getlidi a můžete volat optimalizovanou funkci přidáním symbolu podmíněné kompilace do vlastností sestavení. V okně Průzkumník řešení klikněte pravým tlačítkem myši na projekt osoby a potom klikněte na možnost **vlastnosti**. V nabídce Stránka vlastností klikněte na **sestavit** a zadejte **OPTIMIZED_GETPEOPLE** do textového pole symbol podmíněné kompilace. Optimalizovaná verze getlidé nahrazuje původní metodu v dalším sestavení.  
  
5. Spusťte znovu relaci výkonu. Na panelu nástrojů Prohlížeč výkonu klikněte na **Spustit s profilací**. Klikněte na **získat lidi** a pak klikněte na **exportovat data**. Zavřete okno poznámkového bloku, které se zobrazí, a potom zavřete aplikaci lidé Trax.  
  
     Vygeneruje se nový soubor dat profilování a v hlavním okně se zobrazí **souhrnné** zobrazení pro nová data [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .  
  
6. Pro porovnání dvou spuštění profilování vyberte dva datové soubory v Prohlížeč výkonu, klikněte na ně pravým tlačítkem myši a pak klikněte na **Porovnat sestavy výkonu**. V hlavním okně se zobrazí okno Sestava porovnání [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Sloupec **Delta** zobrazuje změnu v hodnotě výkonu funkcí z dřívější hodnoty **směrného plánu** na pozdější hodnotu **porovnání** . Z rozevíracího seznamu **sloupců** můžete vybrat hodnoty, které chcete porovnat. Vyberte **včetně vzorků%**.  
  
     Všimněte si, že metody getlidé a GetName znázorňují výrazné nárůsty výkonu.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Profilace pomocí metody instrumentace  
 Instrumentace je metoda profilace, ve které Profiler vloží funkce testu do speciálně sestavených verzí profilované binární soubory. Sondy shromažďují informace o časování při vstupu a ukončování funkcí v instrumentované modulech a na všech webech volání v těchto funkcích. Proces instrumentace je vhodný pro zkoumání problémů souvisejících s vstupně-výstupními operacemi, jako je zápis na disk a komunikace přes síť. Instrumentace poskytuje podrobnější informace než vzorkování, ale je více rušivých při provádění procesů a přináší větší množství režie. Instrumentované binární soubory jsou také větší než soubory ladění nebo vydání a nejsou určeny pro nasazení.  
  
 V této části návodu použijeme metodu instrumentace ke zjištění více kódu, který můžeme optimalizovat v aplikaci PeopleTrax –, kterou jsme provedli dříve. Pomocí filtru časové osy zobrazení souhrnu se pozaměřujeme na naši analýzu scénářů exportu dat v naší profilované aplikaci, ve které se seznam lidí zapisuje do souboru poznámkového bloku.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>Profilace existující aplikace pomocí metody instrumentace  
  
1. V případě potřeby otevřete aplikaci PeopleTrax – v aplikaci Visual Studio.  
  
     Ujistěte se, že jste spuštěni jako správce a že konfigurace sestavení pro řešení je nastavena na **release**.  
  
2. V Prohlížeč výkonu klikněte na **instrumentace**.  
  
3. Na panelu nástrojů Prohlížeč výkonu klikněte na **Spustit s profilací**.  
  
     Profiler vytvoří projekt a začne profilovat aplikaci. Zobrazí se okno aplikace PeopleTrax –.  
  
4. Klikněte na **získat lidi**.  
  
     Mřížka dat PeopleTrax – se naplní daty.  
  
5. Počkejte asi 10 sekund a pak klikněte na **exportovat data**.  
  
     Spustí **Poznámkový blok** a zobrazí nový soubor, který obsahuje seznam lidí z PeopleTrax –. Čekání vám umožní snadněji identifikovat Postup exportu dat pro filtrování.  
  
6. Zavřete **Poznámkový blok**a pak zavřete aplikaci **PeopleTrax –** .  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] vygeneruje sestavu výkonnostní relace (*. vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>Analýza výsledků instrumentace profilace  
  
1. Graf časové osy se **souhrnným** zobrazením sestavy zobrazuje využití CPU v programu po dobu trvání běhu profilace. Operace exportu dat by měla být velkou špičkou nebo stabilní úrovně na pravé straně grafu. Můžete filtrovat relaci výkonu a zobrazit a analyzovat pouze data shromážděná v operaci exportu. Klikněte nalevo od bodu v grafu, kde začíná operace exportu dat. Znovu klikněte na pravou stranu operace. Pak klikněte na **filtrovat podle výběru** v seznamu odkazů napravo od časové osy.  
  
    Strom **pochodu cesty** ukazuje, že <xref:System.String.Concat%2A> metoda, která je volána metodou PeopleTrax –. Form1. ExportData, spotřebovává vysoké procento času. Vzhledem k tomu, že **System. String. Concat** je také v horní části **funkcí s největším individuálním pracovním** seznamem, zkrácení času stráveného ve funkci je pravděpodobným bodem optimalizace.  
  
2. Dvojitým kliknutím na **System. String. Concat** v některé z souhrnných tabulek zobrazíte další informace v zobrazení podrobností funkce.  
  
3. Můžete vidět, že PeopleTrax –. Form1. ExportData je jediná metoda, která volá Concat. Klikněte na **PeopleTrax –. Form1. ExportData** v seznamu **volajících funkcí** a vyberte metodu jako cíl zobrazení podrobností funkce.  
  
4. Prohlédněte si metodu v okně zobrazení kódu funkce. Všimněte si, že neexistují žádná volání literálů do **System. String. Concat**. Místo toho existuje několik způsobů použití operandu + =, který kompilátor nahrazuje voláním **System. String. Concat**. Jakékoli úpravy řetězce v .NET Framework způsobují přidělení nového řetězce. .NET Framework obsahuje <xref:System.Text.StringBuilder> třídu, která je optimalizována pro zřetězení řetězců.  
  
5. Chcete-li nahradit tuto problémovou oblast optimalizovaným kódem, přidejte OPTIMIZED_EXPORTDATA jako symbol podmíněné kompilace do projektu PeopleTrax –.  
  
6. V Průzkumník řešení klikněte pravým tlačítkem na projekt PeopleTrax – a pak klikněte na **vlastnosti**.  
  
    Zobrazí se formulář vlastností projektu PeopleTrax –.  
  
7. Klikněte na kartu **sestavení** .  
  
8. Do textového pole **symboly podmíněné kompilace** zadejte **OPTIMIZED_EXPORTDATA**.  
  
9. Zavřete formulář vlastnosti projektu a po zobrazení výzvy vyberte možnost **Uložit vše** .  
  
   Po opětovném spuštění aplikace se zobrazí označená vylepšení výkonu. Doporučuje se znovu spustit relaci profilování, i když je ve výkonu vidět uživatel s vylepšením. Kontrola dat po vyřešení problému je důležitá, protože první problém může zakrýt nějaký jiný problém.  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [Začínáme](../profiling/getting-started-with-performance-tools.md)   
 [/Z7,/Zi,/ZI (formát ladicích informací)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)
