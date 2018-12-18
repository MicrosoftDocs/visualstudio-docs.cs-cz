---
title: Základy uživatelského prostředí pro Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37d2942e64a4c964ad696d1eb2c0d4bf3c777b87
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848589"
---
# <a name="ux-essentials-for-visual-studio"></a>Základy uživatelského prostředí pro Visual Studio
## <a name="best-practices"></a>Osvědčené postupy  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Být konzistentní prostředí sady Visual Studio.  
  
-   Použijte existující [vzory interakcí](interaction-patterns-for-visual-studio.md) v rámci prostředí.  
  
-   Návrh funkcí, které bylo v souladu s jazykem visual k prostředí a [řemeslné ruční práce požadavky](evaluation-tools-for-visual-studio.md).  
  
-   Používat sdílený příkazy a ovládací prvky, pokud existují.  
  
-   Zjistěte, hierarchie sady Visual Studio a jak vytváří kontextu a řídí uživatelské rozhraní.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Pomocí služby prostředí písem a barev.  
  
-   Uživatelské rozhraní by měly dodržovat aktuální [písmo prostředí](fonts-and-formatting-for-visual-studio.md) nastavení, pokud je přístupný pro vlastní nastavení na stránce písma a barev v dialogovém okně Možnosti.  
  
-   Prvky uživatelského rozhraní se musí použít [VSColor služby](colors-and-styling-for-visual-studio.md), použití sdíleného prostředí tokeny nebo konkrétních funkcí tokeny.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Ujistěte se, všechna trénováním konzistentní s nový styl VS.  
  
-   Pomocí sady Visual Studio Principy návrhu pro ikon, glyfy a jiných grafických.  
  
-   Neumísťujte text v grafické prvky.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Návrh z pohledu zaměřenou na uživatele.  
  
-   Vytvořte tok úkolů před jednotlivých funkcí v něm.  
  
-   Se seznámit s vašimi uživateli a proveďte explicitní v vaše specifikace dané znalosti.  
  
-   Při kontrole uživatelského rozhraní, vyhodnoťte plně funkční, jakož i podrobnosti.  
  
-   Návrh uživatelského rozhraní tak, aby zůstane funkční a atraktivní bez ohledu na to, národní prostředí nebo jazyk.  
  
## <a name="screen-resolution"></a>Rozlišení obrazovky  
  
### <a name="minimum-resolution"></a>Minimální rozlišení  
 - Minimální rozlišení pro Visual Studio Dev14 **1280 × 720**. To znamená, že je *možné* pro používání sady Visual Studio toto rozlišení, ale nemusí být optimální uživatelské prostředí. Není zaručeno, že všechny aspekty bude možné použít na nižší než 1280 × 720 jejich řešení.  
  
 - Cíl řešení pro Visual Studio je **1366 x 768**. Toto je nejnižší řešení, ve kterém slibujeme *dobré* činnost koncového uživatele.

 - Dialogové okno počáteční výška musí být **menší než 700 pixelů**, takže se vejde do minimální rozlišení rámce IDE při 96 dpi.
  
### <a name="high-density-displays"></a>Zobrazí s vysokou hustotou  
 Uživatelské rozhraní v sadě Visual Studio musí fungovat dobře ve všech DPI škálování faktory, které podporuje Windows úprav: 150 %, 200 % a 250 %.  
  
## <a name="anti-patterns"></a>Antimodely  
 Visual Studio obsahuje mnoho příkladů uživatelského rozhraní, které následují Naše pokyny a osvědčené postupy. Ve snaze být konzistentní vzhledem k aplikacím vývojáři často si půjčte z podobný co při sestavování vzorů návrhu uživatelského rozhraní produktu. I když je to dobrý nápad, pomůže nám jednotka konzistence v interakci s uživatelem a vizuální návrh, v některých případech dodáváme funkce s několik podrobností, které splňují Naše pokyny z důvodu omezení plánu nebo defect stanovení priorit. V těchto případech doporučujeme nechcete, aby týmy zkopírovat jeden z těchto "antimodely" vzhledem k tomu, že udrželi chybná nebo nekonzistentní uživatelské rozhraní v rámci prostředí sady Visual Studio.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Požadované pole a nastavení výchozí zobrazené v chybovém stavu  
  
#### <a name="feature-team-goals"></a>Funkce cílů týmu  
  
