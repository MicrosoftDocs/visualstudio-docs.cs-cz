---
title: Vytváření diagramů vrstev z kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0a1c5af9394f36f7f89a20b711657a3ca76e8d1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727285"
---
# <a name="create-layer-diagrams-from-your-code"></a>Vytváření diagramů vrstev z kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vizualizovat váš softwarový systém logické architektury vysoké úrovně, vytvořit *diagram vrstev* v sadě Visual Studio. Pokud chcete mít jistotu, že váš kód zůstane s tímto návrhem konzistentní, ověřte kód proti diagramu vrstev. Diagramy vrstev můžete vytvářet pro projekty aplikací Visual C# .NET a Visual Basic .NET. Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Vytvoření diagramu vrstev](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Diagram vrstev umožňuje uspořádat položky řešení sady Visual Studio do logických, abstraktních skupin nazvaných *vrstvy*. Pomocí vrstev můžete popsat hlavní úlohy, které provádějí tyto artefakty, nebo hlavní komponenty systému. Každá vrstva může obsahovat další vrstvy, které popisují podrobnější úlohy. Můžete také určit zamýšlené nebo existující *závislosti* mezi vrstvami. Tyto závislosti, které jsou reprezentovány šipkami, zobrazují, které vrstvy mohou použít nebo právě používají funkce představované ostatními vrstvami. Chcete-li si udržet architektonickou kontrolu nad kódem, zobrazte zamýšlené závislosti v diagramu a potom ověřte kód proti diagramu.  
  
