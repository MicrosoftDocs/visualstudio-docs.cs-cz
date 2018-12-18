---
title: 'Návod: Identifikace problémů s výkonem | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 58
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d26e6ccabcdff12b8f4d9839888e17dc1ab3ce4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745370"
---
# <a name="walkthrough-identifying-performance-problems"></a>Návod: Identifikace problémů s výkonem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak chcete-li Profilovat aplikaci identifikovat problémy s výkonem.  
  
 V tomto návodu bude projít procesem profilaci spravované aplikace a pomocí odběru vzorků a instrumentace izolovat a identifikovat problémy s výkonem v aplikaci.  
  
 V tomto podrobném návodu postupujte podle těchto kroků:  
  
-   Profilovat aplikaci pomocí metody vzorkování.  
  
-   Analýza vzorky výsledků profilace účelem vypátrání a opravení problému s výkonem.  
  
-   Profilovat aplikaci pomocí metody instrumentace.  
  
-   Analýza výsledků instrumentovaná profilace účelem vypátrání a opravení problému s výkonem.  
  
## <a name="prerequisites"></a>Požadavky  
  
- Zprostředkující Principy jazyka C#.  
  
- Kopie [peopletrax – ukázka](../profiling/peopletrax-sample-profiling-tools.md).  
  
  Pro práci s profilace na základě informací poskytnutých, je nejlepší mít ladění k dispozici informace o symbolech.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Profilace pomocí metody vzorkování  
 Vzorkování je metodu profilace, podle kterého procesu dotyčný pravidelně dotazovaní určit aktivní funkce. Výsledná data poskytuje přehled o četnosti dotyčný funkce byla vrcholu zásobníku volání při procesu je Vzorkovaná.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Chcete-li Profilovat aplikaci pomocí metody vzorkování  
  
1.  Otevřít [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] s oprávněními správce. Přihlášení jako správce se vyžaduje pro profilování.  
  
2.  Otevřete řešení PeopleTrax.  
  
     Peopletrax – řešení nyní naplní Průzkumníku řešení.  
  
3.  Nastavte na hodnotu konfigurace projektu **vydání**.  
  
     Ke zjištění problémů s výkonem v aplikaci, měli byste použít sestavení pro vydání. Sestavení pro vydání se doporučuje pro profilaci, protože sestavení pro ladění obsahuje další informace kompilovány do něj může nepříznivě ovlivnit výkon a není ilustrují přesně problémy s výkonem.  
  
4.  Na **analyzovat** nabídky, klikněte na tlačítko **spustit Průvodce výkonem**.  
  
     Zobrazí se Průvodce výkonu.  
  
5.  Ujistěte se, že **vzorkování procesoru (doporučeno)** je vybrána a potom klikněte na tlačítko **Další**.  
  
6.  V **kterou aplikaci chcete Profilovat**vyberte peopletrax – a pak klikněte na tlačítko **Další**.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Vytvoří projekt a spustí do profilu aplikace. **PeopleTrax** se zobrazí okno aplikace.  
  
7.  Klikněte na tlačítko **získá osoby**.  
  
8.  Klikněte na tlačítko **ExportData**.  
  
     Poznámkový blok se otevře a zobrazí nový soubor, který obsahuje data exportovaná z **PeopleTrax**.  
  