-   Upozornit uživatele, aby vložili element, který musí být nakonfigurované.  
  
-   Upozornit uživatele na oblasti, které vyžadují vstup.  
  
#### <a name="anti-pattern-solution"></a>Řešení ochrany proti vzor  
 Poté, co uživatel inicioval akci a předtím, než nebude dokončena úloha okamžitě umístíte kritické zastavení ikony vedle oblastí, které vyžadují konfiguraci.  
  
#### <a name="example-manifest-designer-declarations"></a>Příklad: Manifest Designer deklarace  
 Přidáte deklaraci do seznamu bezprostředně umístí v chybovém stavu, která zůstává v platnosti do uživatel nastaví požadované vlastnosti.  
  
 V tomto případě je další žádný problém vzhledem k tomu, že obsahuje Ikona použitá pro upozornění "&times;" ikonu, takže se nedá použít běžné odebrat ikonu vedle něj. V důsledku toho rozhraní používá tlačítko odebrat, více clunky ovládacího prvku.  
  
 ![Umístění uživatelského rozhraní v chybovém stavu, ve výchozím nastavení je vzor proti sady Visual Studio. ](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti – vzor")<br />Umístění uživatelského rozhraní v chybovém stavu, ve výchozím nastavení je vzor proti sady Visual Studio.
  
#### <a name="alternatives"></a>Alternativy  
 Mnohem lepší řešení tohoto problému může být:  
  
-   Umožní uživateli přidat deklarace bez upozornění a poté přesuňte okamžitě můžete nastavit vlastnosti v položce.  
  
-   Přidat ikonu upozornění (gold trojúhelník) když fokus přesunete z položky, například přidat další deklarace do seznamu nebo pokusí změnit karet v návrháři.  
  
-   Pokud uživatel se pokusí změnit karty před nastavením vlastností pro všechny deklarace, vyvolat přes pop dialogové okno s vysvětlením, že nebude možné sestavit aplikaci (nebo libovolné důsledky) až do vyřešení upozornění. Pokud uživatel zavře dialogové okno a změní karty přesto pak ikonu (kritický nebo varování, podle potřeby) se přidá na kartu deklarace.  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>Několika kliknutími k zavření uživatelského rozhraní  
  
#### <a name="feature-team-goals"></a>Funkce cílů týmu  
 Nepovolit uživatelům zavřít uživatelského rozhraní, aniž byste museli zobrazovat první text vysvětlení.  
  
#### <a name="anti-pattern"></a>Ochrana proti vzor  
 Tým vložení videa odkazů na různých místech v rámci uživatelského rozhraní VS rozhodl proti common vzor "&times;" Zavřít tlačítko a popisek vysvětlení jako určeného uživatelského prostředí a místo toho implementovat rozevírací nabídku a "Již příště nezobrazovat" propojení.  

#### <a name="example-video-links-in-team-explorer"></a>Příklad: video odkazy v Průzkumníku týmových projektů
Vynucení uživateli číst vysvětlující text před zavření uživatelského rozhraní je odolné proti vzoru v rámci sady Visual Studio. Odkazy správně navrženého, video by měl zobrazení popisu tlačítka společně s dalšími informacemi na podržte ukazatel myši a kliknutím "&times;" by měla Zavřít zprávu bez nutnosti další interakce.


 ![Vysvětlující text spojení anti&#45;vzor &#45; nesprávné](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Nesprávný odkaz na video vzor
  
#### <a name="result"></a>Výsledek  
 Místo jednoduchého tlačítko pro uzavření (jedním kliknutím) uživatel bude muset používat dvě kliknutí se jednoduše zavřít uživatelského rozhraní všude, kde je video odkazy jsou zobrazeny.  
  
#### <a name="alternatives"></a>Alternativy  
 Správný návrh v této situaci může být podle tohoto vzoru vytvořené common Internet Explorer, Office a sady Visual Studio: při najetí myší, uživatel uvidí popisek a jedním kliknutím skryje uživatelské rozhraní.  
  
 ![Vysvětlující text spojení anti&#45;vzor &#45; správné](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "opravte vzor Explanatorytextanti")<br />Vzor správné odkaz na video
  
### <a name="using-command-bars-for-settings"></a>Použití panely příkazů pro nastavení  
 **Obrázek A** představuje tento model proti: uvedení nastavení pod příkazového tlačítka, která se vztahuje k více než jen příkaz. V tomto nákresu jsou příkazy kromě spustit ladění – jako zobrazit v prohlížeči spustit bez ladění a Krokovat s vnořením –, který bude respektovat nastavení vybrané.  

  ![Obrázek A: příkaz panelu proti vzor](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti. vzor FigureA")<br />Obrázek A: příkazového řádku proti vzor
  
 O trochu lepší, ale stále nežádoucí, je nastavení tohoto typu vložení v panelech nástrojů, jak je znázorněno v **obrázek B**. Tlačítka rozdělení trvat méně místa a proto jsou vylepšení přes rozevírací seznamy, obou řešení stále používají panelu nástrojů na podporu něco, co skutečně není příkaz.  
 
 ![Obrázek B: lepší, ale stále proti vzor panel příkaz](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti. vzor FigureB")<br />Obrázek B: lepší, ale stále vzoru proti panel pro příkaz
 
  V správný přístup znázorňuje **obrázek C**, nastavení se váže na řadu příkazů. Neexistuje žádné globální nastavení nastavena a jsme právě jste přepínání mezi čtyř příkazů. Toto je pouze situace, ve kterém jsou přijatelné příkazy na panelu nástrojů. 

 ![Obrázek C: opravit pomocí sady Visual Studio příkazového řádku vzor](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti. vzor FigureC")<br />Obrázek C: správné použití sady Visual Studio příkazového řádku vzor
   
### <a name="control-anti-patterns"></a>Antimodely pro ovládací prvek  
 Některé antimodely pro jsou jednoduše nesprávné použití nebo prezentace ovládacího prvku nebo skupiny ovládacích prvků.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podtržení použitý jako název skupiny, ne hypertextový odkaz  
 Podtržení text by měla sloužit pouze pro hypertextové odkazy.  
  
 **Špatné:**    
 ![Podtržený text, který není hypertextový odkaz je vzor proti sady Visual Studio. ](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />Podtržený text, který není hypertextový odkaz je vzor proti sady Visual Studio.
  
 **Dobré:**   
 ![Styl správně,-hypertextový odkaz text se zobrazí prostým písmem prostředí. ](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />Styl správně,-hypertextový odkaz text se zobrazí prostým písmem prostředí.
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknutím na zaškrtávací políčko následek zobrazení dialogu  
 Kliknutím na políčko "Povolit vzdálenou plochu pro všechny role" v průvodci "Publikování Windows Azure aplikace" okamžitě otevře vyskakovací dialogové okno, proti vzoru sady Visual Studio. Kromě toho zaškrtávací políčko nevyplní se zaškrtávacím políčkem Po výběru, jiné interakční proti.  
  
 ![Spustit až dialogové okno po kliknutí na zaškrtávací políčko proti vzoru sady Visual Studio. ](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />Spustit až dialogové okno po kliknutí na zaškrtávací políčko proti vzoru sady Visual Studio.
  
### <a name="hyperlink-anti-patterns"></a>Antimodely pro hypertextový odkaz  
 Následující příklad obsahuje dva antimodely.  
  
1. Popředí při najetí myší zapnout red znamená, že nepoužívá správná barva sdílené ze služby písma.  
  
2. "Další informace" není odpovídající text odkazu na toto téma. Cílem uživatele je víc, přečtěte si, že je znají důsledky podle vlastní volby.  
  
   ![Ignoruje se barva služby a pomocí "Další informace" hypertextových odkazů jsou antimodely pro Visual Studio. ](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />Ignoruje se barva služby a pomocí "Další informace" hypertextových odkazů jsou antimodely pro Visual Studio.  
  
   **Lepší řešení:** pokládat otázky, uživatel by s dotazem, kliknutím na odkaz.  
  
-   Jak fungují služby Windows Azure?  
  
-   Kdy potřebuji projekt Windows Azure Mobile Services?  
  
#### <a name="using-click-here-for-links"></a>Použití "Kliknutím sem" pro odkazy  
 Hypertextové odkazy by měl být samopopisných. Je proti vzor, který se má použít, "Klikněte sem" nebo libovolný podobné změny.  
  
 **Chybný:** "Kliknutím sem pokyny o tom, jak vytvořit nový projekt."
  
 **V pořádku:** "Jak vytvořit nový projekt?"