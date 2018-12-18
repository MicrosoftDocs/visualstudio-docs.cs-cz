---
title: Visual Studio Shell (integrovaný režim) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3eb0c8dd0588e1af9b3aad500c8bc9f899b44513
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765284"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integrovaný režim)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prostředí sady Visual Studio integrované zahrnuje integrované vývojové prostředí (IDE), ladicí program a integrace správy zdrojového kódu. Žádný programovací jazyk je v ceně. Integrované prostředí však poskytuje rozhraní, které vám umožní přidávat programovacích jazyků.  
  
 Prostředí sady Visual Studio integrované je ve skutečnosti kombinace prostředí sady Visual Studio, samostatný plus další instalace, patří mezi ně konkrétní komponenty prostředí integrated shell.  Aplikace integrované prostředí by měl obsahovat obě izolovaného prostředí Distribuovatelný balíček z [Distribuovatelný balíček prostředí Microsoft Visual Studio Shell (izolovaný režim)](http://go.microsoft.com/fwlink/?LinkId=616022) a také Distribuovatelný balíček prostředí integrated shell z [Microsoft Visual Studio Shell (integrovaný režim) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Před přístupem k Distribuovatelné balíčky izolovaného a integrovaného prostředí, budete požádáni o vyplnění stručného zákaznického dotazníku.  Po vyplnění, budete přesměrováni na stránku Visual Studio Connect s odkazy na stažení balíčku k opětovné distribuci.  Odkazy ke stažení najdete na následné návštěvy webu Visual Studio Connect pod **programy &#124; VISUAL STUDIO 2015 integrované a IZOLOVANÉHO prostředí** kartu.  
  
 Pokud nainstalujete na stejném počítači jako s plnou verzí sady Visual Studio vaší aplikace integrované prostředí, součásti vaší aplikace bude integrovat přímo do sady Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Funkce v prostředí Integrated Shell  
  
|||  
|-|-|  
|Oblast funkcí|Funkce|  
|Podpora jazyků|-Žádný|  
|IDE – integrované vývojové prostředí|<ul><li>Nastavení<br /><br /> <ul><li>Vytvoření nastavení</li><li>Nastavení importu a exportu</li><li>Resetovat nastavení</li></ul></li><li>**Panel nástrojů** integrace</li><li>**Seznam úkolů** integrace</li><li>Integrace nápovědy</li><li>**Možnosti** dialogové okno</li><li>Správa písma a barvy</li><li>**Výstup** okna</li><li>**Příkaz** okna</li><li>Správa oken</li><li>Příkazy, nabídky a klávesové zkratky</li><li>Modul runtime jazyka specifického pro doménu (DSL)</li></ul>|  
|Systém projektu a typů projektu|-Řešení a složky řešení<br />– Řešení configuration Manageru<br />– Správa položky<br />-Jednoprojektové a víceprojektové řešení<br />– Aplikace Návrhář (vlastnosti zjednodušené projektu)<br />-Přidat webový odkaz<br />– Přidat odkaz na službu<br />Jednoho projektu<br />– Typy projektů webové stránky<br />-Projekty webových aplikací|  
|Sestavení|– Vlastní kroky sestavení v integrovaném vývojovém prostředí<br />-Předkompilace pro ochranu duševního vlastnictví (IP)<br />-Podepisování kódu<br />     MSBuild|  
|Editor|-Procházení kódu nástroje (jednotné hledání, definici zdroje, dědičnost)<br />-Navigace v kódu<br />-IntelliSense<br />– Inteligentní značky<br />-Refaktoring<br />-Přehlednou výpis<br />-Filtrování IntelliSense<br />-   **Code Definition** okna|  
|Návrhář|– Windows Presentation Foundation návrháře<br />– Windows Forms Designer<br />-Webové návrháře a editoru HTML|  
|Data|-   **Průzkumník serveru** (zjednodušené: jenom data). Viz poznámka 1.<br />-   **Zdroje dat** okna<br />-Úplnou sadu ovládací prvky dat<br />-XML Editor<br />-Datové připojení k místní zdroj dat (. MDF nebo. MDB)<br />-Datové připojení k objektu<br />-Datové připojení k webové službě<br />-Datové připojení k místní databázi serveru<br />-Data svázat vzdálený databázový server<br />-DDL nástroje pro vzdálených dat<br />-   **Průzkumník serveru** rozšíření ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] ukázky)|  
|Ladicí program|– Místní ladění. Viz poznámka 2.<br />-Spravovaného ladění<br />– Místní ladění<br />-Připojit k místní procesu<br />-Připojit ke vzdálenému procesu<br />-Anonymního delegáta<br />-Aplikační domény<br />– ASPX ladění<br />– Atributy<br />-Přerušení během vyhodnocení funkce<br />-Zarážky<br />– Zarážky omezení<br />-Zásobník volání<br />-   **Příkaz** okna<br />– Ladění mezi vlákny<br />-Datových tipech<br />-Data visualizer<br />-Ladicí program podpora asistentů spravovaného ladění (mda)<br />– Ladicí program podpora pro předávání typů<br />– Podpora dteevents spouští OTB<br />-JMC krokovač<br />-Ladicí program AppID testu (DBGCLR)<br />– Profil ladicí program<br />-Ladicího programu nástroje a možnosti<br />– Iterator ladění<br />-Vyhodnocení výrazu design-time<br />– Vyhodnocovací filtr výrazů C#<br />– Převod do strojového jazyka<br />-Upravit a pokračovat<br />– Chyba při vyhodnocování windows výraz (kukátko, místní hodnoty, automatické hodnoty)<br />– Pomocné rutiny výjimka<br />– Výjimky<br />– Spouštění<br />– Obecné typy<br />– Získání správné zdroje<br />-Cluster prostředí HPC a ladění<br />– Integrované ladění Vícejazyčná verze<br />-InterOp ladění<br />-Ladění just-in-time<br />– Místní ladění<br />-Spravovaného ladění<br />-Ruční kontrola (procesy – okno)<br />– Paměť<br />– S minimálním výpisem podpora<br />– Moduly<br />-Ladění více procesů<br />– Nativní ladění<br />– Podpora modulu nové ladění<br />-Ladění optimalizovaného kódu<br />-Filtrování windows output<br />-Zpracování hostování pro spravované ladění<br />-Procesy<br />– Rychlé kukátko<br />-Registry<br />-Registry v zásobníku<br />-Vzdáleného ladění<br />– Návratové hodnoty<br />-Ladění script<br />-Podpora služby source<br />-Zabezpečení<br />Side-by-side<br />-SQL<br />– Server symbol<br />-Body trasování<br />-Vlákna<br />-Vizualizace<br />-Ladicí program extensible šablony stylů transformace XSLT (Language)|  
|64bitová podpora|-64-bit ladění pro spravovaný i nativní kód, všechny jazyky<br />-x64 nativní podporu|  
|Správa zdrojového kódu (SCC)|– Integrace SCC úrovně basic. Viz poznámka 3.<br />-Nástroje a možnosti ověřování|  
|Rozšiřitelnost|-Zpracování součástí rozšíření VSPackages a rozhraní MEF|  
  