9. Zavřete poznámkový blok a pak zavřete **PeopleTrax** aplikace.  
  
     Profiler generuje data profilace (\*.vsp) souboru, obsahuje název souboru v části Reports okno Prohlížeč výkonu a automaticky načte **Souhrn** zobrazení datového souboru v hlavním okně [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-analyze-sampled-profiling-results"></a>K analýze vzorkovány výsledky profilace  
  
1.  Souhrnné zobrazení zobrazuje časová osa využití procesoru v průběhu běhu, profilování **kritickou cestu** seznam, který představuje větev stromu volání aplikace, která byla nejaktivnější a seznam  **Funkce provádějící nejvíce samostatné práce** , která zobrazuje funkce, které byly vzorkovány nejčastěji při provádění kódu v těle vlastní funkce.  
  
     Zkontrolujte **kritickou cestu** seznamu a Všimněte si, že metoda PeopleNS.People.GetNames je nejblíže konci seznamu PeopleTrax funkce. Jeho pozice je vhodným kandidátem pro analýzu. Klikněte na název funkce k zobrazení podrobností o GetNames v **podrobnosti o funkci** zobrazení.  
  
2.  **Podrobnosti o funkci** zobrazení obsahuje dvě okna. Okno rozdělení nákladů poskytuje grafické zobrazení práci prováděnou funkci práce dokončené pomocí funkcí, které ji volaly a příspěvek funkce, které volaly funkce, která se počet instancí, které byly vzorkovány. Můžete změnit funkci, která je zaměření pro zobrazení kliknutím na název funkce. Například můžete kliknout na PeopleNS.People.GetPeople aby GetPeople vybrané funkce.  
  
     **Zobrazení kódu funkce** okně se zobrazí zdrojový kód pro funkci, pokud je k dispozici a jsou zvýrazněné nejdražší řádky ve vybrané funkce. Pokud je vybrána GetNames, uvidíte, že tato funkce přečte řetězce ze zdrojů aplikace a pak používá <xref:System.IO.StringReader> přidáte každý řádek v řetězec, který se <xref:System.Collections.ArrayList>. Neexistuje žádný zřejmý způsob, jak optimalizovat této funkce.  
  
3.  Protože PeopleNS.People.GetPeople je pouze volající GetNames, klikněte na tlačítko GetPeople v okně rozdělení nákladů pro zjištění jeho kód. Tato metoda vrátí <xref:System.Collections.ArrayList> PersonInformationNS.PersonInformation objektů z jmen osob a testovaným GetNames společnosti. GetNames však je volána dvakrát pokaždé, když je vytvořen objekt PersonInformation. Uvidíte, že metoda lze snadno optimalizovat vytváření seznamů jenom jednou na začátku metody a indexování do těchto seznamů během smyčky změnil PersonInformation vytváření.  
  
4.  Alternativní verze GetPeople je součástí ukázkového kódu aplikace a může volat funkci optimalizované tak, že přidáte symbol podmíněné kompilace na sestavení vlastnosti. V okně Průzkumník řešení klikněte pravým tlačítkem na projekt lidí a potom klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **sestavení** v nabídce stránky vlastností a pak zadejte **OPTIMIZED_GETPEOPLE** v textovém poli symbol podmíněné kompilace. Optimalizovaná verze GetPeople nahradí původní metodu v další sestavení.  
  
5.  Znovu spusťte relaci výkonu. Na panelu nástrojů prohlížeče výkonu, klikněte na tlačítko **spustit s nástrojem pro profilaci**. Klikněte na tlačítko **lidem získat** a potom klikněte na tlačítko **exportovat Data**. Zavřete okno Poznámkový blok, který se zobrazí a pak ukončete aplikaci Trax lidí.  
  
     Vygenerování nového datového souboru profilování a **Souhrn** zobrazení, kde se zobrazí nová data v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] hlavního okna.  
  
6.  Chcete-li porovnat dvě spuštění profilování, vyberte dva datové soubory v prohlížeči výkonu, klikněte pravým tlačítkem na soubor a klikněte na **porovnat sestavy výkonu**. Zobrazí okno sestavy porovnání [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] hlavního okna. **Delta** sloupci se zobrazuje změnu v hodnotě výkonu funkce z dříve **směrného plánu** hodnota, která má později **porovnání** hodnotu. Můžete vybrat k porovnání z **sloupec** rozevírací seznam. Vyberte **% celkových vzorků**.  
  
     Všimněte si, že metody GetPeople a GetNames zobrazit zvýšení značné výkonu.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Profilace pomocí metody instrumentace  
 Instrumentace je metodu profilace, ve kterém profiler vloží do speciálně vytvořených verze profilovaných binárních souborů testu funkce. Sond shromažďovat informace o časování na vstupu a výstupu funkcí v instrumentovaném moduly a na všechny lokality volání v dané funkce. Se procesu instrumentace je užitečná k prošetření problémy související se vstupně výstupní operace, jako je zápis na disk a komunikace přes síť. Instrumentace poskytuje podrobnější informace než vzorkování, ale je rušivější ve spouštění procesů a větší množství režie s sebou nese náklady. Instrumentované binární soubory jsou také větší než ladění nebo vydání binární soubory a nejsou určeny pro nasazení.  
  
 V této části Průvodce používáme metody instrumentace ke zjištění další kód, který jsme můžete optimalizovat v PeopleTrax aplikaci, kterou jsme dříve profilována. Pomocí filtru na časové ose přehled, který se zaměříme analýzy na scénář export dat v naší profilované aplikace 00Z seznam lidí, kteří jsou zapsána do soubor poznámkového bloku.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>Chcete-li Profilovat existující aplikace pomocí metody instrumentace  
  