##  <a name="CreateDiagram"></a> Vytvoření diagramu vrstev  
 Před vytvořením diagramu vrstev zkontrolujte, zda má vaše řešení projekt modelování. Zobrazit [vytvořit modelování projektů a diagramů UML](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
> [!IMPORTANT]
>  Nepřidávejte, nepřetahujte ani nekopírujte existující diagram vrstev z jednoho projektu modelování do jiného projektu modelování nebo jiného místa v řešení. Tím budou zachovány odkazy z původního diagramu i v případě, že změníte diagram. Rovněž to způsobí, že ověřování vrstev nebude fungovat správně. Důsledkem mohou být i další problémy, jako jsou například chybějící prvky nebo jiné chyby při pokusu o otevření diagramu.  
>   
>  Místo toho přidejte do projektu modelování nový diagram vrstev. Zkopírujte prvky ze zdrojového diagramu do nového diagramu. Uložte projekt modelování i nový diagram vrstev.  
  
#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Přidání nového diagramu vrstev do projektu modelování  
  
1.  Na **architektura** nabídce zvolte **nové UML nebo diagramu vrstev**.  
  
2.  V části **šablony**, zvolte **Diagram vrstev**.  
  
3.  Pojmenujte diagram.  
  
4.  V **přidat k projektu modelování**, vyhledejte a vyberte existující projekt modelování z řešení.  
  
     -nebo-  
  
     Zvolte **vytvořte nový projekt modelování** přidat nový projekt modelování řešení.  
  
    > [!NOTE]
    >  Diagram vrstev musí existovat v projektu modelování. Můžete jej však propojit s položkami kdekoli v řešení.  
  
5.  Nezapomeňte uložit projekt modelování i diagram vrstev.  
  
##  <a name="CreateLayers"></a> Vytvořit vrstvu z artefaktů  
 Vrstvy můžete vytvářet z položek řešení sady Visual Studio, jako jsou projekty, soubory kódu, obory názvů, třídy a metody. Tím se automaticky vytvoří spojení mezi vrstvami a položkami, čímž dojde k jejich zahrnutí do procesu ověření vrstev.  
  
 Vrstvy můžete spojovat i s položkami, které ověřování nepodporují, jako například dokumenty aplikace Word nebo prezentace aplikace PowerPoint, takže vrstvu můžete přidružit ke specifikacím nebo plánům. Vrstvy můžete také spojovat se soubory v projektech, které jsou sdíleny napříč více aplikacemi, ale proces ověření nebude zahrnovat ty vrstvy, které se zobrazí s obecnými názvy, například „Vrstva 1“ a „Vrstva 2“.  
  
 Chcete-li zobrazit, pokud propojená položka podporuje ověřování, otevřete **Průzkumník vrstev** a prozkoumejte **podporuje ověřování** vlastnosti položky. Zobrazit [Správa odkazy na artefakty](#Managing).  
  
|**k**|**Postupujte podle těchto kroků**|  
|------------|----------------------------|  
|Vytvoření vrstvy pro jeden artefakt|<ol><li>Přetáhněte položku na diagram vrstev z těchto zdrojů:<br /><br /> <ul><li>**Průzkumník řešení**<br /><br />         Přetáhnout můžete například soubory nebo projekty.</li><li>Mapy kódu<br /><br />         Zobrazit [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md) a [mapy kódu použít k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Zobrazení tříd** nebo **Prohlížeč objektů**</li></ul><br />     Vrstva se zobrazí v diagramu a je propojena s artefaktem.</li><li>Přejmenujte vrstvu tak, aby odrážela odpovědnosti přidruženého kódu nebo artefaktů.</li></ol> **Důležité:** přetažením binárních souborů do vrstvy diagramu automaticky nedojde k přidání jejich odkazů do projektu modelování. Binární soubory, které chcete ověřit, je třeba ručně přidat do projektu modelování. **Přidání binárních souborů do projektu modelování** <ol><li>V **Průzkumníka řešení**, otevřete místní nabídku pro projekt modelování a klikněte na tlačítko **přidat existující položku**.</li><li>V **přidat existující položku** dialogové okno, přejděte na binární soubory, vyberte je a klikněte na tlačítko **OK**.     Binární soubory se zobrazí v projektu modelování.</li><li>V **Průzkumníka řešení**, vyberte binární soubor, který jste přidali a potom stiskněte klávesu **F4** otevřít **vlastnosti** okna.</li><li>U každého binárního souboru nastavte **akce sestavení** vlastnost **ověřit**.</li></ol>|  
|Vytvoření jedné vrstvy pro všechny vybrané artefakty|Přetáhněte všechny artefakty do diagramu vrstev současně.<br /><br /> Vrstva se zobrazí v diagramu a je propojena se všemi artefakty.|  
|Vytvoření vrstvy pro každý vybraný artefakt|Stiskněte a podržte **SHIFT** klávesu přetáhněte všechny artefakty do diagramu vrstev současně. **Poznámka:** používáte **SHIFT** klíč k výběru oblasti položek, po výběru artefaktů klávesu uvolněte. Stiskněte a podržte ji znovu, když přetahujete artefakty do diagramu. <br /><br /> Vrstva pro každý artefakt se zobrazí v diagramu a je propojena se všemi artefakty.|  
|Přidání artefaktu do vrstvy|Přetáhněte artefakt do vrstvy.|  
|Vytvoření nové nepropojené vrstvy|V **nástrojů**, rozbalte **Diagram vrstev** části a pak přetáhněte **vrstvy** do diagramu vrstev.<br /><br /> Chcete-li přidat více vrstev, dvakrát na nástroj klikněte. Až budete hotovi, zvolte **ukazatel** nástrojů nebo stisknete klávesu **ESC** klíč.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku diagramu vrstev, zvolte **přidat**a klikněte na tlačítko **vrstvy**.|  
|Vytvoření vnořených vrstev|Přetáhněte existující vrstvu na jinou vrstvu.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku vrstvy, zvolte **přidat**a klikněte na tlačítko **vrstvy**.|  
|Vytvoření nové vrstvy, která obsahuje dvě nebo více existujících vrstev|Vyberte vrstvy, otevřete místní nabídku pro váš výběr a klikněte na tlačítko **skupiny**.|  
|Změna barvy vrstvy|Nastavte jeho **barva** vlastnost na požadovanou barvu.|  
|Zadání toho, aby artefakty spojené s vrstvou nesměly patřit zadanému oboru názvů|Zadejte obory názvů do vrstvy **zakázané obory názvů** vlastnost. Použijte středník (**;**) k oddělení oborů názvů.|  
|Zadání toho, aby artefakty spojené s vrstvou nemohly záviset na zadaných oborech názvů|Zadejte obory názvů do vrstvy **je zakázané závislosti Namespace** vlastnost. Použijte středník (**;**) k oddělení oborů názvů.|  
|Zadání toho, aby artefakty spojené s vrstvou musely patřit jednomu ze zadaných oborů názvů|Zadejte obor názvů vrstvy **požadované obory názvů** vlastnost. Použijte středník (**;**) k oddělení oborů názvů.|  
  
 Číslo ve vrstvě udává počet artefaktů, které jsou spojeny s vrstvou. Při čtení tohoto čísla však pamatujte na následující skutečnosti:  
  
-   Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.  
  
     Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.  
  
-   Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.  
  
##  <a name="Managing"></a> Správa propojení mezi vrstvami a artefakty  
  
1.  V diagramu vrstev otevřete místní nabídku vrstvy a klikněte na tlačítko **zobrazit odkazy**.  
  
     **Průzkumník vrstev** zobrazuje propojení artefaktů pro vybranou vrstvu.  
  
2.  Ke správě těchto propojení použijte následující úlohy:  
  
|**k**|**V Průzkumníku vrstev**|  
|------------|---------------------------|  
|Odstranění propojení mezi vrstvou a artefaktem|Otevřete místní nabídku propojení artefaktu a následně zvolte **odstranit**.|  
|Přesunutí propojení z jedné vrstvy do druhé|Přetáhněte do diagramu propojení artefaktu s existující vrstvou.<br /><br /> - nebo -<br /><br /> 1.  Otevřete místní nabídku propojení artefaktu a následně zvolte **Vyjmout**.<br />2.  V diagramu vrstev otevřete místní nabídku vrstvy a klikněte na tlačítko **vložit**.|  
|Kopírování propojení z jedné vrstvy do druhé|1.  Otevřete místní nabídku propojení artefaktu a následně zvolte **kopírování**.<br />2.  V diagramu vrstev otevřete místní nabídku vrstvy a klikněte na tlačítko **vložit**.|  
|Vytvoření nové vrstvy z existujícího propojení artefaktu|Přetáhněte propojení artefaktu do prázdné oblasti na diagramu.|  
|Ověřte, zda propojený artefakt podporuje ověřování proti diagramu vrstev.|Podívejte se na **podporuje ověřování** sloupec pro propojení artefaktu.|  
  
##  <a name="Discovering"></a> Provádět zpětnou analýzu existujících závislostí  
 Závislost existuje všude, kde artefakt, který je spojen s jednou vrstvou, odkazuje na artefakt, který je přidružen k jiné vrstvě. Třída v jedné vrstvě například deklaruje proměnnou, která má třídu v jiné vrstvě. Je možné provádět zpětnou analýzu existujících závislostí pro artefakty, které jsou propojeny s vrstvami v diagramu.  
  
> [!NOTE]
>  Pro určité druhy artefaktů nelze provádět zpětnou analýzu žádných závislostí. Zpětnou analýzou například nebudou získány žádné závislosti z vrstvy nebo do ní, když je propojena s textovým souborem. Pokud chcete zobrazit, které artefakty mají závislosti, které je možné provádět zpětnou analýzu, otevřete místní nabídku pro jednu nebo více vrstev a klikněte na tlačítko **zobrazit odkazy**. V **Průzkumník vrstev**, zkontrolujte **podporuje ověřování** sloupce. Závislosti se nebudou provést zpětnou analýzu pro artefakty, u kterých tento sloupec zobrazuje **False**.  
  
- Vyberte jednu nebo více vrstev, otevřete místní nabídku pro vybranou vrstvu a klikněte na tlačítko **generovat závislosti**.  
  
  Obvykle se zobrazí nějaké závislosti, které by neměly existovat. Tyto závislosti lze upravit, aby odpovídaly zamýšlenému návrhu.  
  
##  <a name="EditDependencies"></a> Úprava vrstev a závislostí za účelem zobrazení zamýšleného návrhu  
 Chcete-li zobrazit popis změn, které máte v plánu provést v systému nebo v požadované architektuře, upravte diagram vrstev:  
  
|**k**|**Proveďte tyto kroky**|  
|------------|-----------------------------|  
|Změna nebo omezení směru závislosti|Nastavte jeho **směr** vlastnost.|  
|Vytvoření nových závislostí|Použití **závislost** a **obousměrná závislost** nástroje.<br /><br /> Chcete-li nakreslit více závislostí, klikněte na nástroj dvakrát. Až budete hotovi, zvolte **ukazatel** nástrojů nebo stisknete klávesu **ESC** klíč.|  
|Zadání toho, aby artefakty spojené s vrstvou nemohly záviset na zadaných oborech názvů|Zadejte obory názvů do vrstvy **je zakázané závislosti Namespace** vlastnost. Použijte středník (**;**) k oddělení oborů názvů.|  
|Zadání toho, aby artefakty spojené s vrstvou nesměly patřit zadanému oboru názvů|Zadejte obory názvů do vrstvy **zakázané obory názvů** vlastnost. Použijte středník (**;**) k oddělení oborů názvů.|  
|Zadání toho, aby artefakty spojené s vrstvou musely patřit jednomu ze zadaných oborů názvů|Zadejte obor názvů vrstvy **požadované obory názvů** vlastnost. Použijte středník (**;**) k oddělení oborů názvů.|  
  
##  <a name="EditLayout"></a> Změna způsobu zobrazení prvků v diagramu  
 Velikost, tvar, barvu a polohu vrstev nebo barvu závislostí můžete změnit úpravou jejich vlastností.  
  
##  <a name="Codemaps"></a> Zjišťování vzorců a závislostí v mapě kódu  
 Při vytváření diagramů vrstev, můžete také vytvořit **map kódu**. Tyto diagramy vám můžou pomoct odhalit vzory a závislostí při zkoumání kódu. Prozkoumejte sestavení, oborů názvů a třídy – které často odpovídají existujících vrstev pomocí Průzkumníka řešení, zobrazení tříd nebo prohlížeči objektů. Další informace o mapách kódu naleznete v tématu:  
  
-   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Viz také  
 [Video pro kanál 9: Návrh a ověření architektury pomocí diagramů vrstev](http://go.microsoft.com/fwlink/?LinkID=252073)   
 [Diagramy vrstev: referenční dokumentace](../modeling/layer-diagrams-reference.md)   
 [Diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)   
 [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)   
 [Vizualizace kódu](../modeling/visualize-code.md)