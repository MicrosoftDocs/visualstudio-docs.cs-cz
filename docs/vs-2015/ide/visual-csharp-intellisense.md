---
title: Technologie IntelliSense jazyka Visual C# | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [J#]
- Visual C#, IntelliSense
- IntelliSense [C#]
ms.assetid: 79ca304d-dc1e-4dc9-a2a6-7808df2e588e
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d094a0272e5c90afa1a83a42543dd464f219a17
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862200"
---
# <a name="visual-c-intellisense"></a>Visual C# IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C# IntelliSense je k dispozici při psaní kódu v editoru a při ladění [přímý režim](../ide/reference/immediate-window.md) příkazové okno.  
  
## <a name="completion-lists"></a>Seznamy dokončení  
 Seznamy dokončení technologie IntelliSense v jazyce Visual C# obsahovat tokeny od seznam členů, Dokončit slovo a další. Poskytuje rychlý přístup k:  
  
- Členy typu nebo oboru názvů  
  
- Funkce názvy proměnných, příkazy a  
  
- [Fragmenty kódu](#CodeSnippets),  
  
- [Klíčová slova jazyka](#Keywords),  
  
- [Rozšiřující metody](#ExtensionMethods)  
  
  Seznamu dokončení v jazyce C# je také dostatečně inteligentní, aby odfiltrovat irelevantní tokeny a předem vyberte token na základě kontextu. Další informace najdete v tématu [filtrované seznamy dokončení v jazyce C#](../misc/filtered-completion-lists-in-csharp.md) a [Pre-selected položky seznamu dokončení v jazyce C#](../misc/pre-selected-completion-list-items-in-csharp.md).  
  
###  <a name="CodeSnippets"></a> Fragmenty kódu do seznamů dokončení  
 V jazyce Visual C#, seznam pro doplňování zahrnuje fragmenty kódu můžete snadno vložit předdefinované obsahy kódu do vaší aplikace. Fragmenty kódu se zobrazí v seznamu pro doplňování jako fragment [zástupce – Element (fragmenty kódu technologie Intellisense)](http://msdn.microsoft.com/en-us/052cc97a-5c70-42f8-b398-4c3adf670cfa).  Další informace o fragmenty kódu, které jsou k dispozici v jazyce Visual C# ve výchozím nastavení najdete v tématu [fragmenty kódu Visual C#](../ide/visual-csharp-code-snippets.md).  
  
###  <a name="Keywords"></a> Klíčová slova jazyka do seznamů dokončení  
 V jazyce Visual C#, seznam pro doplňování také obsahuje klíčová slova jazyka. Další informace o klíčových slovech jazyka C# najdete v tématu [klíčová slova jazyka C#](http://msdn.microsoft.com/library/e929b0f2-4b92-4d37-8060-23d323b098ad).  
  
###  <a name="ExtensionMethods"></a> Rozšiřující metody do seznamů dokončení  
 V jazyce Visual C#, seznam pro doplňování obsahuje rozšiřující metody, které jsou v oboru.  
  
> [!NOTE]
>  Seznam pro doplňování se nezobrazí všechny rozšiřující metody pro <xref:System.String> objekty.  
  
 Rozšiřující metody použít jinou ikonu než metody instance. Výpis seznamu ikon, naleznete v tématu [třídy View and Object Browser Icons](../ide/class-view-and-object-browser-icons.md). Jsou-li instanci metody a metody rozšíření se stejným názvem v oboru, seznam pro doplňování zobrazí ikona metody rozšíření.  
  
### <a name="filtered-completion-lists"></a>Filtrované seznamy dokončení  
 Technologie IntelliSense odstraní nepotřebné členy ze seznamu dokončení pomocí filtrů.  
  
 Visual C# filtry seznamy dokončení, které se zobrazují pro tyto položky:  
  
-   **Základní třídy a rozhraní.** Technologie IntelliSense automaticky odebere položky z rozhraní a základní třídy dokončení seznamů v deklaraci třídy base a interface seznamy a seznamy omezení. Například výčty nejsou uvedena v seznamu dokončení pro základní třídy, protože výčty nelze použít jako základní třídy. Dokončení seznamu základních tříd obsahuje pouze rozhraní a obory názvů. Pokud v seznamu vyberte položku a potom zadejte čárku, technologie IntelliSense odebere ze seznamu dokončení základní třídy, protože Visual C# nepodporuje vícenásobnou dědičnost. Stejné chování dochází k dispozici také pro klauzule omezení.  
  
-   **Atributy**: když použijte atribut na typ seznam pro doplňování se vyfiltruje tak, aby seznam obsahuje pouze ty typy, které sestup od obory názvů obsahují typy, jako třeba <xref:System.Attribute>.  
  
-   `as` a `is` operátory.  
  
-   **Klauzule catch.**  
  
-   **Inicializátory objektů:** pouze členy, které mohou být inicializovány se zobrazí v seznamu dokončení.  
  
-   **New – klíčové slovo**: při zadávání `new` a pak stiskněte MEZERNÍK, zobrazí se seznam pro doplňování. Položka je automaticky vybrán v seznamu na základě kontextu ve vašem kódu. Položky jsou automaticky vybrán v seznamu pro doplňování deklarací a návratovými příkazy v metodách.  
  
-   **jako a operátoři:** stisknutím mezerníku po zadání se automaticky zobrazí seznam filtrovaný dokončení `as` nebo `is` – klíčové slovo.  
  
-   Události: Po zadání klíčového slova `event`, seznam pro doplňování obsahuje pouze typy delegátů.  
  
-   Parametr nápovědy automaticky řadí do první přetížení metody, která odpovídá parametrům, jak je zadáte. Pokud více přetížení metody jsou k dispozici, můžete nahoru a dolů šipkami přejít na další možné přetížení v seznamu.  
  
## <a name="most-recently-used-members"></a>Naposledy použité členy  
 Technologie IntelliSense si pamatuje členy, které jste zvolili nedávno v místní nabídce [seznam členů](../ide/using-intellisense.md) pole pro název dokončení automatický objekt. Při příštím použití seznam členů, naposledy použité členy se zobrazí v horní části. Historie naposledy použité členy se vymaže mezi každou relaci v integrovaném vývojovém prostředí.  
  
## <a name="override"></a>override  
 Po zadání [přepsat](http://msdn.microsoft.com/library/dd1907a8-acf8-46d3-80b9-c2ca4febada8) a pak stiskněte MEZERNÍK, technologie IntelliSense zobrazí všechny členy platný základní třídy, které můžete přepsat v rozevíracím seznamu místní nabídky. Zadáte návratový typ metody za `override` vyzve technologie IntelliSense, aby se zobrazily pouze metody, které vracejí stejného typu. Pokud technologie IntelliSense nemůže najít žádná shoda, zobrazí se všechny členy základní třídy.  
  
## <a name="automatic-code-generation"></a>Automatické vytváření kódu  
  
### <a name="add-using"></a>Přidat direktivu using  
 Přidat pomocí operace IntelliSense umožňuje spravovat vaše zaměřit se na kód zápisu nechcete vyžadující, abyste svou pozornost zaměřili na jiné části kódu.  
  
 K zahájení přidat pomocí operace, umístěte kurzor na odkaz na typ, který nelze přeložit. Například když Vytvořte konzolovou aplikaci a pak přidejte `XmlTextReader` do těla `Main` metoda, inteligentní značky se zobrazí v části znaku zcela vpravo o `XmlTextReader`, protože se zobrazí jako odkaz na typ, který nelze přeložit.  
  
 ![Přidat direktivu Using inteligentních značek Image](../ide/media/addusesmart.gif "AddUseSmart")  
  
 Pak lze vyvolat pomocí přidat výběrem z **vyřešit** podnabídce **IntelliSense** nabídky nebo z kontextové nabídky nebo vyvoláním přidat pomocí prostřednictvím inteligentních značek. Inteligentní značky je viditelná jen když je ukazatel myši umístěného na nebo za nevázanému typu.  
  
 ![Přidat direktivu using, inteligentní značky rozšířené image](../ide/media/addusesmartexp.gif "AddUseSmartExp")  
  
### <a name="organize-usings"></a>Uspořádat direktivy using  
 **Uspořádat direktivy using** možnosti řazení a odebrat `using` a `extern` deklarace bez změny chování zdrojového kódu. V průběhu času může stát zdrojové soubory opakovaném a mohou ztížit čtení kvůli nepotřebné a neuspořádaná `using` direktivy. **Uspořádat direktivy using** možnosti compact zdrojový kód tak, že odeberete nepoužívané `using` direktivy a zlepšuje čitelnost tím, že je řazení.  
  
 Chcete-li zobrazit dostupné možnosti v sadě Visual Studio IDE, na **upravit** nabídky, přejděte **IntelliSense**a pak na **uspořádat direktivy using**. Rozhraní IDE poskytuje následující možnosti pro organizaci a odebrat `usings` direktivy:  
  
### <a name="implement-interface"></a>Implementovat rozhraní  
 Technologie IntelliSense poskytuje možnost, aby vám pomohly implementovat [rozhraní](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) při práci v editoru kódu. Za normálních okolností správně implementovat rozhraní musíte vytvořit deklaraci metody pro každého člena rozhraní ve své třídě. Díky technologii IntelliSense, jakmile zadáte název rozhraní v deklaraci třídy, zobrazí se inteligentní značky. Inteligentní značky nabízí možnost automaticky, implementovat rozhraní pomocí explicitní nebo implicitní pojmenování. V explicitní názvy provádění deklarace metody název rozhraní v části implicitní pojmenování, nevyžadují deklarace metody rozhraní, ke kterému patří. Metody rozhraní explicitně pojmenované je přístupný pouze prostřednictvím instance rozhraní a ne prostřednictvím instance třídy. Další informace najdete v tématu [explicitní implementaci rozhraní](http://msdn.microsoft.com/library/181c901f-0d4c-4f29-97fc-895079617bf2).  
  
 Implementovat rozhraní vygeneruje minimální počet zástupných procedur metoda, která je nutné k uspokojení rozhraní. Pokud základní třída implementuje částí rozhraní, pak tyto zástupné procedury se znova vygeneroval.  
  
### <a name="implement-abstract-base-class"></a>Implementace třídy base abstraktu  
 Technologie IntelliSense poskytuje možnost, aby vám pomohly implementovat členy abstraktní základní třída automaticky při práci v editoru kódu. Za normálních okolností k implementaci abstraktní členy základní třídy vyžaduje vytvoření nové definice metody pro každou metodu abstraktní základní třída v odvozené třídě. Pomocí IntelliSense po zadání názvu abstraktní základní třídy v deklaraci třídy, zobrazí se inteligentní značky. Inteligentní značky nabízí možnost automaticky provádět metody základní třídy.  
  
 Metoda zástupné procedury, které se vygenerovaly funkci implementace abstraktní základní třídy jsou modelovány pomocí fragmentu kódu, které jsou definovány v souboru MethodStub.snippet. Fragmenty kódu lze měnit. Další informace najdete v tématu [návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md).  
  
### <a name="generate-from-usage"></a>Generování před využitím  
 **Generovat z využití** funkce vám umožní použít třídy a členy před jejich definování. Můžete vygenerovat zástupnou proceduru pro všechny třídy, konstruktor, metoda, vlastnost, pole nebo výčtu, který chcete použít, ale ještě nebyly definovány. Aniž byste museli opustit váš aktuální umístění v kódu můžete vygenerovat nové typy a členy. Tím se minimalizují přerušení pracovního postupu.  
  
 Každý nedefinovaný identifikátor je zobrazen podtržení vlnovkou. Při umístění ukazatele myši na identifikátor v popisku se zobrazí chybová zpráva.  
  
 K zobrazení příslušné možnosti, můžete použít jednu z následujících postupů:  
  
- Klikněte na nedefinovaný identifikátor. Krátký podtržení se zobrazí pod znak, který nejvíce vlevo. Umístěte ukazatel myši na krátké podtržení a zobrazí se inteligentní značky (ikonu). Kliknutím na inteligentní značku.  
  
- Klikněte na nedefinovaný identifikátor a potom stiskněte klávesu CTRL +. (tečka).  
  
- Klikněte pravým tlačítkem na nedefinovaný identifikátor a potom klikněte na tlačítko **generovat**.  
  
  Možnosti, které se zobrazí následující:  
  
- **Generování provizorního kódu vlastnosti**  
  
- **Generování zástupných procedur pole**  
  
- **Generovat pahýl metody**  
  
- **Generovat třídy**  
  
- **Generovat nový typ** (pro třídy, struktury, rozhraní nebo výčet)  
  
## <a name="generate-event-handlers"></a>Generujte obslužné rutiny událostí  
 V editoru kódu technologie IntelliSense můžete připojit k pole události metod (obslužné rutiny událostí).  
  
 Po zadání `+=` operátor po polem událostí v souboru .cs, technologie IntelliSense zobrazí výzvu s možností stiskněte klávesu Tabulátor. To vloží novou instanci třídy delegáta, který odkazuje na metodu zpracování událostí.  
  
 ![Tlačítko automaticky Hook nahoru](../ide/media/vxautohookup.gif "vxAutoHookUp")  
  
 Pokud stisknete klávesu TAB, technologie IntelliSense automaticky dokončení příkazu pro vás a odkazu na obslužnou rutinu události zobrazuje jako vybraný text v editoru kódu. Dokončete propojení automatické události IntelliSense vás vyzve k stiskněte klávesu Tabulátor znovu pro vytvoření prázdné zástupné procedury pro obslužnou rutinu události.  
  
 ![Generovat obslužné rutiny události](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")  
  
> [!NOTE]
>  Pokud nový delegát, který je vytvořen pomocí technologie IntelliSense odkazuje na existující obslužné rutiny události, technologie IntelliSense komunikuje tyto informace v popisu. Poté můžete upravit tento odkaz. text je už vybraná v editoru kódu. V opačném případě propojení automatické událost dokončení v tomto okamžiku.  
  
 Pokud stisknete klávesu TAB, technologie IntelliSense tříd stub si metodu se správným podpisem a umístí kurzor do těla obslužné rutiny události.  
  
> [!NOTE]
>  Použití **přejít zpět** příkaz **zobrazení** nabídky (CTRL +-) se vrátíte do event – příkaz propojení.  
  
 Následující úlohu ukazuje, jak technologie IntelliSense automaticky zavěšení do obslužné rutiny události s názvem `button1_Click` polem událost s názvem `button1.Click`.  
  
## <a name="see-also"></a>Viz také  
 [Integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide.md)