1.  V případě potřeby otevřete aplikaci peopletrax – v sadě Visual Studio.  
  
     Ujistěte se, že jej spouštíte jako správce a že konfigurace sestavení řešení je nastavena na **vydání**.  
  
2.  V prohlížeči výkonu, klikněte na tlačítko **instrumentace**.  
  
3.  Na panelu nástrojů prohlížeče výkonu, klikněte na tlačítko **spustit s nástrojem pro profilaci**.  
  
     Profiler sestaví projekt a začne profilování aplikace. Zobrazí se okno PeopleTrax aplikace.  
  
4.  Klikněte na tlačítko **získá osoby**.  
  
     Datová mřížka PeopleTrax naplní daty.  
  
5.  Počkejte asi 10 sekund a pak klikněte na tlačítko **exportovat Data**.  
  
     **Poznámkový blok** spustí a zobrazí nový soubor, který obsahuje seznam lidí z PeopleTrax. Čekání na umožňuje snadněji identifikovat data exportovat postup pro filtrování.  
  
6.  Zavřete **Poznámkový blok**a pak zavřete **PeopleTrax** aplikace.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] generuje sestavu relace výkonu (*.vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>K analýze instrumentovanou profilaci výsledky  
  
1. Časová osa grafu **Souhrn** zobrazení sestava ukazuje využití procesoru v programu za celou dobu profilování spuštění. Operace exportu dat musí být velké ve špičce nebo při na pravé straně grafu. Můžete filtrovat relace výkonu zobrazit a analyzovat pouze data, která byla shromážděna do operace exportu. Kliknutím vlevo od čárky v grafu, kde začíná operace exportu data. Klikněte znovu na pravé straně operace. Pak klikněte na tlačítko **filtrovat podle výběru** v seznamu odkazů na pravé straně na časové ose.  
  
    **Kritickou cestu** stromové zobrazení, která <xref:System.String.Concat%2A> metodu, která je volána metodou PeopleTrax.Form1.ExportData spotřebovává vysoké procento času. Protože **System.String.Concat** je také v horní části **funkce s nejvíce individuální práce** seznamu omezení času stráveného ve funkci je pravděpodobně bod optimalizace.  
  
2. Dvakrát klikněte na panel **System.String.Concat** v některém z souhrnné tabulky zobrazíte další informace najdete v zobrazení detailů funkce.  
  
3. Uvidíte, PeopleTrax.Form1.ExportData je jedinou metodou, která volá Concat. Klikněte na tlačítko **PeopleTrax.Form1.ExportData** v **volání funkce** seznam a vyberte metodu je jako cílové zobrazení detailů funkce.  
  
4. Zkontrolujte metodu v okně zobrazení kódu funkce. Všimněte si, že neexistují žádné literálu volání **System.String.Concat**. Místo toho existuje několik použití += operandu, které kompilátor nahradí volání **System.String.Concat**. Všechny změny na řetězec v rozhraní .NET Framework způsobit, že nový řetězec mají být přiděleny. Zahrnuje rozhraní .NET Framework <xref:System.Text.StringBuilder> třídu, která je optimalizovaná pro zřetězení řetězců  
  
5. Nahraďte tento problémové oblasti optimalizovaný kód, přidejte do projektu PeopleTrax OPTIMIZED_EXPORTDATA jako symbol podmíněné kompilace.  
  
6. V Průzkumníku řešení klikněte pravým tlačítkem na projekt peopletrax – a pak klikněte na tlačítko **vlastnosti**.  
  
    Zobrazí se formulář vlastnosti PeopleTrax projektu.  
  
7. Klikněte na tlačítko **sestavení** kartu.  
  
8. V **symboly podmíněné kompilace** textového pole, typ **OPTIMIZED_EXPORTDATA**.  
  
9. Zavře formulář. vlastnosti projektu a zvolte **Uložit vše** po zobrazení výzvy.  
  
   Když spustíte aplikaci znovu spustit, zobrazí se označené vylepšení výkonu. Se doporučuje spustit relaci profilování, ani když se uživatel viditelné vylepšení výkonu. Kontrola dat po vyřešení problému je důležité, protože prvním problémem může být skryl nějaký jiný problém.  
  
## <a name="see-also"></a>Viz také  
 [Přehledy](../profiling/overviews-performance-tools.md)   
 [Začínáme se službou](../profiling/getting-started-with-performance-tools.md)   
 [/Z7, /Zi, /ZI (formát informací o ladění)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)