## <a name="notes"></a>Poznámky  
  
#### <a name="1-data-tools"></a>1. Datové nástroje  
 Zahrnuje nástroje pro vývoj databází jako je například podpora rozšiřitelnosti dat a zjednodušeného prostředí integrated shell **Průzkumníka řešení**. Ale SQL Server Express, SQL Reporting a Crystal Reports nejsou součástí prostředí integrated shell.  
  
#### <a name="2-debugging-support"></a>2. Podpora ladění  
 Integrované prostředí obsahuje stejný ladicí stroj, který je součástí komunitní verze sady Visual Studio. Modulu pro ladění zahrnuje běžné ladicího programu pro spravovaný kód a také související funkce, jako jsou spuštění, připojit, nastavit zarážky, upravit a pokračovat a dalších. Však ladicí stroj nepodporuje ladění databáze SQL serveru.  
  
 I když se podpora pro nativní ladění je zahrnutý v balíčku základní ladicího programu, nelze ji tak, aby podporoval další rozšířit.  
  
#### <a name="3-source-code-control-integration"></a>3. Integrace správy zdrojového kódu  
 Prostředí integrated shell poskytuje rozhraní API pro implementaci správy zdrojového kódu (SCC) a pro poskytování řízení na základě MSSCCI běžné zdroje součásti pro integraci.  
  
 I když SCC integrace není regulární funkce Pro edici sady Visual Studio, SCC integrace je součástí prostředí integrated shell.  
  
#### <a name="4-build-support"></a>4. Podpora sestavení  
 Prostředí integrated shell poskytuje podporu sestavení. Může najít informace o sestavení v [MSBuild Reference](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Funkce není součástí prostředí Integrated Shell  
 Následuje seznam funkcí, které nejsou součástí prostředí integrated shell:  
  
-   Návrhář tříd  
  
-   Preemptivní řešení DotFuscator  
  
-   Jazykové funkce  
  
-   VSHost  
  
-   Žádné jazyky sady Visual Studio nebo jejich přidružený projekt šablony nebo šablony položek projektu, jsou zahrnuté v prostředí integrated shell. Žádná implementace specifické pro jazyk další funkce jsou zahrnuty pro fragmentů kódu jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření Visual Studio – přehled](http://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)